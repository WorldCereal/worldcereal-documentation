# Introduction

The WorldCereal Reference Data Module (RDM) is a outcome of collaborative approach to build a reference data store on label data which can be used for crop and irrigation related model training and validation. The products generated support worldwide crop monitoring. In the RDM we have two types of data storage:

1. Consortium data store
2. Community data store

Data sets in both data stores can be set to be publicly available or private. Data sets that are inside the consortium data storage have been collected, harmonized, and maintained by expert moderators (project partners) and have been made available to the public according their governing data licenses. Private datasets in consortium datastore will be available only for products generation.

The Data sets that are in the Community data storage are harmonized and uploaded by Community users. The uploaded data sets can be made public with appropriate licenses and will be reviewed by moderators before being published. Private user data sets will be available only for the owner of such data sets and will not be shared for use by other users or consortium for product generation until the owner decides to make the data public. The owner decides who will be allowed to use data and under what restrictions.   
User can choose from below license types.  

<table>
  <tr>
    <th>License types*</th>
    <th>Remarks</th>
  </tr>
  <tr>
    <td>CC0</td>
    <td>No Rights Reserved</td>
  </tr>
   <tr>
    <td>CC BY</td>
    <td>Attribution</td>
  </tr>
   <tr>
    <td>CC BY-SA</td>
    <td>Attribution-ShareAlike</td>
  </tr>
   <tr>
    <td>CC BY-NC</td>
    <td>Attribution-NonCommercial</td>
  </tr>
   <tr>
    <td>CC BY-NC-SA</td>
    <td>Attribution-NonCommercial-ShareAlike</td>
  </tr>
   <tr>
    <td>Private</td>
    <td>Only accessible for the owner</td>
  </tr>
   <tr>
    <td>Other</td>
    <td>To be defined by the owner</td>
  </tr>
</table>

* [See Creative Commons licenses](https://creativecommons.org/share-your-work/cclicenses/)

## Explore User Interface

[![WorldCereal RDM quick tutorial](https://img.youtube.com/vi/CmiNBUeM5WI/hqdefault.jpg)](https://www.youtube.com/watch?v=CmiNBUeM5WI&t=91s)

Click to watch video in youtube

## How to Retrieve Public Datasets
RDM provides REST APIs to access data. To access public datasets no user login is required. Below python notebook demonstrates how to access public datasets along with search functionatities
<iframe src="https://nbviewer.jupyter.org/github/WorldCereal/ewoc_rdm_demo_api/blob/main/rdmApiDemo.ipynb" width="100%" height="1000px"></iframe>


## How to Retrieve User Private Datasets
To access user uploaded private datasets through APIs, credentials are required. These credential are the same as were used during upload of the datasets. Below python notebook demonstrates how to get user private datasets
<iframe src="https://nbviewer.jupyter.org/github/WorldCereal/ewoc_rdm_demo_api/blob/main/rdmApiUserDatasetsDemo.ipynb" width="100%" height="1000px"></iframe>


## Swagger API Documentation
<iframe src="https://ewoc-rdm-api.iiasa.ac.at/swagger/index.html" width="100%" height="1000px"></iframe>
