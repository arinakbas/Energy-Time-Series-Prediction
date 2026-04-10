# Energy-Time-Series-Prediction

## Problem Description
This project aims to predict Turkey's hourly electricity consumption (MWh) using weather conditions and temporal/calendar features. Accurate short-term load forecasting is critical for grid balancing, day-ahead market bidding, and infrastructure planning.

## Dataset Source
- **Consumption data:** EPİAŞ (EXIST) Transparency Platform
- **Weather data:** Open-Meteo API (temperature, humidity, wind, cloud cover, precipitation) (The mean of Istanbul, Izmır, Ankara has been calculated)
- **Calendar features:** Manually engineered (holidays, Ramadan, weekends, cyclical hour encoding, lag variables)
- **Size:** 8592 hourly observations (Jan–Dec 2025), 24 features

## How the Three Projects Connect
- **P1 (EDA):** Explores the dataset, identifies key predictive features (lag variables, temperature, hour, weekend flag), and documents data quality.
- **P2 (Modelling):** Trains regression models — from baseline linear models to LSTM / Dual-Attention networks — using the features and insights from P1.
- **P3 (Evaluation):** Evaluates model performance (MAE, RMSE, R²), adds uncertainty quantification via MC Dropout, and interprets results.
