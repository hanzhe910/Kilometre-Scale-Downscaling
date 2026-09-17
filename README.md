# Attention U-Net for 5-km Wind Downscaling

**Kilometre-Scale Projections and Multi-sector Wind Impact Framework for the Guangdong–Hong Kong–Macao Greater Bay Area in a Warmer Climate**

This repository provides the training and inference code for the Attention U-Net wind-downscaling model used in our study. The model maps ERA5 wind data at approximately 25-km resolution to 5-km wind-speed fields over the Guangdong–Hong Kong–Macao Greater Bay Area (GBA).

## Overview

The downscaling model is a component of a multi-sector framework for assessing the implications of future wind changes for coastal infrastructure, wind energy, tropical-cyclone-like exposure, and air pollution.

ERA5 provides the intermediate-resolution data used to develop the model. The trained model is subsequently applied to bias-corrected CMIP6 inputs prepared for the downscaling workflow.

The workflow consists of three main steps:

1. Prepare wind-speed inputs, elevation data, and the 5-km fusion reference dataset.
2. Train the Attention U-Net to learn the relationship between the input fields and the reference wind-speed fields.
3. Apply the trained model to generate 5-km wind-speed fields.


| Domain | Swin U-Net mean MSE | Attention U-Net mean MSE | MSE reduction |
| --- | ---: | ---: | ---: |
| Land | 0.02020 | 0.01775 | 12.12% |
| Ocean | 0.00577 | 0.00491 | 14.87% |
| Entire study region | 0.01298 | 0.01133 | 12.73% |

Candidate predictors included pressure-level atmospheric variables, surface meteorological variables, and elevation. Predictor selection indicated that using only **10-m wind speed and elevation** preserved model performance (Supplementary Figure S11e). These two predictors and the Attention U-Net architecture form the final model configuration.

## Evaluation

Model performance is evaluated using mean squared error (MSE), reported in m² s⁻²:

$$
\mathrm{MSE} = \frac{1}{N}\sum_{n=1}^{N}(S_n-O_n)^2
$$

Here, $S_n$ and $O_n$ are the predicted and reference wind speeds at grid cell $n$, and $N$ is the number of valid grid cells within the evaluation domain for a given test day.

Supplementary Figure S11a–c presents the domain-specific evaluation, including seasonal performance and assessments under strong-wind and typhoon conditions. The manuscript also examines performance across different elevation classes.

## Using the Code


For application to CMIP6 projections, prepare the bias-corrected climate-model inputs as described in the manuscript before running inference.
