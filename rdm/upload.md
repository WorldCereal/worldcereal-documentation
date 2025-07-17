# Uploading user datasets to the RDM

## Introduction

<div style="text-align: justify">
To generate accurate cropland and crop type maps, high quality reference data is indispensable for both training classification algorithms and validation of the final products.

Users of the WorldCereal system can upload their own reference datasets to:

- **Create fully customized cropland and crop type models** tuned to their region, season and crops of interest. Adding local, high quality reference data for the specific task at hand will always result in more accurate custom products compared to using the generic, globally representative, default WorldCereal models.
- **Contribute to high quality global WorldCereal cropland and crop type maps**, particularly for your area of interest, and receive proper attribution for your valuable contributions. 

Dataset upload is accomplished through our user-friendly, highly automated web tool that takes care of data ingestion and harmonization to WorldCereal standards.<br>

In the following sections you find more information regarding [**data licensing**](#note-on-data-license-for-user-datasets), practicial instructions on the use of the [**upload tool**](#uploading-through-user-interface) and how your data can be used by the [**WorldCereal classification module**](#using-your-data-in-the-processing-module).

</div> 

## Note on data license and protection for uploaded datasets

### Default terms: All rights reserved
Upon successful upload to the WorldCereal RDM, each user dataset is by default treated as a **private dataset**. This effectively means that all rights are reserved by the data contributor and no part of the dataset may be copied, reproduced, publicly displayed, distributed, published, adapted, translated, or otherwise used in any form or by any means by any other party.<br>

To guarantee proper protection of uploaded datasets, the WorldCereal consortium has established a dedicated **authentication and data access system**:
- uploading of datasets can only be done after authentication through a valid [Copernicus Data Space Ecosystem (CDSE)](https://dataspace.copernicus.eu/) account
- once uploaded, the dataset is tied to the CDSE account of the data contributor
- all data interaction tools provided by the RDM to explore, filter and download reference data automatically take into account data ownership: non-authenticated users can only view fully public datasets, while authenticated users only see public and their own private datasets linked to their account.

### Sharing with WorldCereal consortium
Users of the WorldCereal RDM may choose to share any uploaded dataset with the WorldCereal consortium.<br>
Upon selecting this option, the contributor grants the WorldCereal consortium the permission to use the dataset for model training and validation activities performed within the context of the ESA WorldCereal project.
Consortium members may not redistribute, sublicense, publish, or make the dataset (or any derivatives thereof) available to any third party outside the consortium.

In practice, shared datasets will become accessible for WorldCereal admin users of the RDM portal, but not to users outside of the WorldCereal consortium.<br>
As soon as a user shares a dataset with the consortium, the user will no longer be able to edit, nor delete the dataset.<br>

Upon selecting this option, the contributor will be prompted to specify whether and how the contributor wants to be attributed for their effort in any official WorldCereal products and publications making use of the contributed dataset.

### Data publication options
Data contributors are invited to publish their dataset(s) and make them available to the wider agricultural monitoring community, thereby supporting our push towards open data and science. Further instructions and data license options are specified on [this dedicated page](./publish.md).


## Uploading through User Interface

<div style="text-align: justify">

*Note that in order to be able to upload your dataset, you need to sign up for a [Copernicus Data Space Ecosystem (CDSE)](https://dataspace.copernicus.eu/) account. This is completely free of charge!*<br>

A user can upload a dataset by clicking the "Contribute" button on the home page of the [RDM website](https://rdm.esa-worldcereal.org/). We provide an intuitive and AI assisted workflow to facilitate fast upload and harmonization of user datasets.

Please check out our tutorial video which guides you through this procedure step-by-step:

<iframe width="638" height="343" src="https://www.youtube.com/embed/458soD-Gsv8" title="5 4 RDM Data Upload Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


For completeness, the different steps have also been documented below.
</div> 

### Step 1: Dataset Qualification Check

<div style="text-align: justify">
The dataset must adhere to certain formats and contain minimum attributes. The user must ensure the dataset meets the following requirements before being able to continue:<br>


  1. The dataset should have spatial geometry (polygons or points).

  2. The dataset must include information on land cover/crop types.

  3. The dataset should have information on observation time.
  
  4. The dataset must cover years 2017 onwards (due to restricted availability of Sentinel imagery prior to 2017).
  

If the answer for all the above questions is "yes" then the datset is qualified to be uploaded to the RDM. These checks are mainly to prevent errors and ensure the data can be used for training/validating crop models.  
</div> 

### Step 2: Prepare Your Dataset

<div style="text-align: justify">
Follow the below guidelines to ensure a smooth uploading procedure: 

1. Supported Dataset Formats:

    - GeoPackage (.gpkg): multi-layer geopackage files will be rejected. Make sure your file only contains one layer!
    - ESRI shapefile (.shp): shapefiles typically consist of multiple files. All files related to the shapefile need to be zipped together into one .zip file.
    - GeoParquet (.geoparquet)
    - Parquet (.parquet)

    No strict requirements are imposed regarding the dataset projection system.<br>
    All uploaded datasets are automatically converted to EPSG:4326 (WGS84).

2. Land cover/crop type information: 

    Crop type or land cover labels in your dataset will be automatically converted to the [WorldCereal crop type legend](./refdata.md#hierarchical-land-covercrop-type-legend) to ensure compatibility with other datasets. Make sure you know which attribute (column) of your dataset contains this information, you will be asked to select this attribute during the upload procedure.<br>
    
    Supported data types for this attribute: String (preferred) or Integer.

    !! In case land cover/crop type information is spread across multiple attributes, you will need to merge these attributes together before proceeding with the upload.  
      
3. Validity Time (observation time):  
 
    There are two options to specify the observation time for the sampels in your dataset:
    
    - Specific observation time for each sample: In this case, make sure you know which dataset attribute (column) contains this information.<br>
    
        Supported data types for this attribute: Date or String.You will be asked to select the dataset attribute that contains the observation date for each individual sample. 
    
    - Specify one observation time for all samples contained in the dataset. We provide [specific guidelines](https://rdm.esa-worldcereal.org/details/WorldCereal_DerivingValidityTime_v1_1.pdf) to help you assigning a reasonable observation time.

    NOTE: The WorldCereal RDM does not support multi-year datasets.<br>
    In case your dataset contains samples gathered across multiple years, you will receive a message during upload asking which part of the dataset needs to be processed.<br>
    Alternatively, you can split your dataset according to calendar year before proceeding with the upload.<br>

4. Irrigation Status (optional):  

    You will be asked to select the dataset attribute containing information on irrigation (if present). You will be guided to map the original irrigation labels to the [WorldCereal irrigation legend](./refdata.md#irrigation-status-legend).

    Supported data types for this attribute: String (preferred) or Integer.
</div> 

### Step 3: Dataset Upload & Harmonization

<div style="text-align: justify">

 Next step is to upload the dataset through the user interface (accessed through the "Contribute" button, [here](https://rdm.esa-worldcereal.org/)).


1. Drag and drop the dataset file.

2. Dataset Naming:  

    Your dataset will automatically receive a standardized name according to our [dataset naming convention](./refdata.md#dataset-naming-convention).<br>
    You will be asked to specify an "identifier", which should refer to the origin of the dataset (e.g. organization, project). This will be automatically supplemented with year, region, type and information content of the dataset. 

3. Select key dataset attributes:

    You will be presented with a list of dataset attributes. Select those attributes referring to land cover/crop type information, validity time (if present) and irrigation status (if present).

    Alternatively, specify one validity time for the entire dataset.

4. Review and submit the harmonization:

    In case your dataset contains observations across multiple years, select the year that needs to be processed.

    You will be presented with the result of the AI-based automated mapping of crop type and irrigation types to the respective WorldCereal legends.<br>
    Review the mapping (pay specific attention to fields mapped to "unknown") and submit.

After the file is uploaded successfully the RDM processes the file and adds your dataset to the community store as a fully private dataset (only accessible by you).<br>

</div> 

### Step 4: Share Your Dataset With WorldCereal Consortium

<div style="text-align: justify">
After successful upload, you will be encouraged to share your data with the WorldCereal consortium.<br>

By accepting this, your dataset privacy level will be changed to "restricted", meaning that aside from you, only WorldCereal consortium members can access the data and use it for model training and validation activities. The data will not be accessible to anyone else. This also entails that the user is no longer permitted to edit, nor delete the specific dataset.

You will be prompted whether and how you want to be officially attributed for the contribution of this specific dataset.<br>
If clear attribution details are provided, you will be properly attributed in all WorldCereal publications and products for which your dataset has been used.

As soon as you decide to share your dataset in this way, a WorldCereal moderator will be notified and conduct a quick quality check. <br>
No additional information needs to be provided by the uploader at this point.

</div> 

### Step 5: Publish your data

<div style="text-align: justify">

Datasets can be published and shared with the broader community after upload. More information and instructions are available on [this dedicated publication page](./publish.md).

</div> 

## Using your data in the processing module  

<div style="text-align: justify">
As soon as your private dataset has been uploaded successfully, you can either use the [RDM web interface](./explore.md#explore-data-through-our-user-interface), or the [RDM REST API services](./explore.md#retrieve-data-through-api) to interact with your data.<br>

Users will be able to use the uploaded datasets to train cropland/crop type models in the WorldCereal processing module.<br>
A first step in this procedure would be to extract Earth Observation time series data matching the observations in your private datasets. This procedure is explained in this [interactive notebook](https://github.com/WorldCereal/worldcereal-classification/blob/main/notebooks/worldcereal_private_extractions.ipynb).<br>
Based on the extracted data, along with publicly available reference data, users can then continue to train and apply customized crop models. A complete walk-through can be found [here](https://github.com/WorldCereal/worldcereal-classification/blob/main/notebooks/worldcereal_custom_croptype.ipynb).

</div> 
