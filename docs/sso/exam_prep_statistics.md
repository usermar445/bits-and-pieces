# Exam Prep

## Estimating (CI)

### Mean (normal distribution)
**Requirements**

- normal distribution

**CI**  
$\bar x \pm z_{\alpha/2} \frac{\sigma}{\sqrt{n}}$


### Mean (with unkown $\sigma$)
**Requirements**  

- normal??
- unkown $\sigma$

**CI**  
$\bar x \pm t_{\alpha/2, n-1} \frac{s}{\sqrt{n}}$


### Proportion
(see formula sheet)


## Executable Tests

### Testing

Kind of tests: 

- $H_1$ involves $\neq$ then *two-sided test*, so $\alpha/2$
- $H_1$ invovles $<$ then *left-sided test*, so $p$-value $<$ $\alpha$ or $T< t_{\alpha}$ 
- $H_1$ invovles $>$ then *right-sided test*, so $p$-value $<$ $1-\alpha$ or $T> t_{\alpha}$



### one sample mean $\mu$ (from normal distribution, unknown $\sigma$)
**Requirements**  

- sample from normal distribution or $n>30$
- unkown $\sigma$

**Hypotheses**  
$H_0: \mu = \leq \geq \mu_0$  
$H_1: \mu \neq > < \mu_0$

**Test**: $t$-test


### one sample proportion $p$
**Requirements**  

- random sample
- binomial distribution conditions
- $np \geq 5$ and $nq \geq 5$ 

**Hypotheses**  
$H_0: p = \leq \geq p_0$  
$H_1: p \neq > < p_0$

**Test:** binomial aprrox. by normal

### two sample test means $\mu$ (independent samples, $\sigma_1 \neq \sigma_2$)
**Requirements**

- $\sigma_1$, $\sigma_2$ unknown, assumed $\sigma_1 \neq \sigma_2$
- random sample
- independent
- $n>30$ for both or *normal*

**Hypotheses**  
$H_0: \mu_1 -\mu_2 = \leq \geq 0$  
$H_1: \mu_1 - \mu_2 \neq > < 0$

**Test:** $t$-test

### two sample test means $\mu$ (independent samples, $\sigma_1 = \sigma_2$)
**Requirements**

- $\sigma_1$, $\sigma_2$ *unkown*, but assumed $\sigma_1 = \sigma_2$
- random sample
- independent
- $n>30$ for both or *normal*

**Hypotheses**  
$H_0: \mu_1 -\mu_2 = \leq \geq 0$  
$H_1: \mu_1 - \mu_2 \neq > < 0$

**Test:** $t$-test


### two sample test means $\mu$ (dependent sample)
**Requirements**

- paired data
- random sample
- independent
- $n>30$ for both or *normal*

**Hypotheses**  
$H_0: \mu_d = \leq \geq 0$  
$H_1: \mu_d \neq > < 0$

**Test:** $t$-test

### two sample proportions
**Requirements**

- random sample
- for both samples: at least 5 successes and 5 failures

**Hypotheses**  
$H_0: p_1 -p_2 = \leq \geq 0$  
$H_1: p_1 - p_2 \neq > < 0$

**Test:** *normal*

### $\chi^2$ test (both homogeinity or independence)
**Requirements**  

- at least 80\% of the $E_{ij}$s should be at least $5$$

**Hypohesis**  

- *Independence*: $H_0$: the row and columns variable are independent, $H_1$: dependent
- *Homogeinity*: $H_0$: distribution among categories of row variables the same for each column, $H_1$: not the same

**Kind**: alwas *right-sided*

$E_{ij} = \frac{O_j O_i}{n}$

**Test** $\chi^2$

### Correlation test
**Requirements** 

- bivariate sample

**Hypothesis**  
$H_0: \rho = 0$  
$H_0: \rho \neq 0$

## Further tests to know

### Shapiro-Wilk test
To test **normality**

$H_0$: $p$ is normal distribution  
$H_1$: $p$ is not normal distribution


### Sign test
To test median

Test statistic: \# of $X_i < m$

### Signed rank test
Matched pairs or median

### Rank sum test (Mann-Whitney test)
Compare two samples median

### Fishers exact test for 2x2 tables
Exact test, not dependent on approximation; used for contingency tables 2x2

## Regression
### Formula

**Simple linear regression**

$\hat \beta_0 = \bar y - \hat \beta_1 \bar x$

$\hat \beta_1 = r \frac{s_y}{s_x}$

$SSE = \sum_{i=1}^n (y_i - \hat \beta_0 - \hat \beta_1 x_i)^2$

$SSE = \sum \hat e_i^2$

estimated variance of errors $e_i$, $\hat \sigma^2 = s^2 = \frac{SSE}{n-2}$

sum of squared errors (total variation): $SS_{yy} = \sum_{n=1}^n (y_i - \bar y)^2$  
or $SS_{yy} = (n-1)s_y^2$

coefficient of determination $r^2 = \frac{SS_{yy}- SSE}{SS_{yy}}$

t value (test statistic) $T = \frac{\hat \beta_1}{s_{\hat \beta_1}}$  
with $H_0: \beta_1 = 0$, $H_1: \beta_1 \neq 0$. In bivariate case, same as $\rho=0$ testing. 

CI for coefficient: $\hat \beta_1 \pm t_{\alpha/2} s_{\hat \beta_1}$

**Mulitple linear regression**  

multiple regression estimated variance $\hat \sigma^2 = s^2 = \frac{SSE}{n-k-1}$

$R_{adj} = 1 - \frac{n-1}{n-(k+1)}(1-R^2)$

Testing coefficients: $H_0: \beta_1 = ... = \beta_k = 0$  
Assumption: independent errors have $N(0, \sigma^2)$ distribution  
$F$-distribution

CI for coefficients: $\hat \beta_i \pm t_{\alpha/2, n-(k+1)} s_{\hat \beta_i}$
