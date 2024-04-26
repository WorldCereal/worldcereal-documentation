# Design option: serverless RDM

## Introduction

This proposal outlines a potential design for the reference data module, that is based
on cloud native file formats and serverless computing.

This proposal should be seen as a summary of various ideas and technologies that have been proposed elsewhere [@ogc:cloudnative], [@holmes:duckdb],
but applied to ESA WorldCereal context and the problem of managing large datasets of parcel data. 

## Purpose & scope

This document explores an RDM design based on some relatively recent, but mature technologies.
It is not meant to immediately replace the current webservice based RDM, as there is an important risk that we will 
still discover issues in the design that are currently unknown, while the RDM webservice in any case already exists.

By providing this document, we aim to properly inform about available technologies and how they can be used. We believe
this allows to gradually evolve the current setup, or to provide a complementary alternative. 

## Design drivers

This section lists a number of key design drivers (or requirements) that have been considered in this design.
FAIR & open science principles are a major driver in ESA WorldCereal, but also long term operational costs are an issue.


### Operational costs

For a module to be maintainable over a long time after the project, it is key to have
a low operational cost.
Operational costs are incurred by various factors, but a key point is that any open
source component needs an update at some point. This is often triggered by the need
to apply security patches, or to be able to implement small enhancements.

Another cost factor is of course the number of virtual machines that are needed to run
the module.

### Retrieving (meta)data over http

FAIR principle [A1: (Meta)data are retrievable by their identifier using a standardised communication protocol](https://www.go-fair.org/fair-principles/metadata-retrievable-identifier-standardised-communication-protocol/) seems
easy to support by using http. The question is however how we can ensure that http links remain valid over time.

The 'cloud native' solution to this problem is to simply have static versions of data and metadata.

So for instance:
`https://worldcereal-rdm.geo-wiki.org/collections/static/2018beflandersfullpoly110.json`
could point to a static json file containing STAC collection metadata. It would be relatively easy to maintain such a link
in the longer term. 

### Use of standards

Fair principle [R1.3: (Meta)data meet domain-relevant community standards](https://www.go-fair.org/fair-principles/r1-3-metadata-meet-domain-relevant-community-standards/) 
states that domain relevant community standards should be used to describe (meta)data.

For the metadata, we propose the use of the STAC standard, complemented with specific extensions where relevant. The use
of STAC makes it possible to effectively find reference data that is relevant for a specific area of interest.

For the datasets, a real standard does not yet exist, but the GeoParquet format at least allows us to represent the geometry
in a standardized manner.

The use of the STAC label extension would allow us to describe the legend used by worldcereal in a machine readable way.

### Data provenance

Fair principle [R1.2: (Meta)data are associated with detailed provenance](
https://www.go-fair.org/fair-principles/r1-2-metadata-associated-detailed-provenance/) requires that a dataset or model generated
by a system like WorldCereal, can point to the source data that was used to generate it.

The RDM enables this by providing the reference data that was used to train models. So the STAC metadata of a model, can 
point to STAC metadata of reference data collections used to train the model. In STAC, this is typically done using links
with a 'derived-from' relation type.


## Proposed design

The proposal can largely be seen as a logical evolution of the current design, combined with principles from cloud native
geospatial.

The first sentence of [@ogc:cloudnative] states:
> Cloud-native geospatial offers many benefits to location data users ranging from decreasing the burden on data providers, to drastically lowering the costs of managing that data

So the relationship with our own requirement to decrease operational costs should be clear.

To make this general idea more specific, we point to a few technological advancements in the past years, that are also explained
in the next sections:

- GeoParquet as columnar, cloud-native data format. 
- DuckDB: an in-memory database that allows to integrate SQL queries on Parquet files in client side scripts or the browser.

The design is also triggered by a key observation that RDM data is not considered volatile.
When new data is added to the RDM, once made public, that version of the data should stay where it is, 
without changing. Hence we can make technology choices that are optimized for this type of data.

### Used technologies

#### GeoParquet

GeoParquet is often referred to as a 'columnar' format. This section explains what this
stands for and why it is relevant.

Columnar simply refers to the fact that data is organized by column as opposed to by row.
'Traditional' SQL databases like PostGreSQL store data by row, which for instance allows to
easily update all values in a row.

Columnar storage was introduced to address the need for fast analytics queries. For instance,
creating a histogram of all croptypes is much faster with columnar, because you only need to load
a single column for such a query.

Another important property is that GeoParquet is 'cloud-native'. This usually refers to the simple property
of being able to load parts of the data using an HTTP 'Range' request. This avoids a full download of the
file, when only a small part is needed. This ability can replace a key function that is often performed by web services:
reading only a small part of a larger database.

GeoParquet is also a binary format, with internal compression. This means that file sizes are much smaller compared
to for instance GeoJSON. Compression is of course only applied at chunk level, to retain the property of partial reads.

#### DuckDB

DuckDB is an in-memory SQL engine that can run for instance as part of a Python script, or even in a web browser.
It is built for speed, and can handle large datasets. It will utilize all available cpu's, and in our tests could
perform analytical queries on RDM data very fast. 

It support the spatial SQL extension that can also be found in PostGIS, and an H3 extension for working with H3 hexagons.
This means that many of the API requests that are normally handled by a web service backed by a SQL database, can just
as well be handled by DuckDB.

The major advantage of client-side SQL is that you don't need a server, drastically lowering resource and maintenance cost.
Another key advantage, is that users can run any SQL query they like, without needing to ask for a new API endpoint.

#### Technology experiments

Note that, to validate these technologies, we have effectively performed experiments using WorldCereal reference datasets.
These experiments mainly confirmed the statements made above. 

### High-level design

Based on these key components, the high-level design is as follows:

All data is stored as GeoParquet.
Large files are partitioned by H3 index. This allows to very quickly find the datasets that are relevant for a specific AOI.
Partitioning avoids overly large files that may still become problematic when being processed in a single call.

STAC items can be made to point to the subfiles in a collection. This allows to use either STAC or GeoParquet partitioning
to find required files.

A STAC catalog is built to allow users to find the data they need. Both a static and dynamic catalog are relevant here.
Static can be considered a 'long term' archive/backup that is always online. Dynamic web service based catalogs helps
with discoverability and easy searching.

Note that it's even an option to use GeoParquet to store collection metadata as well: this allows to find the right
collection very fast.

#### Private collections

Worldcereal has a need for user-specific collections that are not generally discoverable or accessible.

The most basic way in which this design supports such collections, is simply by letting those users manage the STAC and
GeoParquet files themselves. There is no web service involved, so there is no need for complex access control and user management.

The second option is to make use of STAC collections that are not publicly accessible. This feature is being developed
as part of the Terrascope STAC catalog.

The security scheme applied here is very important, because when a GeoParquet file is protected by a complex scheme,
tools like DuckDB may not be able to support easy reading over http. For instance, a typical OIDC flow is very complex, 
or else requires the user to get a bearer token, and then to somehow instruct DuckDB to set an HTTP header with that token
when trying to access this specific GeoParquet file over http.

The proposed solution would be to use url signing:
https://github.com/stac-extensions/authentication?tab=readme-ov-file#url-signing
This is also used by Microsoft Planetary Computer. It allows the user to generate a specific url that is valid for a limited time,
which allows direct access over http. 

#### openEO integration

To fully validate the design, proper integration options with other webservices should be explored. In the context of
WorldCereal, services based on the openEO standard are most relevant.

OpenEO already supports two predefined processes that may be relevant:
- `load_stac` to load a vector cube from stac metadata
- `load_url` to load a GeoParquet file from a url

What is missing is a process that allows to filter a vector cube both on spatial region and on properties. Note that 
the concept of filter pushdown is very important, so the process definition should give backends the freedom to perform 
this type of optimization. 

We could also consider to allow SQL style queries on vector cubes, but note that some SQL functionality does overlap with
other concepts in openEO.

### Use case explorations

These sections validate the design in terms of specific use cases.

#### Stratification

The stratification algorithm selects a subset of samples from the full RDM, to be used in model training.
It is (normally) a location specific algorithm, as it is generally important to use samples that are properly spatially distributed.

Hence a geospatial index is very important, which is why we propose to add H3 indices to the geoparquet files. By partitioning
large (or all) files on this index, we effectively get a data structure that is optimized for spatial queries, without requiring
a more complex index.

The other problem is how to store the result of the algorithm. There's a few options here:

1. add a column to all GeoParquet files, indicating if a sample is selected.
2. Create a new geoparquet, containing indices of selected samples, allowing to perform a join.
3. Create a new geoparquet, containing the selected subset with full information. (Or at least the information required for further processing.)

In terms of performance, option number 3 is certainly attractive. It will however come at a storage cost, which is to be evaluated.
It is also possible to combine option 3 with either 1 or 2, in the sense that a temporary file can be generated, and stored for the 
time that it is actively used.

#### User specific model training

For the public data, the extractions are already cached (in another GeoParquet). So openEO can load a vector cube containing
extractions for public samples, based on a spatial region.+

For user provided data, if the data is public, the caching mechanism should be triggered automatically.

For user provided data, if the data is private, the user should invoke a workflow that generates point based extractions.
The workflow will require the (signed) url of the private GeoParquet as input, and will generate a Geoparquet with extractions.

For the training itself, the user loads 2 vector cubes (public and private extractions), and performs a merge_cubes before
invoking the model training operation.







