////////// Jeroen comments ///////////////  
  
Introduction  

Guidelines on data collection  
(important features of the data + best practices)  

Uploading through User Interface (you need terrascope account!)  
-->	Refer to demo video!  

Using your data in the processing module  
-	Refer to previous section on retrieving private samples  
-	(Refer to next section on input data extractions)  

////////// Jeroen comments ///////////////

# Introduction

To generate accurate cropland and crop type maps, high quality reference data is indispensable for both training classification algorithms and validation of the final products. Therefore, WorldCereal would like to engage with global agricultural community to stimulate and facilitate opening and sharing of reference data  

Users can upload their datasets in their area of interest or data poor regions to generate custom products  

## Uploading through User Interface (you need terrascope account!) 
User can upload the datasets using the RDM website, We provide a intuitive and AI assisted workflow to facilitate fast upload of user datasets

### Step 1: Dataset Qualification Check

The dataset must adhere to certain formats and contain minimum attributes. User must answer the following questions to ease the dataset upload process.  
1. Does your dataset have spatial geometry?  
2. Does your dataset cover years 2017 onwards?  
3. Does your dataset have information on observation time?(date or season/year or year)

If the answer for all the above questions is "yes" then the datset is qualified to be uploaded in RDM and used in the generation of the product. These checks are mainly to prevent errors later.  

### Step 2: Dataset Upload Guidelines

Prepare the dataset according to below mentioned steps to upload successfully.  
1. Supported Dataset Format.  
  
    Supported file formats: Shapefile, GeoPackage and GeoParquet.  
    Co-ordinate system should be EPSG 4326 (WGS_84 lat/lon).  
    Language: English.  

2. Dataset Naming.  

    Select an appropriate name for your dataset. Refer to this document for guidelines.  

3. WorldCereal Crop Type Legend.  

    Crop type or land cover labels in your dataset need to be converted to the WorldCereal crop type legend to ensure compatibility with other datasets. You will be asked to select the dataset attribute containing the original labels. You will be guided to map these labels to the official WorldCereal crop type legend.    
    Dataset attribute must be String or Integer type.  

4. Validity Time.  
 
    You will be asked to select the dataset attribute that contains the observation date for each individual sample. As an alternative, you will have the possibility to define one observation date for all observations.  
    Dataset attribute must be Date type.  

5. Irrigation Status (optional).  

    You will be asked to select the dataset attribute containing information on irrigation (if present). You will be guided to map the original irrigation labels to the WorldCereal irrigation legend.
    Dataset attribute must be String or Integer type.


### Step 3: Dataset Upload

 Next step is to upload the dataset, for this we need the following basic information  

 1. Title: Full title describing the dataset.
 2. Dataset ID: Consisting of min 3 and max 40 alphanumeric lower case characters, e.g. 2024kenyacopernicus4geoglam. For datasets to be shared with other users, we encourage to use our dataset naming convention. Note that unsupported characters will be automatically removed.
 3. File: Dataset file in geoparquet (parquet) or geopackage(gpkg) or shape file (zipped)  

After the file is uploaded successfully the RDM processes the file and automatically harmonizes and adds it to community store as private dataset

## Automated harmonization and Upload

1. Attribute Extraction: In this step RDM extract all the attribute names available in the uploaded dataset except geometry. This attribute list is presented to user to choose which attribute need to be selected for crop type, irrigation(optional) and observation date mapping  

2. Attribute Mapping: In this step user is shown the AI based mapping done in RDM for Crop type and Irrigation. User can either accept the mapping or modify them if needed. 

3. Harmonization: This is last step before dataset is harmonized to worldcereal standards and assimilated into the store.  

The uploaded user dataset will be availabe to user as private dataset and will not be shared with either other users or with consortium yet. To share with consortium with suitable license users can select the "share with consortium" option available in the user dataset details page.  
