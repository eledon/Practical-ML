# 🔮 Gas Consumption Forecasting with Time Series Models

Forecasting monthly residential gas consumption in California using ARIMA/SARIMA models in R.

<img src="https://raw.githubusercontent.com/eledon/Practical-ML/main/Gas%20Consumption%20Forecasting%20with%20Time%20Series%20Models/david-griffiths-Z3cBD6YZhOg-unsplash.jpg" width="500" height="300"/>

![R](https://img.shields.io/badge/R-TimeSeries-blue?logo=r)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Model](https://img.shields.io/badge/Model-ARIMA%2FSARIMA-yellowgreen)
![Data](https://img.shields.io/badge/Data-EIA%20Gov-orange)

---

## 📘 Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Technologies](#technologies)
- [Key Features](#key-features)
- [Methodology](#methodology)
- [Forecast Performance](#forecast-performance)
- [Getting Started](#getting-started)
- [Next Steps](#next-steps)
- [Contact](#contact)

---

## 🧭 Overview

This project analyzes and forecasts **monthly residential gas consumption in California** using real-world data. It demonstrates the power of time series analysis by applying ARIMA and SARIMA models, along with STL decomposition and diagnostic tests to ensure model reliability.

I created this project to:
- Apply rigorous time series forecasting techniques.
- Work with a real dataset from a trusted source.
- Showcase my data science skills in a practical and interpretable way.

---

## 📊 Dataset

- **Source:** [U.S. EIA - California Natural Gas Consumption](https://www.eia.gov/dnav/ng/hist/n3010ca2m.htm)
- **Frequency:** Monthly
- **Period:** 1989–2024
- **Unit:** Million Cubic Feet

---

## 🧪 Technologies

- **Language:** R
- **Libraries:**
  - `forecast`, `tseries`, `ggplot2`, `urca`
  - `DescTools`, `FinTS`, `patchwork`, `TSA`, `fUnitRoots`, `dplyr`
- **Models:** ARIMA, SARIMA, ETS (Exponential Smoothing)

---

## 🌟 Key Features

- ✅ Real-world dataset from a government source
- 📈 Seasonal-Trend decomposition (STL)
- 🔁 Log transformation & data splitting
- 🔍 Auto ARIMA/SARIMA + custom grid search
- 🧪 Residual diagnostics: stationarity, heteroscedasticity, normality
- 📉 Model evaluation with forecast accuracy metrics

---

## 📈 Methodology

1. **Exploratory Data Analysis**:
   - Line plots, histograms, Q-Q plots
   - ACF and PACF for pattern detection
2. **Transformation & Decomposition**:
   - Log transformation
   - STL decomposition into trend, seasonality, and remainder
3. **Modeling Approaches**:
   - ARIMA and SARIMA with both `auto.arima()` and custom grid search
   - ETS for comparison
4. **Diagnostics**:
   - ADF, KPSS, Shapiro-Wilk, McLeod-Li, Ljung-Box tests
5. **Forecasting**:
   - Comparison of models on holdout test set

---

## 📊 Forecast Performance

**SARIMA with custom hyperparameters** produced the most accurate and stable forecasts.

Models were evaluated based on:
- Forecast error (RMSE, MAE)
- Residual stationarity and normality
- Absence of autocorrelation or heteroscedasticity

---

## ⚙️ Getting Started

To reproduce this project:

```r
# Install necessary packages
install.packages(c("forecast", "tseries", "ggplot2", "urca", "DescTools",
                   "FinTS", "patchwork", "TSA", "fUnitRoots", "dplyr"))

# Run the main script
source("gas_consumption_Ca.R")

