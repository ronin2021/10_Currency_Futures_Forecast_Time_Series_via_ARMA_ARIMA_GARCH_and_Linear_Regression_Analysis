# 10_Currency_Futures_Forecast_Time_Series_via_ARMA_ARIMA_GARCH_and_Linear_Regression_Analysis
Forecasting Currency Futures via ARMA, ARIMA, GARCH and Linear Regression Analysis 

# Forecasting US$ to Japanese Yen Futures via ARMA, ARIMA, GARCH, and Linear Regression Analysis

### Outline

Analysis, model fit, and forcast of Japanese Yen Futures against US$ using Hodrick Prescot Filter, ARMA, ARIMA, and GARCH models and a linear regression analysis.   

#### Part 1. Model Fitting and Forecasting
Currency Futures of Japanese Yen vs. US$ historical data were given in CSV format. Data were uploaded after ETL to a Panda dataframe having Date (index), Open, High, Low, Last, Change, Settle, Volume, and Previous Day Open Interest. Data were filtered using Hodrick-Prescott Filter and graphically analyzed for trend vs. noise of the Settle price of the futures. 

Using data from the dataframe, Return, and Lagged Return data were added as new columns. 

Data were truncated to make dataframe represent only the data after 01-01-1990. These data devided to train (1991-2018) and test (2018-2019) sets. These then fed into the ARMA, ARIMA, and GARCH models. Which resulted in subsequent assessment of fits. From these models 5 day forecasts were generated. The models and forecasts were then assessed from their p values, AIC = Akaike Information Criterion, BIC = Bayesian Information Criterion, HQIC = Hannan-Quinn Information Criterion. From the forecasts the risk and whether is meaningful to buy futures or not was assessed. Models were also compared and considered for reparametrization to improve them or not.  

#### Part 2. Linear Regression Analysis
Linear Regression analysis was carried on the same dataframe derived from the same futures data. Data was split between train (1991-2018) and test (2018-2019) data. 
Returns were plotted with predictions to see how they correlate. In samle and out of sample Root Mean Square Error (RMSE) were calculated and commented on.

### Inputs
Data were read from yen.csv for the analysis. 

### Outputs
Outputs are given out as mentioned above on the terminal as calculated values, visual plots/graphs/figures, and explanations about the results. 

### Remarks
The process should be iteratively improved particularly for the ARMA and ARIMA models (preferably by changing p, q, and d for each fit appropriately while keeping 
the parsimony in mind i.e., higher orders would be adverse for the fit quality). 

#### Comments on Results: 
In implementing ARMA model all of the p values are significantly larger that 0.05. Therefore within the 95% confidence level this fit is a not a good fit. Thus the projected ARMA forecast is also not as good as expected with in the 95% confidence level.  

In implementing ARIMA model all of the p values are significantly larger than 0.05. Therefore within the 95% confidence level this fit is a not a good fit. Thus the projected ARIMA forecast is also not as good as expected with in the 95% confidence level.

In implementing GARCH model except one (alpha[2]) ALL of the p values are smaller than 0.05. Therefore within 95% confidence level this fit is a relatively better than than the ARMA and ARIMA fits to the data set. Thus the projected GARCH (Genereralized Auto Regressive Conditional Heteroskedasticity) forecast is marginally better than what was obtained under ARMA and ARMIA forcasts with in the 95% confidence level.

Based on your time series analysis, suggestions to buy or not buy yen now?

* It is not prudent to buy yen now as per dollar yen amount is projected to go up. This means yen will be cheaper (can buy more yen per doller in the future) in the forecast. However if this firm is selling goods in Japan and is supposed to get paid in Yen in the future it is best to buy a futures contract under current terms so when Yen devalues against dollar the firm can get dollar amount under current terms. That is it can hedge against loosing its revenue due to the weakening of the Yen agaist the dollar. 

Is the risk of the yen expected to increase or decrease?

* ARMA model predicts risk to decrease in the 5-day forecast while the ARIMA and GARCH (the best possible fit from the statistical parameters) predict increased volatility. Since the data is non-stationary ARIMA and GARCH are better models. However the the futures settle values are are somewhat converted to stationary by calculating returns when put into ARMA. From the parameters (p values, AIC = Akaike Information Criterion, BIC = Bayesian Information Criterion, HQIC = Hannan-Quinn Information Criterion) having the lowest value, the best fit is the GARCH. Thus it is possible to consider that the risk to increase as the forecast days increase.   

Based on the model evaluation, would you feel confident in using these models for trading?

* p values of the models to fall within the 95% confidence level must be at or below 0.05 while the AIC, BIC and HQIC must be low relative to p, q, and d values giving different iterations of those models. These models particulalry ARMA and ARIMA needs to be recalibrated with p, q, and d (for ARIMA only) to get better fits. As they stand it is hard to depend on the forecast values from ARMA and ARIMA. Considering the p values: the best p values are for GARCH while the worst p values are for ARIMA. Considering the AIC and BIC the lowest values are for GARCH model and this reinforces that the Garch model is comparatively the best model. However, GARCH modelals has Alpha[2] = 1.000 which is significantly higher than 0.05. In summary, of the three models best is the GARCH while it is still adivisable to vary p and q (as opposed p=2 and q=1) to see if it is possible to make it better. For the ARMA and ARIMA a survey of p, q, and d are a must to get the p, AIC, BIC and HQIC to more acceptable values.    
