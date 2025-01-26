# Choosing and defining metrics

## Metric definition
Two use cases: 

- invariant checking, should not change 
- evaluation: overall business metrics + more detailed metrics


Just one metric or multiple? Depends on company/business decision. 

You can also use OEC: Overall-evaluation criterion, a composite metric.

**Approach:** 

Choose high-level metrics first (based on e.g. funnel), then refine metrics.

**Difficult metrics:**

- no access to data
- takes to long measure

**Additional techniques to generate ideas:**

- External Data, surveys, etc..

## Filtering and Segmenting 
Build  intuition which traffic to be filtered out. Sometimes easier to segment (e.g. by country) and then compare
to understand if differences are occur and can be explained.

**Useful technique**

- week over week plot or
- year over year plot

To see if e.g. a spike is persistent.

Also compare by segmented by country.


## Summarizing metric
There are alot of different metrics (if metric is numerical): mean, median, 25th percentile, 90th percentile, etc.

**How to choose?**

- sensitivity and robustness: metric needs to be sensitive enough to detect change, but doesn't move when you don't want to
- distribution: how does distribution of metric look like? with retrospective analysis, i.e. histogram

Distribution: if "normal shape", mean or median is going to make sense; if more one-sided then maybe percentile

**Categories**

- sums and counts
- distributional metrics
- probabilities and rates
- ratios

## Robustness and sensitivity
Metric should be sensitive enough that it moves when you want to but robust enough that it doesn't move when you don't want to.

**Example**  
Mean is sensitive to outliers. Median on the other hand might be too robust. 

**How to measure**

- run experiments: A/A experiments to check if it is too sensitive, past experiments
- retrospective analysis

## Variability
Depending on variability and practical significance level you want, an experiment might not be feasible. 
Thats why variability matters. 

**Confidence interval you need:**

- Variance (or standard deviation)
- Distribution

**Types of metrics**

| metric              | distribution                 | SE               |
|---------------------|------------------------------|------------------|
| probability         | binomial and SE normal       | formula          |
| mean                | CL: normal (if large enough) | formula          |
| median / percentile | depends on underlying data   | depends          |
| count / difference  | often normal                 | Var (x) + Var(y) |
| rates               | often poisson                | mean             |
| ratios              | depends                      | depends          |


**Nonparametric Methods and empirical variance**  
If there is no standard distribution available, then you can do two things:

- first, estimate empirical variance
- second, then a) either estimate normal distributed confidence interval with empirical variability (if data looks "normal" enough) or b) estimate nonparametric confidence interval


At Google, even for simple metrics, the analytics estimate was an underestimate. Therefore, they started **A/A testing** everything. 
Any difference you measure in these tests, are due to the underlying variability (maybe because of the system, user population, behaviour, etc.). 
If you for example too much variability in an A/A test, then the metric is probably too sensitive to be useful. 


**How many A/A tests?**  
If possible, many. But keep in mind: standard deviation dependent on square root of sample size. Otherwise: use **boostrapping**. 


**How to estimate confidence interval empirically**  
a) either with a normal distribution  
or  
b) choose confidence interval that contains e.g. 95% of the values directly in the data. 

**Boostrapping**  
Run one big experiment, and then take sample (randomly) and treat it as if it were a full experimental group. Repeat this process over and over. 

## Summary

Pay attention to:

- measurement issues: common definition of metrics are important
- robustness: if metric doesn't move at all, maybe not that useful
- speak to engineers
- Variability: start analytically, then do it empirically
- necessity of invariants


