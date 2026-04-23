# Data Access and Zenodo

All official inputs and outputs of the WorldCereal crop calendars are published on Zenodo. This dataset is open and required for reproducing the results.

**Primary Dataset (DOI):** [10.5281/zenodo.17849157](https://doi.org/10.5281/zenodo.17849157)  
**Version:** 2.1.2 (April 21, 2026)

## File Structure
The dataset total size is approximately **36.2 GB**. Below is the recommended layout after extraction:

```text
DATA_ROOT/
├── S1_SOS_WGS84.tif         # Start of Season (Winter)
├── S1_EOS_WGS84.tif         # End of Season (Winter)
├── S2_SOS_WGS84.tif         # Start of Season (Summer)
├── S2_EOS_WGS84.tif         # End of Season (Summer)
├── NDVI_hants.zip           # Smoothed MODIS time series (35.9 GB)
├── auxiliar_data.zip        # ERA5, masks, and boundaries
├── winter_crops_dataset.csv  # Modeling features for S1
├── summer_crops_dataset.csv  # Modeling features for S2
└── Global Crop Calendar Dataset Documentation.pdf
```

## GeoTIFF Specifications
- **Data type**: INT16
- **Valid range**: 1–365 (Day of Year)
- **NoData**: 0
- **CRS**: EPSG:4326 (WGS84)
- **Resolution**: 0.5° grid

## Download Instructions
1. Download from Zenodo via the DOI above.
2. Unzip the archives before running the workflow:
   ```bash
   unzip DATA_ROOT/auxiliar_data.zip -d DATA_ROOT/auxiliar_data
   unzip DATA_ROOT/NDVI_hants.zip -d DATA_ROOT/NDVI_hants
   ```
