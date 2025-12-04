# Global Weather & Air Quality Analysis & Predictive Modeling
**Overview**

This project provides a complete data science workflow for analyzing and predicting global weather and air-quality metrics. It includes data cleaning, exploratory data analysis (EDA), machine learning modeling, scenario forecasting, and dashboard-ready output generation. The dataset contains over 100,000 global observations with more than 40 environmental features.



## Project Structure
```
├── data/
│   ├── Global_Weather_Repository.csv
│   ├── Global_Weather_Final_With_Predictions.csv
│
├── notebooks/
│   ├── EDA_and_Modeling.ipynb
│   ├── Final_Predictions.ipynb
│
├── models/
│   ├── best_model_pm2.5.pkl
│   ├── best_model_aqi.pkl
│   ├── best_model_temperature.pkl
│
├── reports/
│   ├── Final_Project_Report.pdf
│   ├── Visualization_Report.pdf
│
└── README.md
```


**## Dataset Description**

The dataset includes four major types of features:

**Geographical Data:** Country, Latitude, Longitude  
**Weather Metrics:** Temperature, Humidity, Pressure, Wind Speed  
**Air Quality Metrics:** PM2.5, PM10, CO, Ozone, AQI  
**Temporal Data:** Timestamps, Sunrise/Sunset, Moon phases  

Data Cleaning & Feature Engineering
1. Missing Value Handling

- Median/mean imputation performed per country to preserve local characteristics.

2. Outlier Treatment

- Clipping used to fix physically impossible values.

- Winsorization applied to smooth extreme values caused by faulty sensors.

3. Datetime Feature Extraction

- Derived additional features:

    last_updated_hour, last_updated_minute

    sunrise_hour, sunset_hour

    moonrise_hour, moonset_hour

4. Ordinal Encoding for Cyclical Variables

- Wind Direction (N → NE → ... → NNW)

- Moon Phase (New → Waxing → Full → Waning


**Exploratory Data Analysis (EDA)**
    Key Insights

    - Temperature typically ranges between 20–30°C globally.

    - PM2.5 and PM10 distributions are heavily skewed due to pollution hotspots.

    - Strong correlation found between PM2.5, PM10, and AQI.

    - Humidity and temperature show expected inverse patterns.

    - Pollution levels peak during morning and evening rush hours.

    - Country-level rankings were generated for PM2.5, AQI, and Temperature.

    - Geospatial analysis highlights global pollution clusters.

    
Machine Learning Modeling

    Three regression models were evaluated:

    - Random Forest Regressor

    - XGBoost Regressor

    - KNN Regressor

**Best Model**

Random Forest performed best for all three targets.

| Target      | Test R² | MAE    | RMSE  |
| ----------- | ------- | ------ | ----- |
| Temperature | ~0.999  | ~0.005 | ~0.02 |
| PM2.5       | ~0.986  | ~1.69  | ~4.78 |
| AQI         | ~0.964  | ~0.07  | ~0.18 |


**Scenario-Based Forecasting**

A future scenario was simulated by shifting the timestamp hour by +6 hours.
The models predicted:

    - pred_PM25

    - pred_AQI

    - pred_Temp

    Predictions were aggregated by country to generate projected:

    - Top 10 and Bottom 10 polluted countries

    - Top 10 and Bottom 10 AQI rankings

    - Temperature-based country rankings

    - This enables forward-looking environmental risk analysis.


Final Deliverables  
1. Global_Weather_Final_With_Predictions.csv

Includes:

All original cleaned data

Engineered features

Model predictions

Scenario predictions

2. Country Ranking Dataset

Contains historical and predicted top/bottom 10 country lists.

3. Tableau Dashboard

Interactive visualization of:

Global air quality

Temperature heatmaps

Before vs After predictions

**Future Enhancements**

Add time-series forecasting (LSTM, ARIMA, Prophet)

Integrate satellite-derived features (AOD)

Deploy automated model update pipelines using Docker/Kubernetes


