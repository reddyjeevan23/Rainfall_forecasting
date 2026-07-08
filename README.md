# Rainfall Forecasting (Australia)

Predicting next-day rain across Australia using historical weather station data and comparing three classification models.

## Objective

Predict whether it will rain tomorrow (RainTomorrow) at Australian weather stations, using daily observations such as temperature, humidity, wind speed, and pressure.

## Data Source

Daily weather observations from numerous Australian weather stations, originally sourced from the Australian Bureau of Meteorology (bom.gov.au/climate/data) and pulled via Kaggle's weather-dataset-rattle-package. The raw data spans more than a decade and required cleaning before modeling.

## Methodology

Step 1: Cleaned the raw dataset, dropping unusable or incomplete columns (Date, Evaporation, Sunshine, Cloud9am/3pm, RISK_MM, Location, WindGustDir, WindDir9am/3pm) and removing remaining rows with missing values.
Step 2: Ran chi-square tests on categorical variables and correlation analysis on numeric variables to identify the strongest predictors.
Step 3: Converted categorical Yes/No fields to 0/1 and split the data 75% train / 25% test.
Step 4: Trained and compared three classification models: Logistic Regression, Decision Tree, and Naive Bayes.

## Results

| Model | Accuracy | Kappa |
|-------|----------|-------|
| Logistic Regression | 80.46% | 0.3124 |
| Decision Tree | 79.3% | 0.1753 |
| Naive Bayes | 78.19% | 0.1602 |

Logistic Regression performed best, using WindGustSpeed, Humidity3pm, and Pressure3pm as predictors. Its ROC/AUC on training data matched its test accuracy, indicating the model generalizes reasonably well rather than overfitting.

## Limitations

Note 1: The raw dataset required significant cleaning and had many incomplete fields.
Note 2: All three models tended to over-predict the positive (rain) class, with a true positive rate of roughly 60%.

## Tech stack

R, ggplot2, caret, caretEnsemble, ROCR, corrplot, e1071

## Files

File 1: INFO659_Final_Project.Rmd - full analysis notebook (data cleaning, modeling, evaluation).
File 2: INFO659_Final_Project.nb.html - rendered notebook output.
