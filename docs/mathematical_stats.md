# Mathematische Statistik

## Estimators
(following Wooldridge)

### Finite Sample Properties of Estimators

**Basic setup:**  

 - population that depends on *unknown* parameter $\theta$
 - random sample ${Y_1, Y_2, ..., Y_n}$ from this population
 - *estimator* of $\theta$: rule that assigns each possible outcome of sample a value of $\theta$, i.e. estimator $W$ with $W = h(Y_1, Y_2, ..., Y_n)$


**Unbiasdness**  
An estimator $W$ of $\theta$ is unbiased if

$$ E(W) = \theta$$


Bias of an estimator

$$Bias(W) = E(W) - \theta$$


**Sampling variance of an estimator**  
The variance of an estimator is often called *sampling variance*. It is *not* a random variable but a constant; 
although it might be unknown.  
For example, the variance of a sample average:

$$ Var(\bar Y) = \frac{\sigma^2}{n}$$

As a consequence, the variance of this estimator can be made close to zero by increasing the sample size $n$. This is
a key feature of any reasonable estimator. Usually, estimators with the smallest variance are preferred. 


**Efficiency**  
If $W_1$ and $W_2$ are two estimators of $\theta$, $W_1$ is **efficient relative** to
$W_2$ if
 
$$Var(W_1) \leq Var(W_2)$$

Comparing variances for *biased* estimators is meaningless. One way to compare not necessarily unbiased estimators
is to compute the **mean squared error (MSE)** $MSE(W) = E[(W - \theta)^2]$.

### Asymptotic or Large Sample Properties of Estimators
**Consistency**  
Let $W_n$ be an estimator of $\theta$ based on a sample $Y_1, Y_2, ..., Y_n$ of size $n$. Then $W_n$ is a 
**consistent estimator** of $\theta$ if for every $\epsilon > 0$:

$$ P(\vert W_n - \theta \vert > \epsilon) \to 0 \text{ as } n\to \infty$$

If $W_n$ is consistent, then $\theta$ is also known as the **probability limit** of $W_n$ ($plim(W_n)=\theta$). 
If an estimator is *not* 
consistent, then it does not help us to learn about $\theta$ even with an unlimited amount of data. That is why, 
consistency is a **minimal requirement** of a reasonable estimator. Unbiased estimators are not necessarily consistent, 
but those are whose variance shrinks to zero as the sample size grows.  
A classic example is the average of a random sample as estimator of the population mean. This result is also known as
the **law of large numbers:** let $Y_1, Y_2, ..., Y_n$ be independent, identically distributed random variables with
mean $\mu$, then:

$$ plim(\bar Y_n) = \mu$$ 

An important *consistent but biased* estimator is the estimator for the standard deviation $\sigma$.

**Asymptotic Normality**  
Let ${Z_n:n=1,2,...}$ be a sequence of random variables, such that for all numbers $z$, 

$$ P(Z_n \leq z)\to \Phi(z) \text{ as } n\to \infty$$


That means that the cumulative distribution function for $Z_n$ gets closer and closer to the
cdf of the standard normal distribution as the sample size $n$ gets large. When asymptotic normality
holds, for large $n$ we have the approximation $P(Z_n \leq z) \approx \Phi(z)$.  
**Central Limit Theorem**: The **average** from a random sample for **any** population (with finite variance), when 
standardized, has an asymptotic standard normal distribution. 

$$ Z_n = \frac{\bar Y_n - \mu}{\sigma/\sqrt{n}} = \frac{\sqrt{n}(\bar Y_n - \mu)}{\sigma}$$

For large $n$, one can replace the standard deviation $\sqrt{\sigma}$ with its consistent estimator $S_n$ to get an 
approximative standard normal distribution:

$$ \frac{\bar Y_n - \mu}{S_n/\sqrt{n}}$$


### General Approaches to Parameter Estimation

**Method of moments**  
The method makes use of the fact that the **sample average** is an unbiased and consistent estimator of $\mu$ and 
the sample variance is an unbiased estimator (and consistent??) of $\sigma$. Generally, the methods proceeds like this:
the parameter of interest $\theta$ is related to the population mean $\theta = g(\mu)$. Then, $\mu$ can be replaced
with the sample mean $\bar Y$ which gives the consistent estimator $g(\bar Y)$ of $\theta$. If $g(\mu)$ is linear 
function of $\mu$ then $g(\bar Y)$ is unbiased. 

Other useful estimators:  
The **covariance of two variables** can be estimated through the sample covariance

$$ S_{XY} = \frac{1}{n-1}\sum_{i=1}^n(X_i - \bar X)(Y_i - \bar Y)$$

which is a consistent (for sufficiently large $n$) and unbiased estimator. More interestingly would be an estimator
for the correlation $\rho_{XY}$. While the **sample correlation coefficient** is a *consistent* estimator of the 
population corelation, it is a **biased** estimator.


**Maximum Likelihood**  
Assume a population distribution $f(y; \theta)$ and let ${Y_1, Y_2, ..., Y_n}$ be random samples from this distribution. 
Because the samples are random, the joint distribution is equal to the product of densities $f(y_1; \theta)f(y_2; \theta)...f(y_n;\theta)$.
The likelihood function is defined as:

$$ L(\theta; Y_1, Y_2, ..., Y_n) = f(y_1; \theta)f(y_2; \theta)...f(y_n;\theta)$$ 

The maximum likelihood estimator $W$ of $\theta$ is the value of $\theta$ that maximizes the likelihood function.
Usually, it is more conventient to work with the **log-likelihood function**:

$$ \mathbb{L}(\theta) = log[L(\theta; Y_1, Y_2, ..., Y_n)] = \sum_{i=1}^n log[f(Y_i; \theta)] = \sum_{i=1}^n l(\theta; X_i)$$ 

Maximum likelihood estimators are usually consistent and sometimes unbiased. They are generally the most asymptotically
efficient estimators and sometimes the minimum variance unbiased estimator. 


**Least Squares**  
Is the estimator that minimizes:

$$ \sum_{i=1}^n(Y_i - m)^2$$

$\bar Y$ is a least square estimator (and method of moment estimator). For a normal and Bernoulli distribution, the
sample average is also the maximum likelihood estimator of the population mean. 