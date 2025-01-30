# Cheatsheet R

## Useful packages
 * `tibble`, for tibbles, a modern re-imagining of data frames.
 * `dplyr`, for data manipulation.
 * `tidyr`, to easily tidy data using spread() and gather().
 * `lubridate`, for date/times.
 * `ggplot2`, for data visualisation.
 * `tsibble`, for tsibbles, a time series version of a tibble.
 * `tsibbledata`, various time series data sets in the form of tsibbles.
 * `feasts`, for features and statistics of time series.
 * `fable`, for fitting models and producing forecasts.


## tidyverse

`pivot_longer()`


**Facet grid**  

```r
gafa_stock %>%
  ggplot(aes(x=Date, y=Close, group=Symbol)) +
  geom_line(aes(col=Symbol)) +
  facet_grid(Symbol ~ ., scales='free')
```

## tibble

**Create tibble:** `as_tibble()`

```r
mytimeseries <- tute1 %>%
  mutate(Quarter = yearquarter(Quarter)) %>%
  as_tsibble(index = Quarter)
```

## Plotting

`autoplot()`

`gg_season()`

`gg_subseries()`

`gg_lag()`

`ACF()`