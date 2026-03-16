# Explainable Multi-Model Time Series Forecasting System for Household Energy Consumption

## Project Overview

This project builds an **end-to-end explainable time series forecasting system** for predicting household electricity consumption.  
Multiple forecasting approaches are compared, including **statistical models, machine learning, and deep learning architectures**.

The system evaluates the performance of:

- ARIMA / SARIMA
- XGBoost
- LSTM
- Transformer

In addition to forecasting, the project includes:

- Walk-forward forecasting validation
- Multi-step forecasting (24-hour ahead)
- Residual-based anomaly detection
- Transformer attention explainability
- Trend and seasonal analysis

---

# Dataset

The project uses the **Individual Household Electric Power Consumption Dataset** from the UCI Machine Learning Repository.

Dataset characteristics:

- Time range: **2006 – 2010**
- Frequency: **1-minute measurements**
- Resampled to **hourly data**
- ~35,000 hourly observations

Target variable:  Global_active_power

---

# Data Pipeline

The complete pipeline includes:

### Data Processing

- Missing value handling
- Hourly resampling
- Train / validation / test split
  
       Train: 2006-12 → 2009-12
  
       Validation: 2010-01 → 2010-06
  
       Test: 2010-07 → 2010-11

### Feature Engineering

Lag features

    lag_1

    lag_24

    lag_168

Rolling statistics

    rolling_mean_24

    rolling_std_24

Differencing

    diff_1

    diff_24

Cyclical encoding

    hour_sin / hour_cos

    dow_sin / dow_cos

    month_sin / month_cos

Regime feature

    weekend indicator

---

# Models Implemented

## Baseline Persistence Model

Predicts the next value using the previous observation.

Used as a **reference benchmark**.

---

## ARIMA / SARIMA

Classical statistical time series models capturing:

- autoregressive patterns
- moving average effects
- seasonal components

---

## XGBoost

Gradient boosting model trained on engineered lag features.

Advantages:

- strong performance on tabular time series data
- captures nonlinear relationships
- robust with engineered features

---

## LSTM

Long Short-Term Memory neural network designed for sequential data.

Input: 24 hour sequence (LOOKBACK = 24)

Predicts: next hour (single step)

---

## Transformer

Attention-based architecture that learns relationships across past observations.

Benefits:

- captures long-range dependencies
- interpretable via attention weights

---

# Model Evaluation

Evaluation metrics:

- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)

### Final Model Comparison

| Model | MAE | RMSE |
|------|------|------|
| Baseline | 0.358 | 0.562 |
| XGBoost | **0.017** | **0.029** |
| SARIMA | 1.241 | 1.399 |
| LSTM | 0.315 | 0.455 |
| Transformer | 0.371 | 0.522 |

**XGBoost achieved the best forecasting performance.**

---

# Walk-Forward Forecasting

To simulate real-world deployment, the model was evaluated using **rolling walk-forward forecasting**.

Training window: 2 years of data

Prediction horizon: 1 week ahead

Average performance:

      MAE ≈ 0.018

      RMSE ≈ 0.029

---

This confirmed that the model maintains **stable performance over time**.

---

# Multi-Step Forecasting

A **24-hour ahead forecasting model** was implemented using LSTM.

LOOKBACK = 24
HORIZON = 24

The model predicts the entire next day of electricity consumption.

---

# Explainability

Transformer attention weights were extracted to understand **which past hours influence predictions most**.

The model learned strong importance for: 24-hour lag (daily consumption pattern)


This confirms the presence of **daily periodic behavior** in electricity usage.

---

# Anomaly Detection

Anomaly detection was performed using **forecast residuals**.

Steps:

1. Forecast consumption
2. Compute residuals

     Residual = Actual − Predicted


3. Identify outliers beyond a threshold

Detected anomalies correspond to **unusual spikes in energy consumption**.

---

# Trend and Seasonality Analysis

Trend and seasonal components were analyzed using:

- moving averages
- seasonal decomposition

Findings:

- strong **daily cycle**
- noticeable **seasonal patterns**
- stable long-term trend

---

# Repository Structure

energy-forecasting-system
│
├── notebooks
│ └── Project6_Energy_Forecasting.ipynb
│
├── src
│ ├── preprocessing.py
│ ├── feature_engineering.py
│ ├── xgboost_model.py
│ ├── lstm_model.py
│ ├── transformer_model.py
│ ├── walk_forward.py
│ ├── anomaly_detection.py
│ └── trend_analysis.py
│
├── results
│ ├── figures
│ └── metrics
│
├── requirements.txt
└── README.md


---

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


---

# Key Takeaways

- Machine learning models outperform classical time series models on this dataset
- XGBoost provided the best performance
- Transformer attention enables model interpretability
- Walk-forward validation confirms real-world forecasting reliability
- Residual analysis enables anomaly detection in electricity consumption

---

# Author

Adugna Woldemedhin

Data Engineering | Machine Learning | Time Series Forecasting | AI






