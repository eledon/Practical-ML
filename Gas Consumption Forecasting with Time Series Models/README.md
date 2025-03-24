# 🔮 Gas Consumption Forecasting with Time Series Models

Forecasting monthly residential gas consumption in California using ARIMA, SARIMA, and ETS models in R.

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
- [Forecast Accuracy](#forecast-accuracy)
- [Getting Started](#getting-started)
- [Next Steps](#next-steps)
- [Contact](#contact)

---

## 🧭 Overview

This project forecasts **monthly residential gas consumption in California** using time series models. It compares the performance of ARIMA, SARIMA, and ETS models and includes thorough diagnostics and residual analysis.

---

## 📊 Dataset

- **Source:** [U.S. EIA - California Natural Gas Consumption](https://www.eia.gov/dnav/ng/hist/n3010ca2m.htm)
- **Frequency:** Monthly
- **Period:** 1989–2024
- **Unit:** Million Cubic Feet
- **Data points:** 421
- **Missing value imputation:** January 2024 value was imputed using the historical average for January

---

## 🔍 Preliminary Data Testing

Before modeling, we assessed the time series characteristics of the data:

- **Stationarity:** ADF and KPSS tests indicated the need for seasonal differencing
- **Distribution:** Skewness = 0.73, Kurtosis = -0.77; Q-Q plot showed heavier lower tail
- **Variance behavior:** Log transformation was applied to stabilize variance
- **Autocorrelation:** ACF and PACF plots indicated strong seasonal patterns

---

## 🧪 Technologies

- **Language:** R
- **Libraries:** `forecast`, `ggplot2`, `tseries`, `urca`, `TSA`, `FinTS`, `DescTools`, `fUnitRoots`, `patchwork`, `dplyr`
- **Models:** ARIMA, SARIMA, ETS (Exponential Smoothing)

---

## 🌟 Key Features

- 📈 STL decomposition of seasonal patterns
- 🧪 ADF, KPSS, McLeod-Li, and Ljung-Box residual diagnostics
- 🔍 ACF/PACF-guided model development
- 🔁 Log transformation, seasonal differencing
- 🔍 Model comparison using in-sample and out-of-sample accuracy

---

## 📈 Methodology

1. **Exploratory Data Analysis**: Visualizations, summary stats, and seasonality analysis
2. **Data Transformation**: Log transformation and STL decomposition
3. **Model Building**:
   - **Basic ARIMA** (non-seasonal)
   - **Auto SARIMA** via `auto.arima()`
   - **Grid SARIMA** selected as best final model
   - **ETS (M,N,A)** for benchmark
4. **Model Evaluation**:
   - Forecast accuracy: RMSE, MAE, MAPE
   - Residual diagnostics: ACF, Ljung-Box, McLeod-Li

---

## 📊 Forecast Accuracy

Forecast performance was evaluated on a holdout test set. The table below summarizes error metrics only (no AIC/BIC comparison across different model families).

| Model                         | RMSE     | MAE      | MAPE    | Verdict                         |
|------------------------------|----------|----------|---------|----------------------------------|
| SARIMA(1,0,3)(0,1,1)[12]      | 0.0951   | 0.0694   | 0.655%  | ✅ Best model overall            |
| Auto SARIMA(2,0,1)(0,1,1)[12] | 0.0953   | 0.0696   | 0.656%  | Close second                    |
| Basic ARIMA(2,0,2)            | 0.1594   | 0.1197   | 1.13%   | ❌ Misses seasonality            |
| ETS(M,N,A)                   | 0.1016   | 0.0779   | 0.736%  | ❌ Residual autocorrelation present |

---

## ⚙️ Getting Started

To run the project locally:

```r
# Install required libraries
install.packages(c("forecast", "tseries", "ggplot2", "urca", "DescTools",
                   "FinTS", "patchwork", "TSA", "fUnitRoots", "dplyr"))

# Load and run the script
source("gas_consumption_Ca.R")

