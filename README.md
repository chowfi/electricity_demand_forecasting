# Electricity Demand Forecasting

This project focuses on comparing multiple forecasting models to predict electricity demand, aiming to improve:
- Backup power planning
- Energy storage management
- Grid stability

Accurate forecasts are crucial for optimizing intermittent renewable sources like wind and solar and supporting energy market decisions.

## Dataset
- **Source**: https://huggingface.co/datasets/EDS-lab/electricity-demand
- **Content**: Time series data on electricity consumption and weather
- **Scope**: Commercial and residential buildings in Europe and North America
- **Frequency**: 15-minute, 30-minute, and 1-hour intervals (Jan 2011 – Dec 2017)

## Methods
1. **Parametric Models**:
   - ARIMA/SARIMA (univariate)
   - ARIMAX/SARIMAX (multivariate with exogenous variables like weather)
2. **Non-Parametric Models**:
   - Gaussian Processes (Bayesian approach)

## Evaluation Metrics
- **Mean Absolute Percentage Error (MAPE)**
- **Root Mean Squared Error (RMSE)**

## Results

| **Model**                              | **MAPE(%)** | **RMSE(kWh)** |
|----------------------------------------|-------------|---------------|
| ARIMA(1, 0, 0)                         | 8.42        | 0.0224        |
| Auto ARIMA(2, 1, 1)                    | 16.41       | 0.0443        |
| Auto SARIMA(1, 1, 1)(2, 0, 2, 7)       | 10.31       | 0.0285        |
| SARIMA(1, 1, 1)(2, 0, 2, 7) + Fourier for yearly variation | 21.27    | 0.0572        |
| **SARIMA(1, 1, 1)(2, 0, 2, 7) + Weather** | **4.49**    | 0.0134   |
| GP (RBF & weekly periodic kernel)      | 9.27        | 0.0005        |
| **GP (RBF & weekly + annual periodic kernel)** | 5.86        | **0.0002**    |

![SARIMAX with Weather Data](./best%20models/SARIMAX%20w%20weather%20data.png)
![Forecast Plot](./best%20models/GP%20w%20RBF%20and%20weekly%20+%20yearly%20periodic%20kernels.png)



