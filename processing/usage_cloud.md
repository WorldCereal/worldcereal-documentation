# Cloud-based processing

## Powered by OpenEO and the Copernicus Data Space Ecosystem

<div style="text-align: justify">

WorldCereal selects [openEO](https://openeo.org/) as processing standard, because it allows to express both the training and inference workflows in a high-level manner.
The use of openEO aids in generating results that follow FAIR data and open science principles. This is crucial to provide transparency and reproducibility of WorldCereal results. It will also make it very feasible for anyone to inspect workflows in a visual manner.

The scalable processing needed to generate a regional to global maps is offered by the CDSE openEO federation. This includes the software to manage cloud resources, the software to parallelize workflows, disaster recovery across two datacenters, and the operational burden of monitoring the system.<br>

The CDSE open-source deployment is described in more detail in the [CDSE openEO documentation](https://documentation.dataspace.copernicus.eu/APIs/openEO/openeo_deployment.html). The most important element is that CDSE components are required to maintain an uptime of 99.5% on a monthly basis. Lower uptimes are possible, but result in penalties for the platform operators. The contract also has a long lifetime, ensuring that WorldCereal workflows can be executed beyond the project lifetime.<br>

Finally, it is important to note that CDSE is the only EU platform that offers access to the full archives of Sentinel-2 L2A and Sentinel-1 GRD data.

</div>

## How to access the cloud-based processing module?

<div style="text-align: justify">
Currently the Processing Module can be accessed through a series of Jupyter Notebooks, hosted on our public GitHub Repository. 

A user has the choice to run these notebooks:<br>
- on VITO's Terrascope platform, where everything you need is pre-installed for you<br>
- locally on your own system, after installing the worldcereal-classificaiton repository and associated Python environment<br>

Detailed instructions on how to get started can be found in each individual notebook.
</div>


**Links to notebooks:**
- Generate a cropland mask for your area and year of interest using the pre-trained WorldCereal model --> https://github.com/WorldCereal/worldcereal-classification/blob/main/notebooks/worldcereal_default_cropland.ipynb
- Prepare your private reference data for model training --> https://github.com/WorldCereal/worldcereal-classification/blob/main/notebooks/worldcereal_private_extractions.ipynb
- Train and apply a custom crop type model based on public + private reference data --> https://github.com/WorldCereal/worldcereal-classification/blob/main/notebooks/worldcereal_custom_croptype.ipynb