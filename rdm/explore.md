# Data exploration and access


## Introduction

The WorldCereal Reference Data Module (RDM) offers multiple tools to explore, filter, visualize and download reference data and associated metadata, either through [a web interface](#explore-data-through-our-user-interface) or [API service](#retrieve-data-through-api).<br>

Both services can be used without authentication, initially granting users access only to publicly available reference data.

Upon login with their [Copernicus Data Space Ecosystem (CDSE)](https://dataspace.copernicus.eu/) credentials, users can additionally upload, consult, filter, retrieve and share their own private datasets as well. Read more on [data upload](./upload.md) and [publication](./publish.md).


## Data use and citation

Each published dataset in the RDM is properly documented using a standardized metadata form, including details on the data owner, applicable data license, required citation and harmonization procedure.

When using reference data obtained through RDM in your own applications, please make sure to use the appropriate citation information as captured in the metadata of the associated datasets, as well as to include proper reference to the RDM application:

*Karanam, S., Laso Bayas, J. C., Fritz, S., Boogaard, H., Pratihast, A. K., Degerickx, J., Butsko, C., Dries, J., & Van Tricht, K. (2024). WorldCereal Reference Data Module (RDM). International Institute for Applied Systems Analysis (IIASA). https://doi.org/10.60566/80p50-6z433*


## Explore data through our User Interface

The interactive RDM user interface for data exploration can be accessed [here](https://rdm.esa-worldcereal.org/map).<br>
The map (image below) provides a quick overview of distribution of reference datasets. Pins are colored based on data privacy levels:
- blue for public datasets (accessible to anyone)
- yellow for fully private datasets (accessible to owner)
- green for restricted datasets (accessible to owner and WorldCereal consortium)

The filter options in the upper right corner allow you to quickly filter reference datasets based on observation year and land cover/crop type labels.
Clicking an individual pin shows the link to the dataset, along with the total number of observations.

<p align="center">
<img src="../images/RDM_explore_map.png" alt="refdatamap" width="500"/>
<figcaption>Exploring reference data through the map view. Public datasets are represented by blue pins, fully private datasets by yellow pins and user datasets shared with WorldCereal consortium by green pins.</figcaption>
</p>

Upon clicking the link to a dataset, you end up on a dedicated page showing all metadata and direct download links to the different components of the dataset, including:
- full harmonized dataset
- subsampled harmonized dataset
- metadata excel file
- explanation of harmonization procedure
- mapping of original crop labels to WorldCereal legend

<p align="center">
<img src="../images/RDM_dataset_details.png" alt="refdatamap" width="500"/>
<figcaption>Each dataset has a dedicated page where metadata can be consulted and the data can be downloaded.</figcaption>
</p>

Alternatively, you can manually browse through the list of [public collections](https://rdm.esa-worldcereal.org/collections) or (once authenticated) [your private collections](https://rdm.esa-worldcereal.org/user-collections).



Click the following image to watch our **full video tutorial on data exploration**:

<iframe width="638" height="343" src="https://www.youtube.com/embed/mI9eq5ydW7w" title="5 2 RDM Data Exploration Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


## Retrieve data through API

The RDM provides REST APIs to access data.<br>
The WorldCereal processing module makes use of these REST APIs to request reference data prior to training crop classification algorithms.<br>


### RDM demo notebook
In [this Jupyter notebook](https://github.com/WorldCereal/worldcereal-classification/blob/main/notebooks/worldcereal_RDM_demo.ipynb) we have implemented some user-friendly functionalities in Python allowing anyone to find, query, inspect and download entire datasets, metadata and individual observations.
The notebook teaches you the practical skills needed to interact with reference data, representing the first step towards building your own crop type models.

The notebook includes instructions on how to run the notebook without the need for installing anything to your local system.


### Other resources

In case you would like to learn more about the underlying API functionalities, here are some additional resources for you to consider:

- **Jupyter notebook on how to access public datasets**

<div style="text-align: justify">
More detailed insights into how API requests are constructed to access public datasets.<br>
</div> 

<iframe src="https://nbviewer.jupyter.org/github/WorldCereal/ewoc_rdm_demo_api/blob/main/rdmApiDemo.ipynb" width="100%" height="1000px"></iframe>


- **Jupyter notebook on how to access private datasets**

<div style="text-align: justify">
To access user uploaded private datasets through APIs, credentials are required. These credentials are the same as those that were used during [upload of the datasets](./upload.md). The following Python notebook demonstrates how to get user private datasets:
</div> 

<iframe src="https://nbviewer.jupyter.org/github/WorldCereal/ewoc_rdm_demo_api/blob/main/rdmApiUserDatasetsDemo.ipynb" width="100%" height="1000px"></iframe>


- **Swagger API Documentation**

<div style="text-align: justify">
Full documentation on the different API requests can be found on our dedicated Swagger page:
</div> 

<iframe src="https://ewoc-rdm-api.iiasa.ac.at/swagger/index.html" width="100%" height="1000px"></iframe>
