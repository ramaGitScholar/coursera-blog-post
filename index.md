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
1. Population:
The population for this study includes extreme weather events recorded in the United States that have impacted agricultural crops. These events range from hurricanes, tornadoes, floods, droughts, hail, high winds, lightning, and other meteorological phenomena that could cause crop damage. The dataset spans from January 2013 to October 2015

2. Sample Selection Criteria:
The sample includes records from the dataset related to events that resulted in significant damage to crops. This selection was made to focus specifically on weather events that had a notable economic impact, measured by crop loss in monetary value or percentage of yield loss. Random sampling was used to select 10% of the data (N=16,600 records) to ensure a representative subset of the population. This sample represents various types of weather events, states, and crop damage levels.

3. Sample Size:
The sample size is 16,600 records, which accounts for 10% of the total dataset consisting of 166,000 records.

4. Sample Description:
The sample includes a variety of weather events from multiple states in the United States, each with varying levels of severity. The data includes:

- Event Type: Including hurricanes, floods, tornadoes, etc.

- Location: Events from different regions and states are included.

- Crop Damage: Ranging from low to high damage, measured in monetary value or percentage of yield loss.

- Other Meteorological Conditions: Includes precipitation, temperature extremes, wind speed, and other factors associated with weather events.

### Measures
.1 Description of Variables:

Response Variable:

- Crop Damage: The dependent variable representing the monetary value or percentage of crop loss as a result of the extreme weather event.

Predictor Variables:

- Event Type: Categorical variable representing the type of extreme weather (e.g., hurricane, tornado, flood).

- Event Magnitude: Continuous variable indicating the severity of the weather event (e.g., wind speed, rainfall amount).

- Temperature Extremes: Continuous variable representing temperature deviation during the event.

- Precipitation: Continuous variable representing the amount of precipitation recorded during the event.

- Wind Speed: Continuous variable representing the highest wind speed during the event.

- Location (State): Categorical variable indicating the state or region affected by the weather event.

2. Managing the Variables:

- Categorical Variables: Variables like Event Type and Location were encoded using dummy variables for inclusion in the analysis.

- Continuous Variables: All continuous variables (e.g., Event Magnitude, Precipitation, Wind Speed) were standardized to have a mean of 0 and standard deviation of 1 to ensure comparability.

- Creation of New Variables: For modeling purposes, new composite variables or binned versions of continuous variables were not created, as the focus was on analyzing the original variables' relationship to crop damage.

### Analyses
1. Statistical Methods:
The analysis focuses on identifying the best predictors for crop damage using various statistical techniques:

- Exploratory Data Analysis (EDA): Involves examining the distributions of the variables and identifying potential relationships using scatter plots, box plots, and correlation matrices.

- Pearson Correlation: To identify linear relationships between continuous predictor variables and crop damage.

- Lasso Regression: A method for variable selection, used to identify a subset of predictors that best explain crop damage while preventing overfitting.

2. Data Splitting:
The dataset will be split into training and test datasets. The training dataset will consist of 60% of the data (N=9,960 records), and the test dataset will include the remaining 40% (N=6,640 records). The training dataset will be used to fit the lasso regression model, while the test dataset will be used to evaluate the predictive accuracy of the model.

3. Cross-Validation:
10-fold cross-validation will be used to assess model stability and performance. This technique will divide the training dataset into 10 subsets, training the model on 9 subsets and testing on the remaining 1 subset, rotating this process to ensure each subset is used for validation. The cross-validation mean squared error (MSE) will be calculated at each step to identify the best subset of predictor variables.
