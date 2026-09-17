# Wind Downscaling

**Kilometre-Scale Projections and Multi-sector Wind Impact Framework for the Guangdong–Hong Kong–Macao Greater Bay Area in a Warmer Climate**

This repository provides the training and inference code for the Attention U-Net wind-downscaling model used in our study. The model maps ERA5 wind data at approximately 25-km resolution to 5-km wind-speed fields over the Guangdong–Hong Kong–Macao Greater Bay Area (GBA).

| Domain | Swin U-Net mean MSE | Attention U-Net mean MSE | MSE reduction |
| --- | ---: | ---: | ---: |
| Land | 0.02020 | 0.01775 | 12.12% |
| Ocean | 0.00577 | 0.00491 | 14.87% |
| Entire study region | 0.01298 | 0.01133 | 12.73% |



## Evaluation

Model performance is evaluated using mean squared error (MSE), reported in m² s⁻²:

$$
\mathrm{MSE} = \frac{1}{N}\sum_{n=1}^{N}(S_n-O_n)^2
$$

Here, $S_n$ and $O_n$ are the predicted and reference wind speeds at grid cell $n$, and $N$ is the number of valid grid cells within the evaluation domain for a given test day.

Supplementary Figure S11a–c presents the domain-specific evaluation, including seasonal performance and assessments under strong-wind and typhoon conditions. The manuscript also examines performance across different elevation classes.

## Using the Code


For application to CMIP6 projections, prepare the bias-corrected climate-model inputs as described in the manuscript before running inference.
