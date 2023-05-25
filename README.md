# Big Data Project with Spark

Big Data project aiming to utilize PySpark.

# Kaggle Competition

You are provided with historical daily sales data. The task is to predict the total quantity of products sold in each store for the test set. Note that the list of stores and products slightly changes every month. Creating a robust model that can handle these situations is part of the challenge.

# Why do we use PySpark?

Throughout the project, PySpark was used to parallelize all the actions related to data reading, as well as all the preprocessing applied to them before using them in training linear regression and Random Forest Regression models, which are also included in the Spark package for Python. Finally, the prediction is obtained by parallelizing the possible processes throughout its development.

# What did we do?

First, predict the top-level. (For example, predict the total sales)
Next, calculate weights denoting the proportion of total sales to be allocated to the bottom-level forecast (e.g., the contribution of item sales to total sales).
There are different ways to obtain the "weights."

    Historical Mean Ratios - Simple average of the item's contribution to sales in the past months.
    Mean Ratio Ratios - The weight is the ratio of the mean value of the lower series to the mean value of the total series (e.g., Weight(item1) = mean(item1) / mean(total_sales)).
    Forecasted Ratios - Predict the ratio in the future using changes in past ratios.
    Use these weights to calculate the base forecasts and other levels.

# Conclusions

The Random Forest regression model performs better than the linear regression model. There are still many things that can be improved to obtain better predictions, such as:

    Using a stricter range for outlier values (sales count and item prices).
    Filling missing data with the mean or median of the product across all months instead of just 0.
    Designing more features based on lag and moving window.
    Creating an ensemble model using multiple different regression models.
    Using the statsmodel library to extract more accurate trend and seasonality from time series data for use as features.
    Employing a hyperparameter tuning algorithm. PySpark only supports K-Fold Cross Validation, which is not suitable for time series forecasting problems.
    Using a recurrent neural network such as LSTM instead of converting this dataset into a regression problem.
