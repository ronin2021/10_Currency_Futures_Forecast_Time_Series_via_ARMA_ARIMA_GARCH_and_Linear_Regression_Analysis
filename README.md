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
