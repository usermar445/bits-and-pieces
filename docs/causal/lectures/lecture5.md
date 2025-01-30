# Lecture 5 - Causal models and covariate adjutment (Backdoor criterion)

((late))


## Causal effects in linear SCM

**Direct causal effect:** parent to child   
Expected values of interventions

**Total causal effect:** both direct and indirect  

also possible with **path method**: total average causal effect is given by sum of multiplied edge weights for all paths


## Unknown coefficients
Estimate coefficients, usually using *linear regression*

Problem: empirically it shows that some version of linear regression work better than other (i.e. $X_4 \sim X_1, X_2, X_3$ 
is worse than  $X_4 \sim X_1, X_2$) - but why?

Use *Adjustment sets*

## Adjustment sets
Adjustments are sets that allow to estimate the effect von $x_i$ on $x_j$ based only on observational data


## Backdoor adjustment
**Backdoor criterion** is a way to find the $x_z$s for the adjustment sets

**Additional criterion: positivity**  (??)  
Values in interventional regime should also be possible in the observational regime (?)

**Special case: no causal parents** (??)  
Same case as double-blind randomized test

**Special case: use parents of treatment as adjustment set**  


There are many possible adjustment sets but not all of them are statistically efficient, so usually you want smaller sets.


**Identifiability:** an inverventional distributional is identifiable, if it can be re-written using observational distributions


**Backdoor criterion intuition**  

- $Z$ does not contain any descendant of $i$ 
- $Z$ blocks all backdoor paths from $i$ to $j$ ()

I.e. block *spurious associations* (backdoor paths)


Mediators and collider bias (?)


(Example in class, why $Z=\emptyset$ ??)

Find the criterion:

- Find $Z$ that blocks all backdoor paths between $x_i$ and $x_j$


## Adjustment with Linear Regression
((fast))

## Example: smoking and adult asthma

Usually people take all other pre-treatment variables controled for but this is wrong

Why not only adjust for "Predisposition to asthma"? Because Childhood asthma is collider, therefore also 
adjust for parental smoking







