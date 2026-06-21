# Requirements for Application in a New Country

To apply the ARYA model in a new region, the following inputs are required:

## 1. Crop-type map
A crop-type map (e.g. WorldCereal) for your country of interest is required in order to isolate the target crop.

## 2. Administrative boundaries
Administrative level-1 units are required to generate aggregated yield forecasts at subnational and national levels.

## 3. Satellite data
A time-series of surface reflectance data from MODIS is required to compute the DVI evolution.

## 4. Meteorological data
Meteorological datasets (e.g. ERA5) are used to compute the accumulated Growing Degree Days (GDD).

## 5. Crop fraction thresholds
Users should define thresholds (e.g. ≥50–80%) to select pure crop pixels.

## 6. Calibration data
Local calibration data (yield statistics or field measurements) are recommended to:
- train the regression model
- adapt it to local agro-climatic conditions

These elements ensure the transferability and robustness of the ARYA approach across new regions.