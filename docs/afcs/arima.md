# Chapter 9 - ARIMA models

## Stationarity and differencing


Stationary: distribution of $s$ does not depend on $t$

often: 

- rouhgly horizontal -> no trend
- constant variance
- no patterns -> no seasonality


- Economic much more often non-stationarity because trend and cycnles
- econological data much more often stationary


if non-stationary data -> needs to make stationary before ARIMA, so

- stabilize variance
- for ARIMA also stabilize mean (differencing)

Process for ARIMA: make data stationary, build model, reverse everything, generate forecasts

making data stationary = differencing  
reversing stationary = integrating

How to tell if non-stationary?

- time plot
- *stationary*: ACF drops to zero quickly 
- *non-stationary* ACF slowly decreaeses
- *non-stationary* $r_1$ often large and positive


Differenced series $T-1$ values, first is $t_2$

Sometimes second order difference needed to make it stationary ($T-2$ values) first is $t_3$. In practice almost never
beyond second order difference.

**Sesonal differenced data**  
$m=$ sesonal pattern, so values are $T-m$ values

Important that **interpretable** if 12 months sesonal data, 3 months lag does not make sense

Example: first seasonal differencing 12 + then differencing 1
Does not make a difference which order; but recommend always do seasonal first


**Random walk model**  

- white noise always implies stationarity
- stationarity does not imply white noise

Model:  
$y_t = y_{t-1} + \epsilon_t$ with $\epsilon-t \sim NID(0, \sigma^2)$

Expected value $t+1$ is always $y_t$

Random walks typically: 

- long periods of trends up or down 
- sudden changes, therefore, hard to predict (stochastic trend)
- forecasts are equal to last observation (naive), future movements up or down are equally likely


*Random walk drift model*: differenced series is white noise with non-zero mean (model behing drift method)

*Seasonal random walk*: model behind seasonal naive method


**Unit root tests**  
Tests for stationarity

- ADF test -> $H_0$: non-stationary -> for econometric modelling (or inference) preferred test because interested in controlling for *Type 1* error
- KPSS test -> $H_0$: stationary -> used in forecasting (don't want to difference unless evidence of non-stationary)


so for KPSS: small p-value -> reject $H_0$, so data non-stationary


Seasonal test don't work really well  
Therefore, seasonal strength $F_S$ see formula -> value 0.64 after experience to do seasonal difference


## Backshift notation
Letter $B$ before $y_t$ then just shifted one time

For 12 month backshift $B^12 y_t$

For differencing: $(1-B)y_t$ for one difference, second order differencing $(1-B)^2 y_t$  
In general $(1-B)^d y_t$

Or combine seasonal and first difference by $(1-B)(1-B^m) y_t$


## Autoregressive models
Regression on lagged values of predictor (therefore autoregressive)

Example AR(1) $y_t=-0.8y_{t-1} + \epsilon_t$:  
Oscilates, because negative weight

$\vert \phi_1 \vert < 1$ then stationary

- $\phi_1 = 0$ and $c=0$ then WN
- $\phi_1=1$  and $c=1$ then RW
- $\phi_1=1$ and $c\neq 0$ then RW with drift

Constant and mean: 
$\mu = \frac{c}{1-\phi_1}$

**AR(2)**  
We get cyclic behaviour

Normally constrict AR models for stationary data, leads to parameters contstraints

- for $p=1$, $-1 < \phi_1 < 1$
- for $p=2$, $-1 < \phi_2 < 1$, $\phi_2 + \phi_1 < 1$, $\phi_2 - \phi_1 < 1$


## Moving average models
Regression on "past errors"

$\neq$ moving average smoothing

**MA(1)**  
wanders around, not like white noise, but still noisy

**MA(2)**  
Looks like oscilating


Any AR() model can be written as a MA($\infty$) model (given $-1 < \phi_1 < 1$)

And also any MA(q) can be written as AR($\infty$)

--> invertability constraints (same as forecating constraints for ETS model)

- for $q=1$, $-1 < \theta_1< 1$
- for $q=2$, $-1 < \theta_2 < 1$, $\theta_2 + \theta_1 < 1$, $\theta_2 - \theta_1 < 1$


## Non-seasonal ARIMA models
No nice interpretability in trend, seasonality, etc. like ETS

- predictors include lagged values of $y_t$ and lagged errors
- conditions AR ensure stationarity
- conditions on MA ensure invertiblity

Without differencing, ARMA model

Special models: 

- ARIMA(0,0,0) white noise, because $y_t=\epsilon_t$
- ARIMA (0,1,0) with not constant: RW
- ARIMA (0,1,0) with constant: RW with drift
- ARIMA(p,0,0): AR(p)
- ARIMA(0,0,q): MA(q)


Backshift notation, e.g. ARIMA(1,1,1):  
$(1-\phi_1 B)(1-B)y_t = c + (1+\theta_1 B) \epsilon_t$

Intercept form vs. mean form

Cyclic behaviour with $p>=2$, ETS models can't handle cyclic behaviour (only sesonality); ARIMA can do both


**Features of models:**  

For *long-term forecasts:* 
- if constant $c$ included
- and differencing 

p and q only affect short-term forecasts

- $c=0$, $d=0$, then long-term fc goes to zero
- $c=0$, $d=1$, then long-term fc goes to non-zero constant
- $c=0$, $d=2$, then long-term fc straight line
- $c\neq 0$, $d=0$, then long-term fc got o mean of data
- $c\neq 0$, $d=1$, then long-term fc straight line
- $c\neq 0$, $d=2$, then long-term fc follow quadratic trend

The bigger $d$, more rapidly prediction intervals increase in size  
If $d=0$, std of long-term fc will be same as historical std

**Cyclic forecasts**  

- p at least 2
- plus additional constraints


**Partial autocorrelations**  
Measure relationship between $y_t$ and $y_{t-k}$ without effects of intermediate lags  
--> regression on $k$th $y$ $= \alpha_k$

when $k=1$, $\alpha_1 = \rho_1$

One way to find $p$ in a AR() model is to look at the last significant lag:
-> PCAF then look at last significant spike  
but works only, if pure AR model


ACF of seasonal and cyclic data: sinuosidial

ONLY FOR PURE:
AR(1):

- ACF expontential decay
- PACF one significant spike and then nothing

AR(p):

- ACF expontential decay OR damped sine-wave pattern
- PACF last significant spike at p

MA(q):

- PACF expontential decay
- ACF one significant spike and then nothing

MA(q):

- PACF expontential decay OR damped sine-wave pattern
- ACF last significant spike at q


---> not suitable for mixed models


## Estimation and order selection
Maximum liklehood estimation (non-linear optimization) -> conditional 

How to choose model?  

- AIC criteria
- Corrected aIC
- Bayesian Information Criterion

Preference on AICc

Portmanteau test for ARIMA: 

- Use $l-K$ degrees of freedom with $K=p+q$
- dof = K

If p large, then white noise


## Forecasting

Steps: 

- rearrange ARIMA equation, so $y_t$ on LHS
- rewrite $t$ by $T+h$
- on RHS replace future observations by forecasts

iterate with h=1, ... 

**Prediction interval** 

- h=1, always $\hat \sigma^2$
- for all MA(q) models, its easy
- for all other models, complex


Features of prediction intervals:

- increase in size with fc horizon, if $d=0$ flatten out; if $d>0$ increase forever
- can be difficult to calculate by hand
- assume resid uncorrelated and normally distributed
- prediction intervals tend to be too narrow

## Seasonal ARIMA models

Guess model parameters: same as non-seasonal ARIMA, but only look at spikes that are multiples of $m$ seasonal pattern


- two differencing leads to trend
- only models with same level of differencing can be compared
- RMSE on test set can involve different levels of differencing

## ARIMA vs. ETS






