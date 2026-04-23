# Repository Usage

The workflow to reproduce the WorldCereal crop calendars is hosted on GitHub:  
[WorldCereal/worldcereal-cropcalendars](https://github.com/WorldCereal/worldcereal-cropcalendars)

## Environment Setup
Create and activate the conda environment:
```bash
conda env create -f environment.yml
conda activate ewoc-calendars
```

## Workflow Overview
The reproduction pipeline consists of three mandatory stages:

### Stage 1: Climate Modeling (Baseline)
Train the initial XGBoost models using ERA5-Land variables to establish a global baseline.
```bash
python src/crop_calendars/scripts/wc_sos_xgboost_1st_lsp.py
# Repeat for EOS and Summer scripts...
```

### Stage 2: Remote Sensing Processing
Apply the **HANTS** algorithm to MODIS CMG NDVI time series and extract Land Surface Phenology (LSP) metrics.
```bash
python src/lsp_world.py
```

### Stage 3: Synergistic Refinement
Re-run the modeling scripts using both climate and LSP-derived predictors for the final output.

## Key Scripts
- `src/hants_3d.py`: HANTS-based smoothing utilities for 3D arrays.
- `src/lsp_world.py`: Main entry point for global phenology extraction.
- `src/crop_calendars/scripts/`: Training and prediction scripts for SOS/EOS.

::: {.callout-note}
Remember to update the `DATA_ROOT` environment variable to point to your Zenodo extraction folder before running the scripts.
:::
