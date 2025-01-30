# Time Series Decomposition

## Transformation and Adjustments
For decomposition, it is useful to first do adjustments and transformations, because it can 
simplify the decomposition, can remove known source of variation, can make patterns more consistent, simple patterns 
are usually more easy to forecast. 

Examples: 

- Population adjustments $\to$ consider the per capita value instead of absolute value
- Inflation adjustments $\to$ consider inflation
- Calendar adjustments $\to$ e.g. changes due to different lengths of months

**Transformations**:  
If data shows variation that increases or decreases with different levels of the series, then use a transformation.

**Log transformation**  
$log(y_t) = w_t$

Useful for: changes in log value are relative (percent) changes in original scale, but only possible if 
original scale is **not zero** or **non-negative**


**Power transformations** 
$w_t = y_t^p$, e.g. $w_t = \sqrt{y_t}$

not so interpretable

**Box-Cox transformation**
(formula see slides)

Characteristics: 

- if $\lambda = 0$, then natural logarithm is used, else a power transformation is used.
- if $\lambda =1$, power transformation but does not change shape
- good $\lambda$ = which makes the size of the seasonal variation about the same across the whole series

## Time series components
**Additive:** $y_t = S_t + T_t + R_t$
**Multiplicative:** $y_t = S_t \times T_t \times R_t$

When to use: 

- Additive: magnitude of seasonal fluctations, variation around trend-cycle, **not** variy with level of time-series
- Multiplicative: variation in seasonal patterns, variation around trend-cycle, proportional to level of time series

```r
series %>% model(stl = STL(Employed)) %>% components() %>% autoplot()
```

<img src="/images/stl.png" alt="Time Plot" height="auto">

**Seasonaly adjusted data**

- useful when interested in non-seasonsal variation (e.g. economic reasons)
- **but** trend-cycle alone more useful because it also contains $R_t$

## Classical decomposition

### Moving averages
First step in classical decomposition

**Mooving average smoothing**  
Eliminates some randomness, (formula see slides)

**uneven m-MA**: m-MA, e.g. 5-MA with $m = 2k +1$, therefore, usually uneven  
**even m-MA**: would not be symmetric, therefore, moving averages of moving averages: $4 \times 2$-MA

**Weighted moving averages**
Use $2\times m$-MAs depending on pattern (e.g. quarterly, yearly) to smooth over seasonal patterns. 


**Classical decomposition**

Problems: 

- not robust to unusual events
- estimate of trend-cycle not available for first few and last few observations
- assumes seasonal components repeats year over year
- over-smoothing

## Methods used by official statistics offices
Mostly used

- X-11
- SEATS
- combination of both

Specifically designed for quarterly and monthly data.


**X-11 Method**

- trend-cycle available for all data
- seasonal component allowed to vary slowly over time
- more robust



## STL decomposition

Advantages: 

- can handle and type of seasonality
- user can specify rate of change in seasonal component AND smoothness of trend cycle
- robust