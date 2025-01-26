# Skills nonparametric tests

**Overview**

Sign test:

- sign test for matched pairs
- sign test for nominal data

Wilcoxon test:

- Wilcoxon signed-rank test
- Wilcoxon rank-sum test
- test median



### Sign test
**Applicability**

1. Matched pairs (subtract secon value from first, ignore all 0s and record sign of difference)
2. Nominal data with two categories (represent each category with a sign)
3. Median of single population: subtract median of each sample value, record sign and ignore 0s

**Notation**   
Number of *less frequent sign* $x$. And $n$ number of signs.

**Requirements**  
Random sample.

**Test statistic**  
If $n\leq 25$ then $x$.

If $n> 25$: $z = \frac{(x + 0.5) -  n/2}{\frac{\sqrt{n}}{2}}$.

**Critical values**  
If $n\leq 25$, then use sign test table. If $n> 25$ use $z$ distribution. 

**Procedure**  
Always check if sample contradicts $H_1$ (must be in the same direction significant). Otherwise normal procedure.


### Wilcoxon signed-ranks test (for matched pairs)

**Applicability**

1. Matched pairs (claim median of zero)
2. Population of individual values: population median equal to some value.

**Notation**   
With $T$ as the smaller of the following sums:

1. sum of positive ranks of nonzero differences
2. absolute value of the sum of the negative ranks of the nonzero differences

**Requirements**  

1. Random sample
2. Population of differences approx. *symmetric*. 

**Test statistic**  
If $n\leq 30$ then $T$.

If $n> 30$: $z = \frac{T - \frac{n(n+1)}{4}}{\sqrt{\frac{n(n+1)(2n+1)}{24}}}$.

**Critical values**  
If $n\leq 30$, then use Wicoxon signe-ranks test table. If $n> 30$ use $z$ distribution.

**Procedure**  
Always check if sample contradicts $H_1$ (must be in the same direction significant). Otherwise normal procedure.

For matched pairs:

1. Calculate differences $d$ of pairs
2. Discard 0 values, then rank remaining absolute values
3. Assign every rank the corresponding sign of difference
4. Calculate $T$, and execute test

For median of a single population:  
Create matched pairs by subtracting assumed population mean from it.


### Wilcoxon rank-sum test for two independent samples

**Applicability**  
$H_0$: two samples come from poppulations with *equal medians*  
$H_1$: median of first population is $\neq < >$ from second population

**Notation**   
$R_1 = R:$ sum of ranks of sample 1.

**Requirements**

1. Random sample
2. Each of the sample have more than 10 values.

**Test statistic**  

$$z = \frac{R - \mu_R}{\sigma_R}$$

With $\mu_R = \frac{n_1(n_1 + n_2 + 1)}{2}$ and $\sigma_r = \sqrt{\frac{n_1 n_2 (n_1 + n_2 +1)}{12}}$.

**Critical values**  
Use $z$ distribution.

**Procedure**  

1. Create one big sample, and assign ranks
2. Calculate sum of ranks for each sample
   3. Calculate $z$, execute test