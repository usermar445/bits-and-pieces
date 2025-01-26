# Skills Estimating

**Overview**

Estimating a proportion:

- Estimating proportion with point estimator and confidence interval

Estimating a mean:

- Estimating mean with point estimator and confidence interval


## Estimating a proportion

Steps: 

1. make point estimate $\hat p$ from sample proportion
2. construct CI: use normal distribution with $\alpha/2$,  $E = z_{\alpha/2} \sqrt{\frac{\hat p \hat q}{n}}$
3. use $\hat p \pm E$


**Determining sample size**  
When $\hat p$ is known: $n = \frac{z_{\alpha/2}^2 \hat p \hat q}{E^2}$

If $\hat p$ is *not* known: $n = \frac{z_{\alpha/2}^2 0.25}{E^2}$
(assuming $p=0.5$)


**Determining margin of error**  
$E = \frac{\text{upper bound } - \text{ lower bound}}{2}$

**Determining $\hat p$ from CI**  
$E = \frac{\text{upper bound } + \text{ lower bound}}{2}$


## Estimating a mean

Steps:

1. make point estimate $\bar x$ from sample proportion
2. construct CI: use t distribution with $\alpha/2$,  $E = t_{\alpha/2, n-1} \frac{s}{\sqrt{n}}$
3. use $\hat p \pm E$


**Determining sample size**  
$n = [\frac{z_{\alpha/2} \sigma}{E}]^2 \approx \frac{(z_{\alpha/2})^2 s^2}{E^2}$


**Determining margin of error**  
$E = \frac{\text{upper bound } - \text{ lower bound}}{2}$

**Determining $\hat p$ from CI**  
$E = \frac{\text{upper bound } + \text{ lower bound}}{2}$

**How to make the CI smaller** 

- larger $n$
- smaller $\sigma$ or $s$
- larger $\alpha$ (but less confidence)