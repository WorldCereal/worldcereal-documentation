# Uploading user datasets to the RDM

## Introduction

<div style="text-align: justify">
To generate accurate cropland and crop type maps, high quality reference data is indispensable for both training classification algorithms and validation of the final products. Therefore, WorldCereal would like to engage with global agricultural community to stimulate and facilitate opening and sharing of reference data.  

Users can upload their datasets in their area of interest or in data poor regions to contribute to high quality global WorldCereal products, or generate their own custom, high quality maps.  
</div> 

## Uploading through User Interface

<div style="text-align: justify">

*Note that in order to be able to upload your dataset, you need to sign up for a [Terrascope](https://terrascope.be/en) account. This is completely free of charge!*<br>

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

By accepting this, your dataset privacy level will be changed to "restricted", meaning that aside from you, only WorldCereal consortium members can access the data and use it to finetune the global WorldCereal crop models. The data will not be visible to anyone else.

As soon as you decide to share your dataset in this way, a WorldCereal moderator will be notified and conduct a quick quality check. <br>
No additional information needs to be provided by the uploader at this point.

</div> 


## Using your data in the processing module  

<div style="text-align: justify">
As soon as your private dataset has been uploaded successfully, you can either use the RDM web interface, or the RDM REST API services to interact with your data.<br>
More information and dedicated guidelines can be found [here](./explore.md#explore-data-through-our-user-interface).

Users will be able to use the uploaded datasets to train cropland/crop type models in the processing module.<br>
More details on this will be added once this functionality is fully operational.

</div> 

## Sharing your data with the community

If you would like to share your dataset with the general public and contribute to the move towards open data and science, please consult the associated guidelines on [this dedicated page](./publish.md).
