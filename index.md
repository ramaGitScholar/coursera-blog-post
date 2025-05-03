---
title: "Data Analysis and Interpretation Capstone Coursera"
author: rama
date: 2025-05-02
---

# Predicting Crop Loss from Storm Events

---

## Introduction to the Research Question

This study aims to identify the most significant factors contributing to crop loss caused by extreme weather events across the United States. Using historical storm data, we examine how various event types—including hurricanes, tornadoes, hail, floods, droughts, lightning, high winds, snow, and extreme temperatures—impact agricultural outcomes.

The dataset contains critical information such as event type, magnitude, geographic location, storm category, and reported damages to both property and crops. The target variable, `DAMAGE_CROPS`, represents the estimated financial impact of storms on agricultural production. Key features include `EVENT_TYPE`, `MAGNITUDE`, `FLOOD_CAUSE`, `CATEGORY`, `TOR_F_SCALE`, `STATE`, `YEAR`, and geographical coordinates.

While the United States is not a tropical country, severe weather events—especially in the Midwest and Southern regions—pose significant threats to agriculture. This research leverages data-driven modeling to help mitigate these risks and inform future food security efforts.

---

## Method

### Sample

**Population**  
The population includes all recorded extreme weather events in the United States between January 2013 and October 2015 that impacted agriculture, particularly those causing crop damage.

**Sample Selection Criteria**  
The data were filtered to retain only events with complete records on crop damage, magnitude, and geographic location (latitude and longitude) to ensure analytical accuracy and statistical validity.

**Sample Size**  
After cleaning and filtering, a total of 59,161 observations were retained for analysis. These reflect diverse extreme weather events and affected regions across the U.S.

**Sample Description**  
The dataset includes:
- `EVENT_TYPE`: Type of event (e.g., storm, tornado, flood)
- `MAGNITUDE`: Intensity of the event (e.g., wind speed, rainfall)
- `BEGIN_LAT` / `BEGIN_LON`: Geographical coordinates of the event
- `DAMAGE_CROPS`: Monetary value of crop damage (log-transformed for modeling)

---

## Measures

**Response Variable**
- **Crop Damage (`DAMAGE_CROPS`)**: Financial impact of storm events on crops, transformed using `log(1 + x)` to address right-skewness and zero inflation.

**Predictor Variables**
- `MAGNITUDE`: Numeric intensity of the event
- `BEGIN_LAT`: Latitude
- `BEGIN_LON`: Longitude

Additional variables like `EVENT_TYPE`, `STATE`, and `CATEGORY` will be considered in extended models (e.g., Lasso regression).

---

## Data Preprocessing

- Converted non-numeric `DAMAGE_CROPS` values into numeric by stripping symbols and characters.
- Removed rows with missing values in key variables.
- Applied logarithmic transformation (`log1p`) to reduce skewness in crop damage.

---

## Analyses

### Exploratory Data Analysis (EDA)

The distribution of crop damage is highly skewed, with:
- **Mean (log damage)**: 0.2417  
- **Median**: 0.0000  
- **Maximum**: 18.42  

A large number of events resulted in no reported crop damage. Scatter plots and correlations showed weak relationships between `MAGNITUDE` and `LOG_DAMAGE_CROPS`.

### Modeling Approach

A baseline multiple linear regression was performed using:
- **Predictors**: `MAGNITUDE`, `BEGIN_LAT`, `BEGIN_LON`  
- **Results**:
  - All predictors were statistically significant (*p* < 0.05)
  - Adjusted R-squared = 0.005 (explaining only 0.5% of variance)

### Model Evaluation

- **RMSE**: 1.4965  
- **MSE (Test Set)**: 2.2397  
- **R-squared (Test Set)**: 0.005  

These metrics indicate the baseline model performs poorly in predicting crop damage.

---

## Discussion

### Descriptive Statistics

| Variable           | Min      | 1st Qu. | Median | Mean   | 3rd Qu. | Max         |
|-------------------|----------|---------|--------|--------|---------|-------------|
| DAMAGE_CROPS_NUM  | 0        | 0       | 0      | 12,044 | 0       | 100,000,000 |
| MAGNITUDE         | 0.00     | 1.00    | 50.00  | 32.91  | 52.00   | 109.00      |
| BEGIN_LAT         | 17.73    | 34.32   | 38.93  | 38.11  | 41.80   | 49.00       |
| BEGIN_LON         | -124.34  | -97.81  | -90.50 | -90.48 | -82.49  | -64.78      |
| LOG_DAMAGE_CROPS  | 0.0000   | 0.0000  | 0.0000 | 0.2417 | 0.0000  | 18.4207     |

The dominance of zero values limits the performance of traditional linear models.

### Multivariate Regression

- **MAGNITUDE**: β = -0.0014 (*p* < 0.001)  
- **BEGIN_LAT**: β = 0.0209 (*p* < 0.001)  
- **BEGIN_LON**: β = 0.0039 (*p* < 0.001)  
- **Model F-statistic**: 110.8 (*p* < 2.2e-16)  
- **Adjusted R²**: 0.0055  
- **Residual Std. Error**: 1.501  

Despite statistical significance, effect sizes are small and explain very little variance.

### Predictive Accuracy

- **RMSE**: 1.4965  
- **R² (Test Set)**: 0.005  
- **MSE (Test Set)**: 2.2397  

This underscores the limited utility of the current predictors in accurately forecasting crop damage.

---

## Interpretation and Implications

Although some predictors are statistically associated with crop damage, they are not practically useful for prediction. Potential reasons include:

- **Missing Variables**: Absence of key predictors like crop type, soil condition, and precipitation.
- **Zero Inflation**: Prevalence of zero values in the response variable complicates modeling.
- **Geospatial Complexity**: Nonlinear and region-specific interactions not captured by linear regression.

---

## Recommendations for Future Work

- Use zero-inflated or hurdle models to manage the excess of zero values.
- Incorporate additional features (e.g., crop type, real-time climate data).
- Apply non-linear or ensemble models (e.g., random forests, gradient boosting).
- Evaluate event-type specific models to capture differential impacts.
