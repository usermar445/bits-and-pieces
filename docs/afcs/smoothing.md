# Chapter 8 - Exponential Smoothing

## Simple Exponential Smoothing
In between naive method (last observation) and average method (average of whole time series) $\to$ weighted average, 
with more recent observations more weight. 

$\alpha =$ smoothing parameter ($0 \leq \alpha \leq 1$), with

- $\alpha$ close to 0, more weight on distant past
- $\alpha$ close to 1, more weight on recent past
- $\alpha=1$ equal to naive method

**Weighted average form**  
Forecast $T+1$ equal to weighted average of most recent observation and previous forecast. Derive form. 

**Component form**  
(??)

$h=1$ gives fitted values  
$t=T$ gives true forecast

**Flat forecasts**
(?)

**Optimisation**  
Need to select smoothing parameter $\alpha$ and intial values $l_0$ to be chosen. 

Can be chosen from experience, but more reliable: estimate from data. 

Same here: minimising SSE (but non-linear minimsation)

## Methods with trend
**Holt's linear trend model**  
Involves forecast equation and two smoothing equations (one for level and one for trend).

Forecast function linear function of $h$, i.e. last estimated level plut $h$ times the last estimated trend. 

**Damped trend methods**  
Holt's method assumes linear trend for infinity. Tends to over-forecast, therefore, dampen forecast for long horizons.

$\phi$ dampend parameter: 

- $\phi = 1$ same as linear forecast
- in practice $\phi$ rarely less than 0.8 and max. 0.98
- short-run forecasts are trended, long-run forecasts are constant

**Comparing**  
Check MAE or RMSE. 

## Methods with seasonality
Extended model with three smoothing equations: level $l_t$, trend $b_t$, and seasonal component $s_t$, with parameters
$\alpha$, $\beta^*$, and $\gamma$ and $m$ number of periods. 

Two versions for seasonal component

- additive: when seasonal variation roughly constant
- multiplicative: when seasonal variations changing proportional to level of series

**Holt-Winter's additive method**  
Weighted average of sasonally adjusted observation and non-seasonal forecast. 

$k$ is integer part of $(h-1)/m$, ensures estimates of seasonal indices used come from final year of sample

Trend identical to Holt's linear method

**Holt-Winders' multiplicative method**  
parameter $\gamma$ (?)

Both methods have same parameters, therefore, RMSE can be used. 

Small value for $\gamma \to$ seasonal component hardly changes over time

Small value for $\beta^* \to$ trend component hardly changes over time


**Holt-Winders' damped method**  
Often accurate and robust forecasts: damped trend + multiplicative seasonality

## Taxonomy of exponential smoothing methods
9 possible methods, given by $(T, S)$ with $T \in {N, A, A_d}$ (None, Additive, Additive damped) and $S \in {N, A, M}$ 
(None, Additive, Multiplicative).

## Innovations state space models
Exponential smoothing generate point forecasts, statistical methods prediction intervals (distributions). Stochastic 
model consists of

- measurement equation: describes observed data
- state equations: describes unobserved components or states (level, trend, seasonal)

Always two types: additive + mutliplicative errors; if same parameters = same point forecasts but differernt prediction
intervals. 


**ETS(A, N, N): simple exponential smoothing with additive errors**  
Rewrite simple exponential smoothing equation (level equation) to get *error correction form* with $e_t$ as residual 
at time $t$. 

Negative error at time $t$ means level at time $t-1$ has been over-estimated. Parameter $\alhpa$ decides how "rough" the
adjustment of the level will be.

$y_t = l_{t-1} + e_t$

Assumption: $e_t \sim NID(0, \sigma^2)$ (normally and independelty distributed. )

Smoothing parameter $\alpha =$ how smooth changes are

- $\alpha = 1$ random walk
- $\alpha =0$ level of series does not change over time

**ETS(M, N, N): simple exponential smoothing with additive errors**  

((More different models))

## Estimating ETS models
For additive model: maximizing liklehood same as minimising least squares (assuming normally distributed errors)

For multiplicative model: different results

Parameter estimation, conventially: 

- $0< \alpha <1$
- $0 < \beta < \alpha$
- $0<\gamma<1-\alpha$
- in practice, $0.8 < \phi <0.98$ 

Restrictions because: limit effect of past observations

Certain models can lead to numerical difficulties (because division my zero; ETS(A, N, M), ETS(A, A, M), ETS(A, $A_d$, M))

## Forecasting with ETS models

**Prediction Intervals**  
Parameters: 

- $c$ coverage probability
- $\sigma_h^2$ forecast variance
















