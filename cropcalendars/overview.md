# Overview: WorldCereal Crop Calendars

Accurate crop calendars are critical for understanding global agricultural phenology, mapping crop types, and improving yield forecasts. The WorldCereal crop calendars (Phase II) represent a significant advancement over previous versions by integrating **Land Surface Phenology (LSP)** with climate data.

## Key Enhancements in Phase II
- **Synergistic Modeling**: Fusion of MODIS AQUA NDVI time series (LSP) with ERA5-Land climate parameters using **XGBoost**.
- **Dormancy Modeling**: Explicit modeling of dormancy periods for winter cereals, significantly improving accuracy in high-latitude regions (Canada, Northern Europe, Central Asia).
- **Densified Training Data**: Increased reference density in underrepresented regions (South America, Africa, and Asia).
- **High Accuracy**: Achieved $R^2 > 0.90$ and $RMSE < 30$ days across major crop types.

## Seasonal Groups
The dataset is organized into two primary seasonal groups:

| Group | Description | Typical Crops |
|-------|-------------|---------------|
| **S1** | Winter crops | Winter wheat, Winter barley, Winter Rye, Rapeseed |
| **S2** | Summer crops | Maize, Sorghum, Soybean, Sunflower, Millet |

For a detailed technical description, see the [Methodology](methodology.md) section.
