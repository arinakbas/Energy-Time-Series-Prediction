# Forecasting Turkey's Hourly Electricity Consumption

## Problem Description
This project aims to predict Turkey's hourly electricity consumption (MWh) using weather conditions and temporal/calendar features. Accurate short-term load forecasting is critical for grid balancing, day-ahead market bidding, and infrastructure planning.

## Dataset Source
- **Consumption data:** EPİAŞ (EXIST) Transparency Platform
- **Weather data:** Open-Meteo API (temperature, humidity, wind, cloud cover, precipitation)
- **Calendar features:** Manually engineered (holidays, Ramadan, weekends, cyclical hour encoding, lag variables)
- **Size:** 8 592 hourly observations (Jan–Dec 2025), 24 features

## How the Three Projects Connect
- **P1 (EDA):** Explores the dataset, identifies key predictive features (lag variables, temperature, hour, weekend flag), and documents data quality.
- **P2 (Modelling):** Trains regression models — from baseline linear models to polynomial and regularized regression — using the features and insights from P1.
- **P3 (Evaluation):** Evaluates model performance, adds uncertainty quantification via MC Dropout, and interprets results.

## P2 Summary
Five regression models were compared on a chronological 60/20/20 split. The baseline single-feature model (load_lag_24) achieved Test R² ≈ 0.68. Multiple linear regression with all 25 features improved to R² ≈ 0.80. Polynomial regression (degree 3 on top-5 features) reached the best Test R² ≈ 0.91. Ridge and Lasso performed similarly to plain MLR; Lasso zeroed out 8 redundant features. The remaining non-linear patterns motivate the use of deep learning models in P3.
