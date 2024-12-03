# electricity_demand_forecasting

dataset: https://huggingface.co/datasets/EDS-lab/electricity-demand

We have chosen to conduct a multiple model comparison project on an existing electricity demand dataset, focusing on electricity demand forecasting to provide accurate predictions that support better planning for backup power generation, efficient energy storage management, and overall grid stability. This is particularly important for integrating intermittent renewable sources like wind and solar, helping optimize their use while enabling informed purchasing and selling decisions in the energy market. 

For this project, we will use an electricity demand dataset from HuggingFace, which harmonizes multiple open smart meter datasets. The dataset contains time series data on electricity consumption and weather, spanning commercial and residential buildings across various cities in Europe and North America. Data is recorded at three frequency intervals (15minutes, 30minutes, and 1 hour) from January 2011 to December 2017. 

Our approach will explore both parametric univariate methods such as ARIMA/SARIMA and multivariate methods like ARIMAX/SARIMAX, incorporating exogenous variables like weather data to improve forecasts. Additionally, we will use non-parametric Bayesian models such as Gaussian Processes.

We will evaluate our models using MAPE and RMSE metrics.
