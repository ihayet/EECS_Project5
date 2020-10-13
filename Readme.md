Project 5 - World Wide Products Inc. - Forecasting Product Demand
--------------------------------------------------------------------

Data Cleaning:
---------------------
At first, I have isolated and narrowed down on a specific product from a specific category in a specific warehouse. The Order_Demand column represents the time series demand of this product. There seemed to be non-numerical characters in the Order_Demand column. I have used regex to remove these characters. Then, I have replaced the inifinite values in this column by the mean and sorted the dataframe by the date.

Preprocessing:
--------------------
At first, I have standardized the data and taken the first differences to improve stationarity. We can achieve stationarity through a constant mean, constant variance and no covariance from past data. I have performed two tests to check the stationarity of the data. The first test is an inspection of the rolling mean and rolling standard deviation to see if they are more or less constant. Then, I have carried out the Dickey-Fuller test to get a more statistical assurance of stationarity. For improving stationarity, I have taken the log transform (accounting for both positive and negative results) and standardized the log transformed values.

Data Exploration:
-------------------
I have used a seasonal_decomposition function to explore the trend, seasonality and residual of the decomposed data.

Forecasting:
------------------
I have used two forecasting approaches - ARIMA (Auto Regressive Integrated Moving Average) and HMM (Hidden Markov Model). 

ARIMA: For getting the order of ARIMA, I have used Auto-correlation function (for estimating Q value) and Partial auto-correlation function (for estimating P value). The Q and P values are the ones along the x axis for which the correlation along the y axis is 0. And, the D value is 1 since we have taken only first difference.

HMM: For the HMM model, I have used 4 hidden states to perform the forecasting.

For both approaches, I have used an inversion function to transform the forecast value to the original scale.

Analysis:
-----------------
Both the ARIMA (Auto Regressive Integrated Moving Average) and HMM (Hidden Markov Model) models have given a decent forecasting with MSE (Mean Squared Error) 0.53 and 1.11. The lesser MSE, the better. I am confident that the systematic preprocessing and feature engineering really helped the models to perform this good. At the same time, the hyperparameters for both ARIMA (p, d, q) and HMM (n_components) were chosen appropriately to achieve satisfactory forecasts.
