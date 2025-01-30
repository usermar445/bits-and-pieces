# Time Series Graphics

## Time plots
Create "normal" plot of time series

```r
series %>% autoplot()
```

<img src="/images/time_plot.png" alt="Time Plot" height="auto">


## Patterns

Three patterns: 

- **Trend**: long-term increase or decrease in data (does not have to be linear)
- **Seasonal**: when time series is affected by seasonsal factors, e.g. time of the year or day (fixed period)
- **Cyclic**: rises and falls that are not of fixed frequency, e.g. business cycle, (at least 2 years)

## Seasonal plots
Splitted plot over same period of different time periods

```r
series %>%  gg_season(Cost, labels = "both")
```

<img src="/images/season_plot.png" alt="Time Plot" height="auto">

Useful: 

- underlying seasonal pattern can be seen more clearly
- useful for detecting changes in pattern


## Subseries plots
Data for each season in seperate plot

```r
series %>%  gg_subseries(Cost)
```
<img src="/images/subseason_plot.png" alt="Time Plot" height="auto">

Useful

- Detection of underlying seasonal pattern and changes in it

## Scatterplots
Useful to see relationship between two (or more) timeseries to detect possible correlation or relationships.

**Reminder:** Correlation is not causation! (And linear)

## Lag plots
Special kind of scatter plot

```r 
series %>% gg_lag()
```
<img src="/images/lag_plot.png" alt="Time Plot" height="auto">

Each plot shows $y_t$ plotted agains $y_{t-k}$ for different values of $k$.

Useful to detect relationships between lags of same time series. 

## Autocorrelation
Measures the linear relationship between two lags of a time series. 

The different values for $r_t$ can be computed and plotted by
```r
series %>% ACF() %>% autoplot()
```

<img src="/images/acf_plot.png" alt="Time Plot" height="auto">

ACF plots: 

- significance line if significant differently from zero
- when there is a **trend**, small lags tend to be large an positive, because ovservations nearby in time also have similar values (decreasing over time)
- when there is **seasonality**, autocorrelations will be larger for seasonal lags
- combination of both possible

## White noise
Time series with no autocorrelation

Criteria: each autocorrelation close to zero

<img src="/images/white_noise.png" alt="Time Plot" height="auto">


Rule: 

- $95\%$ of spikes within $\pm 2/\sqrt{T}$
- if one or more spikes outside these bounds OR substantially $5\%$ outside, then probably not white noise
