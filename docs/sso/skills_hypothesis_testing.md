# Skills Hypothesis Testing

**Overview**

Basics:

- know three different ways of hypothesis testing

Testing claims about a proportion:

- Testing claims about a proportion (using p-value method) and confidence interval

Testing claims about a mean:

- Testing claims about a mean (using p-value method) and confidence interval


## Basics of hypothesis testing

The general idea:  
Given a certain distribution (from $H_0$), if the probability of getting an "extreme" value (for the test statistic $T$)
is really small, then you reject $H_0$ and accept the alternative hypothesis. 

General procedure: 

- identify $H_0$ and $H_1$
- Calculate test statistics
- Choose relevant sampling distribution
- Use either a $p$-value or the critical value method
- Or: use confidence interval


#### $p$-value method
Calculate $p$-value (probability of test statistic given distribution). If $p$-value $< \alpha$, reject $H_0$, otherwise
do not reject $H_0$.

To find the relevant $p$-value:

- critical region in the *left* tail: area to the *left* of the test statistic
- critical region in the *right* tail: area to the *right* of the test statistic
- critical region in *two* tails: *twice* the area in the tail beyond the test statistic (depends on whether the test statistic is on the left or right from the middle)

#### Critical value method
Find critical value of significance level $\alpha$. If test statistic is within region of critical value, reject $H_0$.
Otherwise, do not reject $H_0$.

#### Confidence interval method
Reject claim that the population parameter has a value that is not included in confidence interval.

Construct confidence interval with:

- *Two-tailed test:* confidence level $1-\alpha$
- *One-tailed test:* confidence level $1-2 \alpha$


#### Overview of different test statistics

| Parameter                           | Sampling Distribution | Requirements                                                                             | Test Statistic                                     |
|-------------------------------------|-----------------------|------------------------------------------------------------------------------------------|----------------------------------------------------|
| Proportion $\rho$                   | Normal ($z$)          | $np \geq 5$ and $nq \geq 5$                                                              | $z = \frac{\hat p - p}{\sqrt{\frac{pq}{n}}}$       |
| Mean       $\mu$                    | $t$                   | $\sigma$ not known and normally distributed pop <br> or<br>$\sigma$ not known and $n>30$ | $t = \frac{\bar X - \mu}{\frac{s}{\sqrt{n}}}$      |
| Mean       $\mu$                    | Normal ($z$)          | $\sigma$  known and normally distributed pop <br> or<br>$\sigma$  known and $n>30$       | $z = \frac{\bar X - \mu}{\frac{\sigma}{\sqrt{n}}}$ |
| Std $\sigma$ <br> or var $\sigma^2$ | $\chi^2$              | Strict requirement: <br>normally distributed population                                  | $\chi^2 = \frac{(n-1)^2 s^2}{\sigma^2}$            |



#### Differences in tests: left-sided, right-sided, two-sided
The type of test can be determined by looking at $H_1$:

- $H_1: \neq$ then the test is *two-sided*
- $H_1: >$ then the test is *right-sided*
- $H_1: <$ then the test is *left-sided*

#### Equivalence of classic approach and confidence interval

| Paramenter  | Equivalence in conclusion |
|-------------|---------------------------|
| Proportion  | No                        |
| Mean        | Yes                       |
| Stdv or Var | Yes                       |

It is not the same because confidence interval method uses the estimated standard deviation based on sample.
It might also lead to different conclusions.



#### Errors in hypothesis testing
Two types of errors:

- **Type I:** Reject $H_0$, when it is actually true. With $\alpha$ being the probability of a Type I error. 
- **Type II:** Failing to reject $H_0$, when it is actually false. With $\beta$ being the probability of a Type II error. 

**Power of a test:**
$1-\beta$ is the probability of rejecting a false null hypothesis $H_0$. It is common to have at least 0.8 as power of
a test. 


## Testing a claim about a proportion
From the description, find out what kind of test is used (which side). Then execute.

## Testing a claim about a mean
Procedure essentially the same, but use a $t$ statistic if $\sigma$ is not known (check requirements) or a normal
distribution if $\sigma$ is known.

