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


<table>
  <thead>
    <tr>
      <th rowspan="2">Model</th>
      <th colspan="2">Forecast Performance (Test Data)</th>
      <th colspan="2">Model Fit (Training Data)</th>
    </tr>
    <tr>
      <th>MAPE(%) &darr; </th>
      <th>RMSE(kWh) &darr; </th>
      <th>Log-Likelihood &uarr; </th>
      <th>AIC &darr; </th>
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
      <td>2136</td>
      <td>-4263</td>
    </tr>
    <tr>
      <td>Auto SARIMA(1, 1, 1)(2, 0, 2, 7)</td>
      <td>10.31</td>
      <td>0.0285</td>
      <td>2227</td>
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
      <td>4.870</td>
      <td>0.0134</td>
      <td><b>2311<b></td>
      <td><b>-4605<b></td>
    </tr>
    <tr>
      <td><b>Final Tuned SARIMA(1, 1, 2)(0, 1, 2, 7) + Weather</b></td>
      <td><b>2.900<b></td>
      <td>0.0083</td>
      <td>2304</td>
      <td>-4588</td>
    </tr>
    <tr>
      <td>GP (RBF & weekly periodic kernel)</td>
      <td>9.270</td>
      <td>0.0005</td>
      <td>43</td>
      <td>-73</td>
    </tr>
    <tr>
      <td><b>GP (RBF & weekly + annual periodic kernel)</b></td>
      <td>5.860</td>
      <td><b>0.0002</b></td>
      <td>67</td>
      <td>-116</td>
    </tr>
  </tbody>
</table>





![Fine-tuned SARIMAX with Weather Data](./best%20models/Fine-tuned%20SARIMAX%20w%20weather%20data.png)
![Forecast Plot](./best%20models/best_gp_model.png)



