# In-situ reference data

## Definition & usage

<div style="text-align: justify">

We define reference data as all data which can either be used for calibrating the WorldCereal classification algorithms or validating the resulting WorldCereal products. As such, reference data should contain **location- and time-specific information about land cover and/or crop type**.<br><br>

Reference data can include:<br>
- in-situ field data gathered through dedicated field surveys<br>
- farmers declarations through parcel registration systems<br>
- data derived from visual or automated interpretation of very high resolution satellite imagery or in-situ photographs (e.g. streetview or mapillary)<br>
- existing high-quality classified maps based on analysis of satellite imagery<br>

</div>

## Harmonization

<div style="text-align: justify">

Reference data is typically available in different formats depending on the source of the dataset. To ensure multiple reference datasets can be readily combined and can serve as input for a dedicated calibration/validation task, all datasets entering the Reference Data Module should adhere to the same (meta)data standards and formats.<br><br>

In practice, this means:<br>
- Each dataset should be named according to a [**standardized naming convention**](#dataset-naming-convention), so the origin and contents of the dataset are immediately clear to the user.<br><br>
- Each dataset should be documented according to a **standardized metadata structure**, again to enable easy retrieval of information related to origin, history, content and access right of the data. To ensure maximum interoperability with other geospatial data portals and specifically allow easy data discovery, the STAC metadata format has been adopted to document each individual dataset. Click [**HERE**](https://ewoc-rdm-ui.iiasa.ac.at/collections/2018asremelgadopoly111) to see an example of the type of metadata that is collected for each harmonized and publicly available dataset. <br><br>
- The land cover/crop type labels in each dataset should be defined according to the same [**generic and hierarchical land cover / crop type legend**](#hierarchical-land-covercrop-type-legend).<br><br>
- Each dataset should contain the same list of [**standardized data attributes**](#dataset-attributes) and each attribute should adhere to predefined formatting standards.<br><br>

</div>

To illustrate this harmonization procedure, the next two figures show a screenshot of a dataset (publicly available in the RDM):


**(a) Before harmonization**

<p align="center">
<img src="../images/ref_data_harmonization_1.png" alt="system" width="600"/>
</p>


**(b) After harmonization**

<p align="center">
<img src="../images/ref_data_harmonization_2.png" alt="system" width="600"/>
</p>


### Dataset naming convention

<div style="text-align: justify">
A reference dataset name is typically compiled of 5 elements:<br>

- **Year**: Primary year of the dataset (Example: 2020)<br><br>

- **Region**: Spatial extent covered by the dataset.<br>

In case of only one country: use [ISO 3166-1 alpha-3](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3) country codes.<br>
In case of larger regions: GO (Globe), AF (Africa), NA (North America), OC (Oceania), AN (Antarctica), AS (Asia), EU (Europe), SA (South America)<br>
(Example: NPL)<br><br>

- **Identifier**: Unique identifier for the dataset containing pointers to source and content. Should be a sequence of words connected by hyphens. (Example: VITO-Potato-survey)<br><br>

- **Data type**: Short string indicating the type of data. Can be either:<br>
POINT --> shapefile containing points<br>
POLY --> shapefile containing polygons<br>
MAP --> classified map (raster data)<br><br>

- **Information content**: 3-digit code indicating which type of information is included.<br>
First digit represents land cover, second represents crop type and third represents irrigation.<br>
0 means absent, 1 means present.<br>
Examples: <br>
'100' means only information on land cover available;<br>
'110' means both land cover and crop type information;<br>
'101' means both land cover and irrigation information<br><br>

</div>

### Hierarchical land cover/crop type legend
<div style="text-align: justify">
The central idea is to have a common, hierarchical legend for land cover/crop type.<br>

The WorldCereal system can support the mapping of any crop type of interest, which requires our legend to be both extensive and dynamic (i.e. allowing the addition of new crop types, as new data come in). The legend has also been built hierarchically, using multiple levels (land cover, crop group, crop type, etc.), as our crop type classification models will also be trained in a hierarchical way.<br>

Our legend has been based mainly on crop characteristics as can be observed by remote sensing and is inspired by the Hierarchical Crop and Agriculture Taxonomy [HCAT](https://www.researchsquare.com/article/rs-3725140/v1) legend as also adopted in the [EuroCrops initiative](https://zenodo.org/records/6868143) (an initiative aimed at harmonizing European parcel registration datasets).<br>

In conclusion, the proposed detailed, dynamic and hierarchical legend allows ample flexibility to the user of the system in terms of customized model training and application.

The current legend can be consulted through [**this link**](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_crop_legend_ui_v2_20240709.pdf).

</div>

### Irrigation status legend

<div style="text-align: justify">

Even though irrigation mapping will not be officially supported by the  WorldCereal system, many of the datasets currently present in the WorldCereal Refernece Data Module hold information on irrigation practices. As we would like to conserve this information as much as possible, taking into account potential future extensions of the system, we decided to keep the irrigation label as an optional data attribute. The same irrigation legend is adopted as was introduced during WorldCereal Phase I and can be consulted through [**this link**](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_irrigation_legend_ui_v2_20240709.pdf). 

</div>

### Dataset attributes
<div style="text-align: justify">
Each harmonized vector file contains the following data attributes:<br>

- **ewoc_code** (int64): Land cover and crop type label according to the [hierarchical WorldCereal legend](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_crop_legend_ui_v2_20240709.pdf). This label is composed of 5 numeric parts, put together in one number.<br>
Example: 1111020036<br><br>

- **irrigation_status** (int32): 3-digit code indicating presence and type of irrigation. See the [irrigation legend](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_irrigation_legend_ui_v2_20240709.pdf).<br>
Example: 213<br><br>

- **valid_time** (date, format YYYY-MM-DD): A specific date for which the observation is valid. In case an exact observation date is not known, it should be derived from information regarding the year and season in which the data was collected. See [this document]((https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_DerivingValidityTime_v1_1.pdf)) for guidelines.<br>
Example: Datetime(2020-10-01)<br><br>

- **sample_id** (string): Unique ID for each individual sample. In order to guarantee ID uniqueness, this ID is typically composed by the name of the dataset, followed by an underscore and a sample ID. In case the original dataset contains unique sample IDs, these can be adopted for this last part during the harmonization procedure.<br>
Example: 2019_BEL_vito-potato_POINT_101_AABD23<br><br>

- **index** (int64): Unique sample ID<br>
Example: 1<br><br>

- **quality_score_lc** (int32): A quality score ranging from 0 to 100 indicating the inherent quality of the sample with respect to its landcover label. Usually the values are between 50 (low) and 100 (high). See also [Confidence score calculations](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_ConfidenceScoreCalculations_v1_1.pdf)<br>
Example: 80<br><br>

- **quality_score_ct** (int32): A quality score ranging from 0 to 100 indicating the inherent quality of the sample with respect to its crop type label. Usually the values are between 50 (low) and 100 (high). See also [Confidence score calculations](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_ConfidenceScoreCalculations_v1_1.pdf)<br>
Example: 80<br><br>

- **extract** (int32): In case of very large datasets, it is simply not feasible to use ALL samples for model training/validation, as for each sample the associated input data need to be fetched, which can become quite costly. Therefore, this attribute indicates whether or not for this sample an extraction of model inputs should be done. The higher the value, the more priority this sample has for launching the extractions pipeline.<br>
Example: 1 (lowest priority)<br><br>

- **h3_l3_cell** (string): ID of the h3 cell (used for sub-sampling) at level 3 resolution.<br>
Example: <br><br>

- **sampling_ewoc_code** (int64): <br><br>

- **h3_best_res_cell** (string): <br><br>

- **distance_to_nearest_road** (double): Distance in meter to nearest road based on OSM data layers. Optional, in case spatial accuracy of FO data have been calculated.<br>
Example: 268.32 <br><br>

</div>


## Harmonization in practice

<div style="text-align: justify">

To ensure this data standardization, harmonization and documentation is done in the same way for all datasets, a **semi-automated workflow** has been set up to guide the user through this process for each dataset. Learn more about how you can add your data to the RDM and get it harmonized almost entirely automatically through our user dedicated user interface --> [**HERE**](./upload.md).

</div>