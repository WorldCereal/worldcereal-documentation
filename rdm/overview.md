//////Jeroen comments //////
Definition of in-situ reference data for crop mapping  
Technical background of RDM  
list of main functionalities --> refer to more detailed sections  
////// Jeroen comments //////   

# Introduction

Availability of high-quality in-situ reference data remains one of the few bottlenecks for training and validating accurate cropland/crop type classification models. The [WorldCereal Reference Data Module (RDM)](https://ewoc-rdm-ui.iiasa.ac.at/) is an online application that hosts a global collection of harmonized and curated in-situ reference datasets on land cover and crop type, freely accessible to anyone.   

The RDM hosts datasets from various providers with standardized metadata and attributes mapped to a unified crop type legend. Built-in automated data quality checks and careful curation performed by WorldCereal data moderators ensure high and transparent data quality. Through the RDM, users can view, query, download, contribute and share in-situ reference data.  

All this functionality is available through an intuitive user interface and a more advanced API service. The Reference Data Module is linked to the WorldCereal classification system through means of a STAC catalogue, which is queried automatically during classification model training. Through this initiative the WorldCereal consortium aims to foster open data sharing within the agricultural monitoring community.


<p align="center">
<img src="../images/ref_data_overview.jpg" alt="constr" width="500"/>
<figcaption>Generic framework on in-situ reference data employed in WorldCereal.</figcaption>
</p>


# 


## Harmonization

Worldcereal follows standardised legends and procedures to prepare harmonized datasets. Below are the list of documents explaining the different procedures.

1. [Croptype legends](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_crop_legend_ui_v2_20240709.pdf)

2. [Irrigation status legends](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_irrigation_legend_ui_v2_20240709.pdf)

3. [Observation Date](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_DerivingValidityTime_v1_1.pdf)

4. [Confidence score calculations](https://ewoc-rdm-ui.iiasa.ac.at/details/WorldCereal_ConfidenceScoreCalculations_v1_1.pdf)


