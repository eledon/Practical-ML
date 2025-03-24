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
- [Preliminary Data Testing](#preliminary-data-testing)
- [Technologies](#technologies)
- [Key Features](#key-features)
- [Methodology](#methodology)
- [Forecast Performance](#forecast-performance)
- [Getting Started](#getting-started)
- [Next Steps](#next-steps)
- [Contact](#contact)

---

## 🧭 Overview

This project analyzes and forecasts **monthly residential gas consumption in California** using real-world data. It demonstrates the power of time series analysis by applying ARIMA, SARIMA, and ETS models, with diagnostic testing and model comparison to ensure robust and interpretable forecasts.

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
- **Data point count:** 421
- **Preprocessing:** One missing value (Jan 2024) imputed using historical January averages

---

## 🔍 Preliminary Data Testing

Before modeling, the following diagnostics were performed:

- **Stationarity:** ADF and KPSS tests confirmed the series is stationary after seasonal differencing.
- **Distribution:** Skewness = 0.73, Kurtosis = -0.77; Q-Q plot revealed deviation from normality, particularly in the lower tail.
- **Variance stabilization:** A log transformation was applied to reduce heteroscedasticity.
- **Autocorrelation:** ACF/PACF plots showed clear seasonal cycles, supporting the use of SARIMA.

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
- 📈 STL decomposition of seasonal patterns
- 🔁 Log transformation & train/test split
- 🧠 ARIMA/SARIMA via both `auto.arima()` and full grid search
- 🧪 Residual diagnostics: ACF, PACF, Shapiro-Wilk, Ljung-Box, McLeod-Li
- 📉 Forecast evaluation on test set using RMSE, MAE, MAPE

---

## 📈 Methodology

1. **Exploratory Data Analysis:**
   - Time series plots, histograms, Q-Q plots
   - ACF/PACF analysis and seasonal decomposition
2. **Transformation & Decomposition:**
   - Log transformation to stabilize variance
   - STL to extract trend, seasonality, and remainder
3. **Model Building:**
   - ARIMA and SARIMA (auto and grid search)
   - ETS model for benchmark comparison
4. **Model Diagnostics:**
   - ADF, KPSS, McLeod-Li, and Ljung-Box residual tests
   - Visual inspection of residuals
5. **Model Selection:**
   - Final model: **SARIMA(1,0,3)(0,1,1)[12]**
   - Selected based on lowest AIC/BIC, minimal residual autocorrelation, and low test-set error

---

## 📊 Forecast Performance

### 🔎 Model Comparison Summary

| Model                         | AIC      | BIC      | MAPE     | Ljung-Box p-value | McLeod-Li Result | Verdict         |
|------------------------------|----------|----------|----------|-------------------|------------------|------------------|
| SARIMA(1,0,3)(0,1,1)[12]      | **-577.99** | **-555.18** | **0.655%** | 0.30              | Mild ARCH         | ✅ Best model     |
| Auto SARIMA(2,0,1)(0,1,1)[12] | -577.48 | -554.67 | 0.656%  | 0.36              | Mild ARCH         | Good alternative |
| ETS(M,N,A)                   | 455.04   | 512.61   | 0.736%  | < 0.001           | Not tested        | ❌ Weakest model |

✅ The **SARIMA(1,0,3)(0,1,1)[12]** model provided the most accurate and well-behaved forecasts, outperforming both the auto-selected SARIMA and ETS benchmark.

---

## ⚙️ Getting Started

To reproduce this project:

```r
# Install necessary packages
install.packages(c("forecast", "tseries", "ggplot2", "urca", "DescTools",
                   "FinTS", "patchwork", "TSA", "fUnitRoots", "dplyr"))

# Run the analysis
# Source the script or open the R Markdown notebook
source("gas_consumption_Ca.R")


