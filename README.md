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
