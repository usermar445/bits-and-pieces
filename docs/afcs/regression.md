# Chapter 7  - Time Series Regression Models

## The linear model
**Simple linear regression**
Observation consists of:

- systematic/explained part, $\beta_0 + \beta_1 x_1$
- random error $\epsilon_t$

**Interpretation of intercept**  
Requires that $x=0$ makes sense. But even if it does not make sense, should be included.


**Multiple linear regression**   
Assumptions:

- relationship reasonalby linear
- $\epsilon$ zero mean (otherwise biased)
- $\epsilon$ not autocorrelated, i.e. independent of each other (otherwise more information contained)
- $\epsilon$ unrelated to predictor variables, otherwise more information left
- each predictor not a random variable

Useful

- $\epsilon$ normally distributed with contant variance $\sigma^2$

## Least squares estimation
For estimating parameters. 

$p$-value not really of interest for forecasting (why?)


**Fitted values**  
Fitted values are not actual forecasts but used to fit the model.


**Goodness-of-fit**  
= proportion of variation in forecast variable that is explained be the regression model

In simple linear regression, $R^2 = r^2$.

Will always increase with additional predictors $\to$ prone to over-fitting.


**Standard error of the regression**  
= standard deviation of the residuals, i.e. residual standard error

related to size of average error (?)

## Evaluating the regression model
Residuals have useful properties: 

- sum is = 0
- sum of product $x_t \epsilon_t$ = 0

Therefore, zero mean and zero correlation. 

Check assumptions of models:  
**Check ACF plot of residuals**  
Should show no ACF, otherwise, there is still some information left. Therefore, *inefficient* (but unbiased). Leads
to larger prediction intervals than necessary. 

**Histogram of residuals**  
Check if normally distributed $\to$ not necessary, but makes calculation of prediction intervals easier. 
If skewed, makes prediction interval coverage more difficult. 

**Time plot**  
Check homoskedascity (constant variance over time), otherwise, makes prediction interval coverage inaccurate (?).

**Residuals plots against predictors**  
Expect: randomly scattered without any pattern. If so, relationship may be non-linear. 

Also plot against predictors that are **not** in the model, otherwise, add to the model. 

**Residulads plots against fitted values**  
Expect: randomly scattered without any pattern. If so, could be heteroscedasticity (non-constant variance).  
Solution: transformation of forecast variable

**Outliers and influential observations**  
Extreme values = outliers  
large influence on estimated coefficient = influential observations (usually outliers in x direction)

One source: incorrect data entry. But if no error, not wise to remove. 

**Spurious regression**  
Non-stationarity can lead to spurious regression

## Some useful predictors

**Trend**  
Linear trend using $t$

**Dummy variables**  
Multi-cagetories can be modeled with one-hot-encoding. 

Can also be used to account for an **outlier**. 

**Seasonal dummy variables**  
E.g. to account for day of the week. **Important**: only six dummy variables used, because 7th day modeled by 
intercept. Otherwise, *dummy variable trap*. In general, use one less category. 

Interpretation: always compared to baseline.

**Intervention variables**  
E.g. competitor activity, advertising expenditure, etc. 

- *Spike variable*: dummy variable for one period (equivalent to outlier handling)
- *Step variable*: shift, 0 in periods before shifts, 1 after shift
- *change of slope*: piecewise linear trend

**Trading days**  
Days in a month vary, therefore:

- include number of trading days in a month as predictor
- to account for weekdays, number of mondays, number of tuesdays, etc.

**Distribtued lags**  
Often used for advertistin gexpenditure as predicture (which can have a lagged effect after the campaign). 
Include as predictor:

- $x_1$ advertising previous month
- $x_2$ advertising two months previously
- etc.

**Easter**  
Not held on same day every year. Dummy variable for period (month). 

**Fourier series**  
For long seasonal periods, it can be better to use Fourier series (leads to fewer predictors). E.g. weekly data.
For short seasonal periods (e.g. quarterly) little advantage. 

$K$ specifies how many $sin$, $cos$ pairs to include with $K=m/2$ max. $\to$ Usually called harmonic regression.

## Selecting predictors
Bad approaches:

- plot predictor against forecast variable and see if relationship; other predictors not considered, relationship not always detectable
- do multiplie regression with all, drop unsignificant predictors; statistical significance not equal predictive value + correlated predictors

Instead: measure of predictive accuracy

**Audjusted $R^2$**  
$R^2$ only measures test accuracy, not forecast. Plust more predictors result in higher $R^2$.
Same holds for $SSE$. Therefore, $\bar R^2$ which accounts for number of predictors.

Equal to minimising standard error $\hat \sigma_e$.

Tends to err on the side of selecting too many predictors. 

Best model: 

- minimising CV, AIC, AICc, BIC
- maximizing $\bar R^2$


**Cross-validation**  
Leave-one-out cross-validation, $e_t^* ) = y_t - \hat y_t$. Repeat for all $t$, then calculate MSE. 

**AIC**  
Penalizse the fit of the model (SSE) with the number of parameters that need to be estimated. $k+2$ parameters in the 
model, $k$ coefficients for predictors + intercept + variance of residuals.

For large $T$, minimising AIC same as minimising CV value.

**Corrected AIC**  
For small values of $T$, AIC tends to select too many predictors. Therefore, corrected version.

**Schwarz's Baysian Information Criterion**  
Model will be same or fewer terms as AIC. Because penalizes number of parameters more heavily. 

**Recommendation**  
BIC relies on underlying model (?), rarely the case. Therefore, AIC, AICc, CV to be used. If $T$ large enough, should 
lead to the same model. 

**Best subset regression**: if possible, all models should be fitted and best subsets chosen. If too many predictors/models, 
use stepwise regression:

**Stepwise regression**: backwards stepwise regression vs. forward stepwise regression.

But only useful for forecasting, not statistical significance (??).

## Forecasting with regression
Fitted values vs. forecasts

**Types of forecasts** 

- *ex-ante forecasts*: only with information available at the time, genuine forecasts
- *ex-post forecasts*: with later information, to study forecasts models, not genuine (can assume knowledge of $x$ but not $y$)

No difference, e.g. Australian beer production, because special predictors (seasonal dummy variables, public holidays)
all known in advance. 

**Scenario based forecasting**  
Use scenarios for predictors. 

Do not include uncertainty of predictors. 


Problem of regression based forecasting: predictor variables need to be available in the future. Not always the case. 
Therefore, *lagged values* (?).

**Prediction intervals**  
Assume normally distributed regression errors. 

## Nonlinear regression

- log-log transformation $\to$ elasticity (average percentage change in $y$, resulting from a 1% increase in $x$)
- log-linear
- linear-log

In order for log-transoform: all values $>1$, otherwise for zero values use $log(x+1)$.

**Piecewise lienar**  
Introduce *knots*, where slope can change. Special case of *regression splines*.

**Forecasting with a non-linear trend**  
Use $t^2$ or higher. However, not recommended because forecasts unreliable. 

Better: use piecewise linear trend. 

Example: fitting exponential trend = log-linear regression

## Correlation, causation and forecasting
**Correlation is not causation**  
Correlation $\neq$ causation $\to$ confounding. Confounder: both affecting predictor and response variable. 

Confounder makes it more difficult to evaluate causes of change, but not necessarily forecasting. 

Correlation useful for forecasting even if no causality or causality the other way. But often a better model possible
when causality is accounted for. 

**Correlated predictors**  
When predictors correlated, difficult to separate effects.

Not a problem for forecasting per se, but only when scenario based or historical analysis of contributions.

**Mutlicollinearity and forecasting**  
Same information provided by multiple predictors. E.g. when correlated. Will not lead to better forecasts but also not worse.

Also: linear combination of predictors correlate with other linear combination, e.g. dummy variable trap.

Estimation of individual coefficients difficult, i.e. unreliable, same as $t$ tests. Accordingly, forecasts unreliable
when values of predictors outside (?).



## Matrix formulation


