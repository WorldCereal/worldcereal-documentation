# Background context

The Agriculture Remotely-sensed Yield Algorithm (ARYA) is an EO-based modelling framework designed to forecast wheat yield using satellite observations and meteorological data.

The algorithm relies on the temporal evolution of the Difference Vegetation Index (DVI), derived from MODIS observations at 1 km spatial resolution, and its relationship with the accumulated Growing Degree Days (GDD) extracted from reanalysis data.

For each administrative unit:
- Crop-type maps are used to filter the DVI time-series and isolate wheat pixels
- Only “pure” wheat pixels are retained by setting a fraction threshold
- The DVI time-series, expressed as a function of GDD, is then fitted using a Gaussian function:

DVI(GDD) = A * exp(-(GDD - B)^2 / (2C^2)) + D

Where:
- **A**: amplitude (peak of the DVI curve)
- **B**: GDD at time of the peak
- **C**: width of the curve
- **D**: background (bare soil) DVI signal

The yield is then estimated using a regression model based on the estimated Gaussian parameters:

Yield = a * A + b * C

Where:
- **A, C**: Gaussian parameters from fitted DVI model
- **a, b**: regression coefficients by administrative unit and time in Day Of the Year (DOY)

ARYA has been successfully implemented in major wheat-producing and exporting countries such as the United States, Russia, Ukraine, France, Germany, Australia and Argentina @franch2021arya, achieving:
- 5–15% error at national level
- 7–20% error at subnational level
- forecasts 2–2.5 months before harvest