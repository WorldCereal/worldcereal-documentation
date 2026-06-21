# WorldCereal integration in ARYA

In the original ARYA implementation (Franch et al., 2021), crop-type maps at 1 km resolution were used to isolate wheat signals.

Within the WorldCereal framework, ARYA benefits from higher-resolution crop-type maps to improve pixel purity isolation and spatial accuracy.

The process is as follows:
- WorldCereal crop-type maps are aggregated to the MODIS grid
- The fraction of wheat per MODIS pixel is calculated
- Only pixels above a threshold (e.g. 50–80%) are retained

This approach:
- Reduces mixed pixels 
- Improves DVI signal quality
- Enhances yield prediction accuracy

The integration of WorldCereal products therefore strengthens the robustness of ARYA, particularly in fragmented and heterogeneous agricultural landscapes.

## Case Studies and Demonstration

Within the WorldCereal framework, two case studies were developed to demonstrate the applicability of the ARYA yield modelling approach:

- **Ukraine (winter wheat)**
- **Brazil (maize)**

These case studies serve two main purposes:
- Validate the integration of WorldCereal crop-type maps within ARYA
- Test the transferability of the methodology to a new crop (maize) and a different agro-climatic region (Brazil)

### Ukraine Case Study (Kherson oblast)

For Ukraine, the workflow was applied to winter wheat at the oblast level, with a demonstartion in Kherson, a historically significant agricultural region, in 2021. WorldCereal crop-type maps were resampled to the MODIS grid to compute the fraction of winter wheat within each pixel (0–100%).

![WorldCereal winter wheat fraction resampled to MODIS grid](../images/wheat_fraction_kherson.png)

The filtered signal was then used to derive the DVI time-series at oblast level, expressed as a function of accumulated GDD. A Gaussian function was fitted to model and forecast crop development dynamics.

![DVI evolution as a function of accumulated GDD in Kherson, 2021](../images/DVI_evolution_kherson.png)

The Gaussian fitting of the DVI signal provided:

| Parameter | Value |
|----------|------|
| A        | 0.27 |
| B (GDD)  | 881.8 |
| C        | 362.8 |
| D        | 0.11 |
| R²       | 0.82 |
| RMSE     | 0.04 |

With a final estimated yield of 6.9 t/ha at the oblast level.

### Brazil Case Study (to be completed) 

[This section will describe the application of ARYA to maize in Brazil, including workflow adaptation and key results.]

## Final Results (to be completed)

[This section will include quantitative results such as model performance, yield estimation accuracy, and comparison with official statistics fro both Ukraine and Brazil.]
