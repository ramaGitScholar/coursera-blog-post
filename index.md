---
title: "Data Analysis and Interpretation Capstone Coursera"
author: rama
date: 2025-05-02
---

# Predicting Crop Loss from Storm Events

## 🔍 Introduction to Research Question

This study aims to identify the most significant factors that contribute to crop loss resulting from extreme weather events across the United States. Using historical storm data, we explore how different types of weather events—such as hurricanes, tornadoes, hail, floods, droughts, lightning, high winds, snow, and extreme temperatures—affect agricultural outcomes.

The dataset includes key information such as event type, magnitude, geographic location, storm category, and associated damages, including both property and crop loss. The target variable for this study is DAMAGE_CROPS, representing the estimated financial impact of storms on agricultural output. Key features include EVENT_TYPE, MAGNITUDE, FLOOD_CAUSE, CATEGORY, TOR_F_SCALE, STATE, YEAR, and geographical coordinates.

Although the United States is not a tropical region, extreme weather events such as tornadoes, hurricanes, and blizzards still pose significant risks to agriculture, particularly in the midwestern and southern states. As a data engineer, I believe it’s essential to harness data and predictive modeling to mitigate these risks and enhance food security. By analyzing historical storm events and their impact on crops, this study seeks to provide valuable insights to help farmers and policymakers make more informed decisions.

## Method
### Sample
The sample included N = 166,048 records from the dataset containing information about extreme weather events that impacted agricultural crops in the United States, spanning from January 2013 to October 2015. All records were related to significant weather events that affected crop yields, including hurricanes, tornadoes, floods, droughts, and other extreme weather phenomena.

### Measures
The response variable of interest is the crop damage measured in monetary value or percentage of crop loss for each weather event. This was calculated from official damage reports available in the dataset.

Predictor variables include:

1. Event Type: Categorical variable representing the type of extreme weather event (e.g., hurricane, tornado, flood, etc.).

2. Event Magnitude: Continuous variable indicating the severity of the weather event (e.g., wind speed, rainfall amount).

3. Temperature Extremes: Continuous variable representing the deviation in temperature during the event (e.g., high temperatures, low temperatures).

4. Location: Categorical variable indicating the state or region affected by the weather event.

5. Precipitation: Continuous variable representing the amount of precipitation recorded during the event.

6. Wind Speed: Continuous variable representing the highest wind speed recorded during the event.

7. Other Meteorological Conditions: Additional relevant weather factors such as lightning, hail, snow, etc.

### Analyses
The distributions for the predictors and the response variable (crop damage) were examined by evaluating frequency tables for categorical variables and calculating the mean, standard deviation, and minimum and maximum values for quantitative variables.

#### Exploratory Data Analysis (EDA):

- Scatter plots, box plots, and correlation matrices were used to visually inspect relationships between predictors and the response variable.

- Pearson correlation was used to identify linear relationships between continuous predictor variables and crop damage.

#### Random Sampling:
To efficiently explore the data, a random sample was drawn from the dataset, comprising 10% of the total data (N=16,600) to facilitate quicker exploratory analysis. The sample was selected randomly to ensure that it accurately represented the diversity of events and locations.

#### Lasso Regression:
To identify the most significant predictors of crop damage, lasso regression was used with the least angle regression selection algorithm. The model was estimated on a training dataset consisting of 60% of the random sample (N=9,960), while the remaining 40% (N=6,640) was used as the test dataset. All predictor variables were standardized to have a mean of 0 and a standard deviation of 1 before conducting the lasso regression analysis.

#### Cross-validation:
10-fold cross-validation was performed to assess model stability and prevent overfitting. The change in the cross-validation mean squared error (MSE) was used to identify the optimal subset of predictor variables that best explained crop damage.

#### Predictive Accuracy:
The mean squared error (MSE) of the predictive model was calculated by applying the model trained on the training dataset to the test dataset. This metric was used to evaluate the predictive accuracy of the model.
