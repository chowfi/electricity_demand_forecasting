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


<table>
  <thead>
    <tr>
      <th rowspan="2">Model</th>
      <th colspan="2">Forecast Performance (Test Data)</th>
      <th colspan="2">Model Fit (Training Data)</th>
    </tr>
    <tr>
      <th>MAPE(%)</th>
      <th>RMSE(kWh)</th>
      <th>Log-Likelihood</th>
      <th>AIC</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>ARIMA(1, 0, 0)</td>
      <td>8.420</td>
      <td>0.0224</td>
      <td>2119</td>
      <td>-4232</td>
    </tr>
    <tr>
      <td>Auto ARIMA(2, 1, 1)</td>
      <td>16.41</td>
      <td>0.0443</td>
      <td>xx</td>
      <td>-4263</td>
    </tr>
    <tr>
      <td>Auto SARIMA(1, 1, 1)(2, 0, 2, 7)</td>
      <td>10.31</td>
      <td>0.0285</td>
      <td>xx</td>
      <td>-4509</td>
    </tr>
    <tr>
      <td>SARIMA(1, 1, 1)(2, 0, 2, 7) + Fourier for yearly variation</td>
      <td>21.27</td>
      <td>0.0572</td>
      <td>2248</td>
      <td>-4479</td>
    </tr>
    <tr>
      <td><b>SARIMA(1, 1, 1)(2, 0, 2, 7) + Weather</b></td>
      <td><b>4.870</b></td>
      <td><b>0.0134</b></td>
      <td><b>2311</b></td>
      <td><b>-4605</b></td>
    </tr>
    <tr>
      <td>GP (RBF & weekly periodic kernel)</td>
      <td>9.27</td>
      <td>0.0005</td>
      <td>42.56</td>
      <td>-73.12</td>
    </tr>
    <tr>
      <td><b>GP (RBF & weekly + annual periodic kernel)</b></td>
      <td><b>5.86</b></td>
      <td><b>0.0002</b></td>
      <td><b>66.84</b></td>
      <td><b>-115.68</b></td>
    </tr>
  </tbody>
</table>





![SARIMAX with Weather Data](./best%20models/SARIMAX%20w%20weather%20data.png)
![Forecast Plot](./best%20models/GP%20w%20RBF%20and%20weekly%20+%20yearly%20periodic%20kernels.png)



