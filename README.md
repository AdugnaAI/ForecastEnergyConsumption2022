# Project 126: Explainable Multi-Model Time Series Forecasting System for Household Energy Consumption

## Overview
This project builds an end-to-end time series forecasting system for household electricity consumption using ARIMA/SARIMA, XGBoost, LSTM, and Transformer models. It also includes walk-forward validation, multi-step forecasting, anomaly detection, attention visualization, and trend analysis.

## Objectives
- Forecast household energy consumption
- Compare ARIMA, XGBoost, LSTM, and Transformer
- Evaluate with walk-forward forecasting
- Detect anomalies using forecast residuals
- Perform trend and seasonal analysis
- Provide explainability through Transformer attention

## Dataset
UCI Individual Household Electric Power Consumption dataset

## Project Structure
- `notebooks/` exploratory and end-to-end notebook
- `src/` reusable Python modules
- `results/` charts, tables, metrics
- `docs/` final report

## Methods
- Data cleaning and hourly resampling
- Feature engineering:
  - lag_1, lag_24, lag_168
  - rolling_mean_24, rolling_std_24
  - diff_1, diff_24
  - cyclical encoding
  - weekend regime
- Models:
  - ARIMA / SARIMA
  - XGBoost
  - LSTM
  - Transformer

## Evaluation
- MAE
- RMSE
- Walk-forward forecasting
- Multi-step 24-hour ahead forecasting

## Results
| Model | MAE | RMSE |
|------|------|------|
| Baseline | ... | ... |
| XGBoost | ... | ... |
| SARIMA | ... | ... |
| LSTM | ... | ... |
| Transformer | ... | ... |

## Key Findings
- XGBoost achieved the best performance on this dataset
- SARIMA struggled despite seasonal structure
- LSTM and Transformer captured temporal patterns but underperformed compared to XGBoost
- Walk-forward validation confirmed XGBoost stability over time
- Residual-based anomaly detection identified unusual consumption spikes

## Visualizations
Include:
- XGBoost learning curve
- Actual vs predicted plots
- Walk-forward forecast error over time
- Transformer attention importance
- Residual-based anomaly detection
- Trend analysis and STL decomposition

## How to Run
```bash
pip install -r requirements.txt
jupyter notebook notebooks/Project6_Energy_Forecasting.ipynb
