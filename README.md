# Global Weather & Air Quality Analysis & Predictive Modeling
**Overview**

This project provides a complete data science workflow for analyzing and predicting global weather and air-quality metrics. It includes data cleaning, exploratory data analysis (EDA), machine learning modeling, scenario forecasting, and dashboard-ready output generation. The dataset contains over 100,000 global observations with more than 40 environmental features.


**Dataset Description**

The dataset includes four major types of features:

**Geographical Data:** Country, Latitude, Longitude  
**Weather Metrics:** Temperature, Humidity, Pressure, Wind Speed  
**Air Quality Metrics:** PM2.5, PM10, CO, Ozone, AQI  
**Temporal Data:** Timestamps, Sunrise/Sunset, Moon phases  

Data Cleaning & Feature Engineering
1. Missing Value Handling

Median/mean imputation performed per country to preserve local characteristics.

2. Outlier Treatment

Clipping used to fix physically impossible values.

Winsorization applied to smooth extreme values caused by faulty sensors.

3. Datetime Feature Extraction

Derived additional features:

last_updated_hour, last_updated_minute

sunrise_hour, sunset_hour

moonrise_hour, moonset_hour

4. Ordinal Encoding for Cyclical Variables

Wind Direction (N → NE → ... → NNW)

Moon Phase (New → Waxing → Full → Waning)

📊 Dataset Summary

The dataset includes four major categories of variables:

Category	Description	Examples
Geographical	Location context	Country, Latitude, Longitude
Weather Metrics	Atmospheric measurements	Temperature, Humidity, Pressure, Wind Speed
Air Quality Metrics	Pollution levels	PM2.5, PM10, CO, Ozone, AQI
Temporal	Time-based signals	Timestamp, Sunrise, Sunset, Moonrise
🧹 Data Cleaning & Feature Engineering
✔ Missing Value Handling

Median/mean imputation based per country, preserving regional patterns.

✔ Outlier Treatment

Clipping physically impossible values (e.g., negative precipitation).

Winsorization to smooth extreme sensor errors.

✔ Datetime Processing

Derived features include:

last_updated_hour, last_updated_minute

sunrise_hour, sunset_hour

moonrise_hour, moonset_hour

✔ Ordinal Encoding for Cyclical Variables

Used for:

Wind Direction (N → NE → E → ...)

Moon Phase (New → Waxing → Full → Waning)

📈 Exploratory Data Analysis (EDA)

Key findings include:

🔹 Distributions

Temperature clusters around 20–30°C.

PM2.5 and PM10 are highly skewed—few regions experience extreme pollution.

🔹 Relationships

Temperature and humidity exhibit expected inverse trends.

PM2.5 strongly correlates with PM10 and AQI.

🔹 Country-Level Rankings

Computed Top 10 and Bottom 10 countries for:

PM2.5

AQI

Temperature

🔹 Temporal Patterns

Pollution peaks during morning/evening rush hours.

Temperature peaks in the afternoon.

🔹 Geospatial Insights

Global scatter maps reveal continental and regional pollution hotspots.

🤖 Machine Learning Models

Three regression models were tested for each target variable:

Random Forest Regressor

XGBoost Regressor

KNN Regressor

📌 Best Model for All Targets: Random Forest

Performance Summary:

Target	Test R²	MAE	RMSE
Temperature	~0.999	~0.005	~0.02
PM2.5	~0.986	~1.69	~4.78
AQI	~0.964	~0.07	~0.18

The complete preprocessing pipeline + model was saved as .pkl files for deployment.

🔮 Scenario-Based Forecasting

A future-like scenario was simulated by adding +6 hours to the time-based features.
The models then predicted:

pred_PM25

pred_AQI

pred_Temp

These predictions were aggregated by country to generate:

Predicted Top 10 and Bottom 10 Countries for environmental risks.

This allows forward-looking policy and health planning.

📁 Final Deliverables
✔ Global_Weather_Final_With_Predictions.csv

Includes:

Cleaned dataset

Engineered features

Predictions for PM2.5, AQI, and Temperature

Scenario-based predictions

✔ Rankings Dataset

Country-level historical and predicted rankings (Top 10 & Bottom 10).

✔ Tableau Dashboard

Interactive visualization for global weather & air quality insights.

▶️ Using the Saved Models
import joblib
import pandas as pd

model = joblib.load("models/best_model_pm2.5.pkl")
pred = model.predict(new_feature_dataframe)
print(pred)


Ensure the input DataFrame uses the same feature schema as the training data.

🚀 Future Enhancements

Time-series models (ARIMA, LSTM, Prophet)

Integration of satellite-derived features (AOD)

Cloud deployment with automated refresh pipelines
