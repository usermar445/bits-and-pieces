# Skills inferences from two samples

**Overview**

Testing for a proportion:

- testing two sample proportions


Testing for a mean: 

- independent samples: testing with hypothesis testing and confidence interval
- paired samples: testing with hypothesis testing and confidence interval



## Testing for a proportion (Section 8.2)

**Requirements**

1. From two random samples that are *independent*.
2. For each sample, at least 5 successes and failures, i.e. $n \hat p \geq 5$ and $n \hat q \geq 5$.

**Null hypothesis**  

$$H_0: p_1 = p_2$$

**Test statistic**
$$z=\frac{(\hat p_1 - \hat p_2) - (p_1 - p_2)}{\sqrt{\frac{\bar p \bar q}{n_1} + \frac{\bar p \bar q}{n_2}}} $$
with $p_1 - p_2 = 0$ assumed by $H_0$.

And *pooled sample proportion*
$$ \bar p = \frac{x_1 + x_2}{n_1 + n_2}$$


**Confidence interval**

$$(\hat p_1 - \hat p_2) - E < (p_1 - p_2) < (\hat p_1 - \hat p_2) + E$$

with $E = z_{\alpha/2}\sqrt{\frac{\hat p_1 \hat q_1}{n_1} + \frac{\hat p_2 \hat q_2}{n_2}}$


**Test procedure**  
Same as in normal hypothesis testing. 

**Equivalence of $p$-value / critical value method and confidence intervals**  
Here as well, the two methods are not equivalent and conclusion might be different. 

**Confidence interval method**  
If the confidence interval does not include 0, there is evidence that suggests that the two proportions are not the same. 
Check if the sign of the confidence interval boundaries to conclude if $p_1 \gtrless p_2$.


## Testing for a mean
### Independent samples, unknown $\sigma$
**Requirements**  

1. Two independent, random samples
2. $\sigma_1$ and $\sigma_2$ are unkown and assumed to be not equal
3. Either $n_1 > 30$ and $n_2 > 30$ or from populations with normal distributions. 

**Procedure**  
$t$ distribution is used.

**Test statistics**  

$$t=\frac{(\bar x_1 - \bar x_2) - (\mu_1 - \mu_2)}{\sqrt{\frac{s_1^2}{n_1}+ \frac{s_2^2}{n_2}}}$$

With $\mu_1 - \mu_2 = 0$ assumed by $H_0$.

**Degrees of freedom**  
Use approximation formula:

$$df = \text{ smaller of } n_1-1 \text{ and } n_2 -1$$

**Confidence intervall**

$$(\bar x_1 - \bar x_2) - E < (\mu_1 - \mu_2) < (\bar x_1 - \bar x_2) + E$$

With $E = t_{\alpha/2}\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}$

**Equivalence of methods**  
All methods are equivalent.

### Independent samples, known $\sigma$
**Requirements**  
Same requirements hold.

**Procedure**  
Normal distribution is used.


**Test statistics**

$$z=\frac{(\bar x_1 - \bar x_2) - (\mu_1 - \mu_2)}{\sqrt{\frac{\sigma_1^2}{n_1}+ \frac{\sigma_2^2}{n_2}}}$$

With $\mu_1 - \mu_2 = 0$ assumed by $H_0$.


**Confidence intervall**

$$(\bar x_1 - \bar x_2) - E < (\mu_1 - \mu_2) < (\bar x_1 - \bar x_2) + E$$

With $E = z_{\alpha/2}\sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}$


### Independent samples, unknown $\sigma$, but assumed $\sigma_1 = \sigma_2$

**Requirements**  
Same requirements hold.

**Procedure**  
$t$ distribution is used.


**Test statistics**

$$t=\frac{(\bar x_1 - \bar x_2) - (\mu_1 - \mu_2)}{\sqrt{\frac{s_p^2}{n_1}+ \frac{s_p^2}{n_2}}}$$

With $s_p^2$ as *pooled sample variance*: $s_p^2 = \frac{(n_1-1)s_1^2 + (n_2 - 1)s_2^2}{(n_1-1) + (n_2 - 1)}$

**Degrees of freedom**  

$$df = n_1 + n_2 - 1$$

**Confidence intervall**

$$(\bar x_1 - \bar x_2) - E < (\mu_1 - \mu_2) < (\bar x_1 - \bar x_2) + E$$

With $E = t_{\alpha/2}\sqrt{\frac{s_p^2}{n_1} + \frac{s_p^2}{n_2}}$


### Dependent samples
No exact test available, only approximative. 

**Requirements**  
1. Sample data is matched pairs. 
2. Random samples
3. Either (or both): $n>30$ or population approx. normal

**Procedure**  
$t$ distribution is used.

**Test statistics**

$$t=\frac{\bar d - \mu_d}{\frac{s_d}{\sqrt{n}}}$$

With $\bar d$ as mean value of differences of paired samples and $s_d$ as stdv. of differences.

**Degrees of freedom**

$$df = n-1$$

**Confidence intervall**

$$\bar d - E < \mu_d < \bar d + E$$

With $E = t_{\alpha/2}\frac{s_d}{\sqrt{n}}$

**Equivalence of methods**  
The methods are equivalent.


