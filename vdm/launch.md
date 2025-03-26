# Launching WorldCereal Processing Jobs Through User Interfaces

## Introduction
The [WorldCereal Processing Hub](https://hub.esa-worldcereal.org) provides user-friendly interfaces that enable users to launch and monitor WorldCereal processing jobs on the [Copernicus Data Space Ecosystem (CDSE)](https://dataspace.copernicus.eu/) with ease. 

We currently support two types of processes:

- Download an official WorldCereal product for your area of interest
- Generate a customized cropland product for your area and season of interest

The following sections provide a comprehensive walkthrough through the entire application.

---

## The WorldCereal Processing Hub

---

### Login
To access the tool, users must first log in using their CDSE account credentials. Once logged in, users will end up on the Home page of the application (next section).

<p align="center">
<img src="../images/processing-hub/login/login.png" alt="Login screen" width="700"/>
</p>

---

### Home
The homepage provides basic information about the application and links to useful resources. The different components of the Processing Hub can be accessed through the different tabs at the top of the screen.

<p align="center">
<img src="../images/processing-hub/home/home.png" width="700" />
</p>

---

### List of Processes
The "List of Processes" page displays all active and completed processes along with their details (status, extent, input parameters, link to products). From here, you can download the individual results (maps) of your processing jobs directly to your computer by clicking the yellow links. In case you would like to consult detailed logs on a particular jobs, you can use the processing ID mentioned in the first column to locate the job directly in the [OpenEO web editor](https://openeo.dataspace.copernicus.eu/).

<p align="center">
<img src="../images/processing-hub/your-processes/your-processes.png" alt="List of processes" width="700"/>
</p>

---

### Download Official Products

This section allows users to download [official global WorldCereal products](https://esa-worldcereal.org/en/products/global-maps) for their area of interest. Currently, official products are only available for the "2021" collection.

<p align="center">
<img src="../images/processing-hub/download-official-products/download-official-products-step-1.0.png" alt="Download official products" width="700"/>
</p>

#### Step 1: Select Collection and Product
Select the desired collection and product, then proceed to the next step.

<p align="center">
<img src="../images/processing-hub/download-official-products/download-official-products-step-1.1.png" alt="Select collection and product" width="700"/>
</p>

#### Step 2: Define Area of Interest and Output Format
Specify the area of interest (AOI) and output format, then create a new download process. Users can return to the previous step to modify their selection if needed. The download job will not start until it is confirmed in the next step.

*Note: There is a limit to the size of the area that can be selected. Current limits are displayed above the map window, and the size of the selected area is shown below the map window.*

<p align="center">
<img src="../images/processing-hub/download-official-products/download-official-products-step-2.0.png" alt="Define AOI and output format" width="700"/>
</p>

#### Step 3: Confirm and Start the Process
Review the details of the process. If everything is correct, start the process. Once created, the user will be redirected to the "Your Processes" page. Additional processes can also be created and run later from the "Your Processes" tab.

<p align="center">
<img src="../images/processing-hub/download-official-products/download-official-products-step-3.0.png" alt="Confirm and start process" width="700"/>
</p>

---

### Generate Custom Products

This section allows users to generate and download custom WorldCereal classification products.

<p align="center">
<img src="../images/processing-hub/generate-custom-product/generate-custom-products-1.0.png" alt="Generate custom products" width="700"/>
</p>

#### Step 1: Select Product Type and Model
Select the desired product type and model, then proceed to the next step.

*Note: Currently, only the "Default" model and "Cropland" product are available.*

<p align="center">
<img src="../images/processing-hub/generate-custom-product/generate-custom-products-1.1.png" alt="Select product type and model" width="700"/>
</p>

#### Step 2: Define Parameters
Specify the area of interest (AOI), end month, and output format, then create a new custom product process. Users can return to the previous step to modify their selection if needed. The custom product process will not start until it is confirmed in the next step.

*Note: There is a limit to the size of the area that can be selected. Current limits are displayed above the map window, and the size of the selected area is shown below the map window. Additionally, examples are provided to indicate the estimated processing time and credit consumption for different AOI sizes.*

<p align="center">
<img src="../images/processing-hub/generate-custom-product/generate-custom-products-1.2.png" alt="Define parameters" width="700"/>
</p>

#### Step 3: Confirm and Start the Process
Review the details of the process. If everything is correct, start the process. Once created, the user will be redirected to the "Your Processes" page. Additional processes can also be created and run later from the "Your Processes" tab.

<p align="center">
<img src="../images/processing-hub/generate-custom-product/generate-custom-products-1.3.png" alt="Confirm and start process" width="700"/>
</p>