# Uploading user datasets to the RDM

## Introduction

<div style="text-align: justify">
To generate accurate cropland and crop type maps, high quality reference data is indispensable for both training classification algorithms and validation of the final products. Therefore, WorldCereal would like to engage with global agricultural community to stimulate and facilitate opening and sharing of reference data.  

Users can upload their datasets in their area of interest or in data poor regions to contribute to high quality global WorldCereal products, or generate their own custom, high quality maps.  
</div> 

## Uploading through User Interface

<div style="text-align: justify">

*Note that in order to be able to upload your dataset, you need to sign up for a [Terrascope](https://terrascope.be/en) account. This is completely free of charge!*<br>

A user can upload a dataset using the RDM website. We provide an intuitive and AI assisted workflow to facilitate fast upload and harmonization of user datasets.

Please check out our tutorial video which guides you through this procedure step-by-step:


For completeness, the different steps have also been documented below.
</div> 

### Step 1: Dataset Qualification Check

<div style="text-align: justify">
The dataset must adhere to certain formats and contain minimum attributes. The user must ensure the dataset meets the following requirements before being able to continue:<br>
1. Dataset should have spatial geometry.  
2. Dataset must cover years 2017 onwards.  
3. Dataset should have information on observation time.

If the answer for all the above questions is "yes" then the datset is qualified to be uploaded to the RDM. These checks are mainly to prevent errors later and ensure the data can be used for training/validating crop models.  
</div> 

### Step 2: Dataset Upload Guidelines

<div style="text-align: justify">
Prepare the dataset according to below mentioned steps to upload successfully.  

1. Supported Dataset Format.  
  
    Supported file formats: Shapefile, GeoPackage and GeoParquet.  
    Co-ordinate system should be EPSG 4326 (WGS_84 lat/lon).  
    Language: English.  

2. Dataset Naming.  

    Select an appropriate name for your dataset. Refer to [this section](./refdata.md#dataset-naming-convention) for guidelines.  

3. WorldCereal Crop Type Legend.  

    Crop type or land cover labels in your dataset need to be converted to the [WorldCereal crop type legend](./refdata.md#hierarchical-land-covercrop-type-legend) to ensure compatibility with other datasets. You will be asked to select the dataset attribute containing the original labels. You will be guided to map these labels to the official WorldCereal crop type legend.    
    Dataset attribute must be String or Integer type.  

4. Validity Time.  
 
    You will be asked to select the dataset attribute that contains the observation date for each individual sample. As an alternative, you will have the possibility to define one observation date for all observations. Refer to [this document](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_DerivingValidityTime_v1_1.pdf) for specific guidelines.
    Dataset attribute must be Date type.  

5. Irrigation Status (optional).  

    You will be asked to select the dataset attribute containing information on irrigation (if present). You will be guided to map the original irrigation labels to the [WorldCereal irrigation legend](./refdata.md#irrigation-status-legend).
    Dataset attribute must be String or Integer type.
</div> 

### Step 3: Dataset Upload

<div style="text-align: justify">

 Next step is to upload the dataset, for this we need the following basic information:

 1. Title: Full title describing the dataset.
 2. Dataset ID: Consisting of min 3 and max 40 alphanumeric lower case characters, e.g. 2024kenyacopernicus4geoglam. For datasets to be shared with other users, we encourage to use our dataset naming convention. Note that unsupported characters will be automatically removed.
 3. File: Dataset file in geoparquet (parquet) or geopackage(gpkg) or shape file (zipped)  

After the file is uploaded successfully the RDM processes the file and automatically harmonizes and adds it to the community store as a fully private dataset.
</div> 

## Automated harmonization and Upload

<div style="text-align: justify">
Here we shortly describe the different steps the data goes through during automated harmonization:

1. Attribute Extraction: In this step RDM extract all the attribute names available in the uploaded dataset except geometry. This attribute list is presented to the user to choose which attribute needs to be selected for crop type, irrigation(optional) and observation date mapping.  

2. Attribute Mapping: In this step the user is shown the AI based mapping done in RDM for Crop type and Irrigation. User can either accept the suggested mappings or modify them if needed. 

3. Harmonization: This is last step before the dataset is harmonized to WorldCereal standards and assimilated into the community store.  

The uploaded user dataset will be availabe to the user as a private dataset and will not be shared with either other users or with the consortium yet. To share with the consortium with suitable license users can select the "share with consortium" option available in the user dataset details page. Refer to [this specific page](./publish.md) for more details on dataset publication. 
</div>

## Webiste User Dataset upload demo

<video controls width="100%" height="360">
  <source src="[[path/to/your/videofile.mp4](https://ewocstorage.blob.core.windows.net/data/ewoc_userdatasetUpload.mp4)](https://ewocstorage.blob.core.windows.net/data/ewoc_userdatasetUpload.mp4)" type="video/mp4">
  Your browser does not support the video element.
</video>


## Using your data in the processing module  

<div style="text-align: justify">
Users will be able to use the uploaded datasets to train cropland/crop type models in the processing module.

More details on this will be added once this functionality is fully operational.
</div> 
