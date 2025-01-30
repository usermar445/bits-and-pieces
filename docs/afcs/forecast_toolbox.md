# Forecaster's Toolbox

## Simple Forecasting Methods

**Mean method**  
forecast = mean of historical data

<img src="/images/mean_method.png" alt="Time Plot" height="auto">


**Naive method**  
forecast = level of last observation

<img src="/images/naive_method.png" alt="Time Plot" height="auto">


**Seasonal naive method** 
forecast = last seasonal pattern
<img src="/images/naive_seasonal_method.png" alt="Time Plot" height="auto">


**Drift method** 
forecast = first and last point of observation interpolation
<img src="/images/drift_method.png" alt="Time Plot" height="auto">

## Residual Diagnostics
**Fitted values**: $\hat y_{t\vert t-1}$  
**Residuals**: $e_t = y_t - \hat y_t$
**Innovation residuals (transformed residuals)**: $ w_t - \hat w_t$

**Necessary properties** of good forecasts: 

- residuals uncorrelated
- residuals have zero mean (otherwise biased forecast)

**Useful properties** of good forecasts: 

- residuals constant variance
- residuals normally distributed


**How to determine?**
<img src="/images/resid_time.png" alt="Time Plot" height="auto">
<img src="/images/resid_hist.png" alt="Time Plot" height="auto">
<img src="/images/resid_acf.png" alt="Time Plot" height="auto">


**Portmanteau test for autocorrelation**
Residuals should look like white noise

The larger the lag value (the more lags there are), the more liklier a false positive occurs, therefore, test of how 
likely a white noise would generate this. 

Other tests: **Box-Pierce Test** or **Ljung-Box Test**


## Forecast Distribution & Prediction Intervals

Most classical models produce normally distributed forecast interval. 

Prediction intervals which mean is the point estimate.

**One-step prediction interval**: estimate std from residuals  
**Multi-step prediction interval**: prediction interval usually gets larger with number of steps


**Transformation**  

- first produce forecast of transformed data
- then reverse transformation

But back transformed data the point estimate usually not mean (but median)


## Evaluating Forecast Accuracy

**Training and test set**  

- attention over-fitting

**point forecast error vs. residuals**: residuals calculated on training set, forecast error on test set; residuals only 
one-step forecast whereas error multi-step

**Comparing errors** 

- MAE (scale dependent), forecast median
- RMSE (scale dependent), forecast mean
- MAPE (percentage error), scale independent; however, only when $y_t$ strictly greater than 0, no meaningful 0, heavily penalising negative errors
- sMAPE (symmetric MAPE), but possibility of having negative error and values closer to 0
- MASE
- RMSSE

**Distributional forecast accuracy**

**Corss-validation**



