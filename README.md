# Forecasting Turkey's Hourly Electricity Demand

An end-to-end machine-learning project on Turkey's hourly electricity consumption, spanning exploratory analysis (P1), regression modelling (P2), and classification with unsupervised analysis (P3).

## Problem Description
The goal is to anticipate Turkey's hourly electricity demand from weather conditions, calendar context, and recent load history. Accurate forecasts let grid operators balance generation against demand, schedule reserves, and avoid both blackouts and wasted capacity. P1/P2 frame it as regression (predict consumption in MWh); P3 reframes it as binary classification (predict whether an hour is High- or Low-demand relative to the training median).

## Dataset Source
- **Consumption data:** EPİAŞ (EXIST) Transparency Platform
- **Weather data:** Open-Meteo API (temperature, humidity, wind, cloud cover, precipitation)
- **Calendar features:** Engineered (holidays, Ramadan, weekend, cyclical hour encoding, 24h/168h load lags)
- **Size:** 8 592 hourly observations (2025), 24 raw features

## Project Structure & Findings

### P1 — Exploratory Data Analysis (`p1/`)
Clean dataset (no missing values/duplicates). Key signals: the 24h and 168h load lags dominate, temperature has a U-shaped effect on demand, and weekend/holiday flags shift consumption substantially.

### P2 — Regression Modelling (`p2/`)
Feature engineering (log transform, temperature x weekend interaction, temperature bins, hour-mean-load aggregate) on a chronological 60/20/20 split. Models from a single-feature baseline to multiple linear, polynomial, Ridge, and Lasso regression. Best model: degree-3 polynomial, **test R² ≈ 0.91**.

### P3 — Classification & Unsupervised Analysis (`p3/`)
Binarised target (High/Low demand at training median). PCA needs 11 components for 90% variance; clustering shows only weak natural structure (silhouette ≈ 0.2). Five classifiers tuned with GridSearchCV; best model **Gradient Boosting** with **test accuracy 0.948, macro-F1 0.947, AUC-ROC 0.989**. Only 5.2% of test hours are misclassified, almost all sitting near the decision threshold. The dominant predictors remain the load lags and calendar features — consistent with P1/P2.
