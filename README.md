# Data_Science
Repo of Data Science Projects

## Project Overview

This project develops a predictive model that forecasts the number of people visiting a particular train station. It uses a dataset containing various features such as the date, time, day of the week, week of the year, and month, as well as the target variable "traffic" (number of people visiting a station).

Two different types of models were examined: random forest and XGBoost. After the models were trained and optimized, it was found that the XGBoost model performed significantly better compared to the Random Forest model.

## Data preparation

Data preparation includes reading the data, removing zero values, and transforming the data by converting the date into other features such as day of the week, week of the year, and month. Also, the data is sorted to maintain the chronological order.

For categorical features, one-hot encoding was applied. Then, the data were divided into training and testing data.

## Modeling and Evaluation
### Random Forest

First, a random forest regressor was applied to the data. The parameters were set to n_estimators=50 and max_depth=10. After training and prediction, the R² and MAE values were calculated to evaluate the performance of the model.

To further improve the model, a hyperparameter search was performed using Bayesian Optimization. The best hyperparameters found were n_estimators=30 and max_depth=20.

After tuning the random forest, the predictions were only semi-accurate.

### XGBoost

Next, an XGBoost model was trained. Similar to the Random Forest, a hyperparameter search was performed. The best hyperparameters found were n_estimators=200, learning_rate=0.1, and max_depth=9.

Performance was again evaluated and the XGBoost model showed better performance than the Random Forest model.
## Adjustment of predictions

It was found that the model had difficulty predicting the correct values for a given time period (Easter vacations). Since the model did not have access to data that could have learned this pattern, a constant factor was applied to adjust the predictions for that particular period.
## Conclusions and considerations for the future

The XGBoost model has proven to be effective and can be used to guide how many people will frequent a particular station. However, it is important to note that the model may differ in the future as cities may change, pandemics may occur, or regulatory changes may be introduced. Therefore, it is recommended that the model be maintained at appropriate intervals.

It would also be helpful to collect additional data, particularly data that can reflect the impact of school vacations on traffic. This would allow the model to learn these patterns and make the predictions 
