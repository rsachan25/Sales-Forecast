# Rossmann Sales Forecasting Capstone Project
## Table of Contents
- [Introduction](#introduction)
- [Problem Statement](#problem-statement)
- [Dataset](#dataset)
- [Data Preprocessing](#data-preprocessing)
- [Modeling Approach](#modeling-approach)
- [Evaluation Metrics](#evaluation-metrics)
- [Results](#results)
- [Next Steps](#next-steps)
- [Conclusion](#conclusion)
## Introduction
This project involves building a time series forecasting model for Rossmann's daily sales across 1,115 stores. The goal is to predict sales for the next six weeks, using historical sales data along with external factors like promotions, holidays, and competition.

## Problem Statement
Rossmann, a major European drugstore chain, relies on individual store managers to forecast daily sales six weeks in advance. However, these predictions are inconsistent and often inaccurate. The aim of this project is to develop a robust predictive model to forecast sales using time series techniques and external features.

## Dataset
We were provided with two main datasets:

* **train.csv:** Contains daily sales data for 1,115 stores over several years.
* **store.csv:** Contains information on stores such as competition distance, promotional data, and store type.
  
**Key columns:**

* **Store:** Unique identifier for each store.
* **Sales:** Daily sales of the store (target variable).
* **Promo:** Whether the store had a promotion that day.
* **CompetitionDistance:** Distance to the nearest competitor.
* **StateHoliday, SchoolHoliday:** Flags for holidays.

## Data Preprocessing
* **Missing Values:** Columns with over 40% missing data were dropped. Imputation techniques were applied to other columns.
* **Feature Engineering:** Date features (Year, Month, Day, etc.) were extracted, and datasets were merged for complete analysis.
* **Outlier Handling:** Outliers, especially in variables like CompetitionDistance, were treated.
* **Stationarity:** Time series stationarity was checked using the Augmented Dickey-Fuller (ADF) test.
## Modeling Approach
Several models were tested to forecast sales, including:

* **VARMAX:** A multivariate time series model that accounts for multiple time series and external variables like promotions and holidays.
* **SARIMAX:** A seasonal ARIMA model with exogenous variables.
  
**Steps:**
* **Granger Causality & Johansen Test:** To check for causal relationships between variables (e.g., Customers and Sales).
* **Parameter Selection:** Optimal p and q values were chosen based on PACF and ACF plots.
* **Model Training:** Each store’s model was trained using historical data, and predictions were made for the next six weeks.
## Evaluation Metrics
The models were evaluated using:

* **RMSE (Root Mean Squared Error):** Measures the average prediction error.
* **MAPE (Mean Absolute Percentage Error):** Measures error as a percentage.
  
Sample results for Store 1:
| Model  | RMSE | MAPE |
| ------------- | ------------- | ------------- |
| VARMAX  | 800.6 | 17.05% |
| SARIMAX  | 477.6 | 9.20% |

## Results
* SARIMAX consistently outperformed VARMAX across the majority of stores, achieving lower RMSE and MAPE scores.
* Sales trends were evident, but there was minimal seasonality across stores.
* External factors like promotions, holidays, and competition had a significant impact on sales.
## Next Steps
* **Model Fine-Tuning:** Fine-tune models for stores with high error rates.
* **External Factors:** Explore the inclusion of additional variables like weather and local events.
* **Live Forecasting:** Evaluate model performance in a live environment.
## Conclusion
The Rossmann Sales Forecasting project demonstrates the application of time series analysis and multivariate forecasting techniques to predict retail sales effectively. By employing advanced models such as SARIMAX and VARMAX, we were able to achieve substantial improvements in forecasting accuracy. The SARIMAX model, in particular, proved to be more effective, providing valuable insights into the factors influencing sales. Future work involves refining the model for better performance, integrating additional external factors, and deploying the model in a live forecasting environment to further validate and enhance its accuracy.

