# Deutsche-Bahn Passenger Prediction
Repo of Data Science Projects

## Project Overview

This project develops a predictive model that forecasts the number of people visiting a particular train station. It uses a dataset containing various features such as the date, time, day of the week, week of the year, and month, as well as the target variable "traffic" (number of people visiting a station).

The dataset contains the passenger-traffic for certain Trainlines in Hamburg, Germany with detailed arrivals and departments for 4 Months, starting November 2016 to March 2017.

Two different types of models were examined: random forest and XGBoost. After the models were trained and optimized, it was found that the XGBoost model performed significantly better compared to the Random Forest model.

## Data preparation

Data preparation includes reading the data, removing zero values, and transforming the data by converting the date into other features such as day of the week, week of the year, and month. Also, the data is sorted to maintain the chronological order.

For categorical features, one-hot encoding was applied. Then, the data were divided into training and testing data.

## Modeling and Evaluation
### Random Forest

First, a random forest regressor was applied to the data. The parameters were set to n_estimators=50 and max_depth=10. After training and prediction, the R² and MAE values were calculated to evaluate the performance of the model.

To further improve the model, a hyperparameter search was performed using Bayesian Optimization. The best hyperparameters found were n_estimators=30 and max_depth=20.

After tuning the random forest, the predictions were OK. However, a deviation of passenger behavior was recognized while the school-vacation in march.

For this reason, the march data was excluded from the model, because there was no data to train this part of the model.

### XGBoost

Next, an XGBoost model was trained. Similar to the Random Forest, a hyperparameter search was performed. The best hyperparameters found were n_estimators=200, learning_rate=0.1, and max_depth=9.

Performance was again evaluated and the XGBoost model showed better performance than the Random Forest model.
## Adjustment of predictions

Added Constant: Since the model did not have access to data that could have learned the holiday pattern, a constant factor was applied to adjust the predictions for that particular period.
## Conclusions and considerations for the future

The XGBoost model has proven to be effective and can be used to guide how many people will frequent a particular station. However, it is important to note that the model may differ in the future as cities may change, pandemics may occur, or regulatory changes may be introduced. Therefore, it is recommended that the model be maintained at appropriate intervals.

It would also be helpful to collect additional data, particularly data that can reflect the impact of school vacations on traffic. This would allow the model to learn these patterns and make the predictions 
