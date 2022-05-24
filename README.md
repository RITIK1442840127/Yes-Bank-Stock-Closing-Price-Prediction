# Yes-Bank-Stock-Closing-Price-Prediction
![image](https://user-images.githubusercontent.com/94978014/170011519-b67651d3-30a2-4783-a541-7376e6ecc162.png)
# INTRODUCTION:
Stock market is characterized as dynamic, unpredictable and non-linear in nature. Predicting stock prices is a challenging task as it depends on various factors including but not limited to political conditions, global economy, company’s financial reports and performance etc. Thus, to maximize the profit and minimize the losses, techniques to predict values of the stock in advance by analyzing the trend over the last few years, could prove to be highly useful for making stock market movements. Traditionally, two main approaches have been proposed for predicting the stock price of an organization. Technical analysis method uses historical prices of stocks like closing and opening price, volume traded, adjacent close values etc. of the stock for predicting the future price of the stock. The second type of analysis is qualitative, which is performed on the basis of external factors like company profile, market situation, political and economic factors, textual information in the form of financial news articles, social media and even blogs by economic analysts [3]. Nowadays, advanced intelligent techniques based on either technical or fundamental analysis are used for predicting stock prices. Particularly, for stock market analysis, the data size is huge and also non-linear. To deal with this variety of data an efficient model is needed that can identify the hidden patterns and complex relations in this large data set. Machine learning techniques in this area have proved to improve efficiencies by 60-80 percent as compared to the past methods.

# OBJECTIVE:
Yes Bank is a well-known bank in the Indian financial domain. Since 2018, it has been in the news because of the fraud case involving Rana Kapoor. Owing to this fact, it was interesting to see how that impacted the stock prices of the company and whether Time series models or any other predictive models can do justice to such situations. This dataset has monthly stock prices of the bank since its inception and includes closing, starting, highest, and lowest stock prices of every month. The main objective is to predict the stock’s closing price of the month.

# Data Summary:
The dataset of YES BANK has monthly stock prices of the bank since its inception and includes closing, starting, highest, and lowest stock prices of every month of around 180 observations. It contains the following features:

* Date: It denotes date of investment done (in our case we have month and year).

* Open: Open means the price at which a stock started trading when the opening bell rang.

* High: High refer to the maximum prices in a given time period.

* Low: Low refer to the minimum prices in a given time period.

* Close: Close refers to the price of an individual stock when the stock exchange closed for the day.

# Data Visualization
**Distribution Of Features:** Plotted histogram to see the distribution of the data.

![image](https://user-images.githubusercontent.com/94978014/170012217-735b8968-1b20-4d65-a34f-311fad6c8d95.png)


It can be observed that in the starting of the month the stock prices are high but after the fraud incident happened the stock prices gradually decreased.

**Analysis of target variable:**

![image](https://user-images.githubusercontent.com/94978014/170012359-5aff06e1-92a2-4c63-a4da-379aa345542d.png)


**Correlation between the variables:**

![image](https://user-images.githubusercontent.com/94978014/170012463-7819c56e-fd00-4049-bde7-ae5fa5bb5a02.png)


Here, all variables show the highest correlation among them.

# Model building, Predictions and Forecasting
# 1) Regression Approach:
The 4 regression models build for the data are:

* Linear Regression: The most basic machine learning algorithm that can be implemented on this data is linear regression. The linear regression model returns an equation that determines the relationship between the independent variables and the dependent variable.

* Random Forest: It is a supervised learning algorithm that uses ensemble learning methods for regression. Ensemble learning method is a technique that combines predictions from multiple machine learning algorithms to make a more accurate prediction than a single model.

* XGboost: XGBoost stands for “Extreme Gradient Boosting”. XGBoost is an optimized distributed gradient boosting library designed to be highly efficient, flexible and portable. It implements Machine Learning algorithms under the Gradient Boosting framework. It provides a parallel tree boosting to solve many data science problems in a fast and accurate way.

* k-Nearest Neighbours: Another interesting ML algorithm that one can use here is kNN (k nearest neighbours). Based on the independent variables, kNN finds the similarity between new data points and old data points.

#Combining all regression models:
![image](https://user-images.githubusercontent.com/94978014/170012784-3ec95857-ec31-43bd-81f3-1bff2c263b59.png)


Observation from above table:

* Linear Regression gives the lowest MAE, MSE, RMSE, MAPE.
* Here, we can say that Linear Regression is the best model that can be used for the stock price prediction.
# 2) Time Series Approach:
**(i) Auto-ARIMA:** Auto-ARIMA uses brute force and tries different combinations of p, q, and d and then returns the best model after evaluation. It uses mean squared error to evaluate the best model. It also uses Akaike Information Criteria (AIC) and Bayesian information criterion (BIC) which are statistical measures of goodness of fit and the simplicity of the model.

Automatically discover the optimal order for an ARIMA model.

The auto_arima function seeks to identify the most optimal parameters for an ARIMA model, and returns a fitted ARIMA model.

The auro_arima function works by conducting differencing tests (i.e., Kwiatkowski–Phillips–Schmidt–Shin, Augmented Dickey-Fuller or Phillips–Perron) to determine the order of differencing, d, and then fitting models within ranges of defined start_p, max_p, start_q, max_q ranges.

If the seasonal optional is enabled, auto_arima also seeks to identify the optimal P and Q hyper- parameters after conducting the Canova-Hansen to determine the optimal order of seasonal differencing D.

Split data into train and test :

![image](https://user-images.githubusercontent.com/94978014/170013118-46868d13-0bf0-48e3-94e3-9c9ccbb3b0b8.png)


Here, we've used Auto ARIMA to get the best parameters without even plotting ACF and PACF graphs.

![image](https://user-images.githubusercontent.com/94978014/170013330-a06ba5b5-4b89-44cd-b535-edeeb802c3ce.png)


The Auto-ARIMA model provided the value of p, d, and q as 2,0 and 1 respectively.

Residual plots from Auto-ARIMA:

![image](https://user-images.githubusercontent.com/94978014/170013620-de2f9218-5d29-42ad-9410-02952875f3c5.png)


Here,

* Top left: The residual errors seem to fluctuate around a mean of zero and have a uniform variance.
* Top Right: The density plot suggest normal distribution with mean zero.
* Bottom left: All the dots should fall perfectly in line with the red line. Any significant deviations would imply the distribution is skewed.
* Bottom Right: The Correlogram, aka, ACF plot shows the residual errors are not auto-correlated.
Overall, it seems to be a good fit. Let’s start forecasting the stock prices. Now building ARIMA model with provided optimal parameters p(2), d(0) and q(1):

![image](https://user-images.githubusercontent.com/94978014/170014067-bb34a117-f9d7-4875-8a37-4706dd4dbb49.png)


**Forecasting the auto ARIMA model:**

![image](https://user-images.githubusercontent.com/94978014/170014375-252a978c-0818-490c-b2e3-27997ca9a226.png)


An auto-ARIMA model uses past data to understand the pattern in the time series. Using these values, the model captured a decreasing trend in the series.

**Performance metrics for auto-Arima:**

![image](https://user-images.githubusercontent.com/94978014/170014732-6746ed8b-1272-4cb1-bb0a-c94233a5841f.png)


* Around 25.5% MAPE implies the model is about 74.5% accurate in predicting the test set observations.
* Also evident from the plot, the model has captured a trend in the series, but does not focus on the seasonal part. In the next section, we will implement a time series model that takes both trend and seasonality of a series into account i.e. fbprophet.
# (ii) Fbprophet:
Prophet, or “Facebook Prophet,” is an open-source library for univariate (one variable) time series forecasting developed by Facebook. FBProphet uses time as a regressor and tries to fit several linear and nonlinear functions of time as components. By default, FBProphet will fit the data using a linear model but it can be changed to the nonlinear model (logistics growth) from its arguments.

* Prophet is Facebook's library for time series forecasting.
* Prophet follows the sklearn model API.
* Here, we create an instance of the Prophet class and then call its fit and predict methods.
* The input to Prophet is always a dataframe with two columns: 'ds' and 'y'
* The ds (datestamp) column should be of a format expected by Pandas, ideally YYYY-MM-DD for a date or YYYY-MM-DD HH:MM:SS for a timestamp. The y column must be numeric, and represents the measurement we wish to forecast.
# Forecasting model predictions:

Now, we plot the forecast by calling the Prophet.plot method and passing in our forecast dataframe.

![image](https://user-images.githubusercontent.com/94978014/170016039-44f63a9f-fe59-4bd1-8cd7-15fb703bde57.png)


From the above plot we can see that there is an increase in trend in the year 2024 and 2025 onwards.

Now, Plotting prediction components of our model to see the trend, yearly seasonality, and weekly seasonality of the time series.

![image](https://user-images.githubusercontent.com/94978014/170016280-4ec9da46-8af7-4af4-a1b2-b9263201a544.png)


# Observed Trends:

* YES BANK's stock price is showing signs of upper trend yearly.
* YES BANK's stock price shows upper trend signs during February and in December month it tends to give low stock prices.
* YES BANK's stock price is showing signs of upper trend during the end of the month.
**Cross Validation for time series:**

Prophet includes functionality for time series cross validation to measure forecast error using historical data. This is done by selecting cutoff points in the history, and for each of them fitting the model using data only up to that cutoff point. We can then compare the forecasted values to the actual values.

* Parameters used:(model, horizon="365 days", period='180 days', initial='1095 days')
Where,

* model: Prophet class object. Fitted Prophet model.
* horizon: string with pd.Timedelta compatible style, e.g., '5 days', '3 hours', '10 seconds'.
* period(spacing between cutoff dates) : string with pd.Timedelta compatible style. Simulated forecasts will be done at every period. If not provided, 0.5 * horizon is used.
* initial( the size of the initial training period) : string with pd.Timedelta compatible style. The first training period will include at least this much data. If not provided, 3 * horizon is used.
* Here, the output of cross_validation is a dataframe with the true values y and the out-of-sample forecast values yhat, at each simulated forecast date and for each cutoff date.
**Evaluation Metrics:**

Used the performance_metrics utility to compute the Mean Squared Error(MSE), Root Mean Squared Error(RMSE),Mean Absolute Error(MAE), Mean Absolute Percentage Error(MAPE) and the coverage of the the yhat_lower and yhat_upper estimates.

![image](https://user-images.githubusercontent.com/94978014/170017462-bf8c2654-5bc4-45bd-b877-f4dce54717c0.png)


**Plotting Metrics:**
**Mean Absolute Error (MAE)**

![image](https://user-images.githubusercontent.com/94978014/170017724-28d5284e-fa8e-479d-ac62-61811f5ce7be.png)


**Root Mean Square Error (RMSE)**

![image](https://user-images.githubusercontent.com/94978014/170017841-085b8c0a-5849-4899-9e32-4bf72d49862e.png)


**Mean Absolute Percentage Error (MAPE)**

![image](https://user-images.githubusercontent.com/94978014/170017887-84ecb83c-5e02-495a-b4ed-bc0be484c9f0.png)


Here as shown for MAPE(Mean Absolute Percentage Error). Dots show the absolute percent error for each prediction in df_cv. The blue line shows the MAPE, where the mean is taken over a rolling window of the dots.

We see for this forecast that errors around 3% are typical for predictions one month into the future, and that errors increase up to around 18-19% for predictions that are a year out.

# CHALLENGES:
* Because of the small dataset it’s difficult to get good model accuracy.
* Making the data stationary for time series models.
* Adding a monthly trend to fbprophet was a difficult task.
# CONCLUSION:
* There is an increase in trend of Yes Bank stock price till 2018 and then a sudden decrease.
* Using a regression approach we get the best performing model as Linear Regression model with accuracy of 94.60% which is excellent.
* On the other hand, using the time series approach for the FBprophet forecast the error of 3% is typical for predictions one month into the future, and that errors increase up to around 18-19% for predictions that are a year out.
* Fbprophet is the best performing time series model in terms of accuracy.
* February is the month where there are more upward trends for the stock.
* July also shows the upward trend but not as much as February.
* November and December are months with the most downward pressure.
* On a yearly basis there is a decrease in trend from 2021 to 2024 then an increase in trend from 2024 onwards.
