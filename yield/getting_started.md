# Getting started with the ARYA yield forecast DEMO

The ARYA-based yield forecasting DEMO within the WorldCereal framework provides two use cases to forecast crop yield at national and subnational level in Ukraine (winter wheat) and Brazil (maize). 

The DEMO are written as Jupyter notebook and are found in GitHub:
[WorldCereal/worldcereal-yield] (https://github.com/WorldCereal/worldcereal-yield)

Workflow:

1. Define a region of interest (e.g. administrative unit or country)
2. Retrieve MODIS reflectance data
3. Compute the Difference Vegetation Index (DVI)
4. Use WorldCereal crop-type maps to isolate crop-specific pixels
5. Express the DVI time series as a function of GDD
6. Fit a Gaussian model to the DVI evolution
7. Use model parameters in a regression model to estimate and forecast yield

More detailed information on how to set up the environment, user requirements and working with the notebook are provided in the links above.  

