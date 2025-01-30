# Chapter 10 - Dynamic Regression Models

## Estimation
Error terms of regression model are ARIMA process

if $\eta_t^2$ is estimated using ordinary regression

- estimate coefficients $\hat \beta_0$ ... are no longer optimal (efficient) but still consistent; information is ignored
- if non-stationary autocorrlation, estimates are even non-consistent
- statistical tests are incorrect
- p values for coefficient susually too small
- AIC misleading


Every regression with ARIMA error can be rewritten as regression with ARMA error 

- ARIMA(1,1,1) errors equivalent to ARIMA(1,0,1) errors
- model in levels vs. model in differences


## Regression with ARIMA errors using fable


## Forecasting
Prediction intervals do not take into account the uncertaintiy of exogenous variables

## Stochastic and deterministic trends

Deterministic trend:  
linear function of time, where error is stationary process

Stochastic trend:  
linear function of time, where error is differencing process


Give different prediction intervals (in example: stochastic model larger prediction interval)
 
Stochastic prediction intervals larger

Recommendation: not use deterministic trends for long-term forecasts, because strong assumptions

## Dynamic harmonic regression
Deal with any length type of seasonality also with more than one seasonal period

Disandvantage: cannot change sesonality pattern

usually not used on monthly data

For example on weekly data (not an integer ??)

## Lagged predictors
When change in predictor does not affect target immediately

$\gamma(B) x_t$ is transfer function (backshift notation)













