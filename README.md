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

![Image_1](https://raw.githubusercontent.com/ksokoll/Deutsche-Bahn-Passenger-Prediction/6aa78b761e0861a346b1e117113e784a2fec02c2/Figure%201%20-%20Forest%20attempt%201.png)

*Figure 1: First attempt of using Random Forest. There is a visible anomaly beginning March 2017.*

For this reason, the march data was excluded from the model, because there was no data to train this part of the model.

![Image_2](https://github.com/ksokoll/Deutsche-Bahn-Passenger-Prediction/blob/main/Figure%202%20-%20Forest%20attempt%202.png?raw=true)

*Figure 2: Adjusted data foundation for random forest*

### XGBoost

Next, an XGBoost model was trained. Similar to the Random Forest, a hyperparameter search was performed. The best hyperparameters found were n_estimators=200, learning_rate=0.1, and max_depth=9.

Performance was again evaluated and the XGBoost model showed better performance than the Random Forest model.

![Image_3](https://github.com/ksokoll/Deutsche-Bahn-Passenger-Prediction/blob/main/Figure%203%20-%20XGBoost%201.png?raw=true)

*Figure 3: Results of XGBoost after Hyperparameter-Optimization via Hyperopt*

## Adjustment of predictions

Added Constant: Since the model did not have access to data that could have learned the holiday pattern, a constant factor was applied to adjust the predictions for that particular period.

![Image_4](https://raw.githubusercontent.com/ksokoll/Deutsche-Bahn-Passenger-Prediction/63280ba454ab3efa6d1ce7e4345c9997ed6fe855/Figure%204%20-%20XGBoost%202.png)

*Figure 4: Above XGBoost model on the whole dataset, including March 2017, with the added constant of 0,5*

## Conclusions and considerations for the future

The XGBoost model has proven to be effective and can be used to guide how many people will frequent a particular station. However, it is important to note that the model may differ in the future as cities may change, pandemics may occur, or regulatory changes may be introduced. Therefore, it is recommended that the model be maintained at appropriate intervals.

It would also be helpful to collect additional data, particularly data that can reflect the impact of school vacations on traffic. This would allow the model to learn these patterns and make the predictions 
