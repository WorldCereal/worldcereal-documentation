# The WorldCereal Processing Module

## Generic overview

<div style="text-align: justify">
The WorldCereal Processing Module has been designed to generate custom cropland and crop type maps, anywhere on the globe. Users can either use our default models or train a custom classification model, finetuned for their region, time and crops of interest.

The figure below provides a full conceptual overview of the Processing Module:
</div>

<p align="center">
<img src="../images/pm_overview.png" alt="pm-overview" width="500"/>
<figcaption>Generic workflow employed by the WorldCereal Processing Module.</figcaption>
</p>

<div style="text-align: justify">

In short, the Processing Module deals with the following steps:<br>
- Fetching Earth Observation (EO) and ancillary input data needed for training/inference<br>
- Pre-processing the fetched time series and ensuring all inputs are resampled to 10 m resolution<br>
- Using the Presto deep learning framework to compute classification features, based on the extracted inputs<br>
- Training a custom CatBoost classification model<br>
- Applying a trained (or default) model on an area and season of interest<br>
- Spatially cleaning the model predictions and associated class probabilities<br>

</div>


*NOTE: more details on the individual components of the processing module will be added here...*