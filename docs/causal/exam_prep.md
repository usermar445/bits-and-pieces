# Exam prep


# 1. Basics

### Introduction

**Definition of causality**  
Informal Defintion: X causes Y if changing distribution of X changes distribution of Y

**Causal Hierarchy**  
Level 1: Association $P(y \vert x)$  
Level 2: Intervention $P(y \vert do(X))$  
Level 3: Counterfactuals $P(y \vert x', y')$  

Causality: Level 2 + 3

**RCT**  
Randomized Control Trials: split in Control and Treatment Group 

Double-blind: neither subjects nor researcheres know which group is which

- Observational vs. interventional data 

**Biases**  

- Confounders: influences treatment and outcome
- Selection bias
- Cylces: can lead to spurious correlations

Not adjust just for everything

**Simpson' paradox**  


**Reichbach's principle**  

Correlation implies: X causes Y, Y causes X, Caused by common cause, or any combination

How to derive graph? 

- add experiment
- measure more variables


### Probability Theory

**Bayes Theorem**

$p(A \vert B) = \frac{p(B \vert A) p(A)}{p(B)}$

Notation:

- $p(A)$: prior
- $p(B)$: evidence
- $p(B \vert A)$: liklehood
- $p(A \vert B)$: posterior

- Independence

**Conditional Independence**  
$Y \perp X \vert Z$ if $p(Y \vert X, Z) = p(Y \vert Z)$

$X$ does not add any information on $Y$ not already contained in $Z$


**Correlation vs. dependence**
(Spearman) correlation is linear, therefore only linear relationships captured

If two variables are **indpendent**, then correlation = 0. But **not** vice versa.


**Factorizing distributions**  
Chain rule: $P(X,Y) = P(X \vert Y) P(Y)$$


# 2. Graphical Models

### Graphs

**Graph terminology**  

Collider: non-endpoint, 


**d-separation**  
Under standard conditions, allows to read conditional independences

All paths are blocked


### Causal graphs

**Causality**
X causal effect on Y if $P(Y \vert do(X =x)) \neq P(Y \vert do(X = x'))$  
or $P(Y \vert do(X =x)) \neq P(Y)$

Confounding:  $P(Y \vert do(X =x)) \neq P(Y \vert X=x)$

- do-operator


**SCMs**  
Important: Variance only calculated if random variable


Assumptions: 

- all noise terms independent of each other


# 3. Identifying Estimands

Definition: Identification strategy is formula to estimate an interventional distribution from a 
combination of observational ones. do-calculus is complete
 
### Backdoor criterion

Application: 

- no unobserved confounders

**Criterion** 

1. No descendants of $i$ (any children)
2. Blockes all **backdoor** paths 
   3. Non collider and part of adjusment set
   4. Or collider and collider and its descendants **NOT** part of adjustment set


**Assumptions**  

For adjustment: 

- Positivity: all values of treatment possible in observational 

Intuition: 

- block spurious associations (all paths into $i$)
- is not complete (does not find all valid adjustment sets)


### Adjustment criterion

Finds all valid adjustment sets


**Criterion**

1. No descendants of $r \neq i$ on **directed paths** from $i$ to $j$ 
2. Blocks all paths that are not directed

-> important: also descendants of $j$ not part of adjustment set

### Frontdoor criterion

Application: 

- when unobserved variable
- mediator

1. $M$ blocks all directed paths from $i$ to $j$
2. No unblocked backdoor paths from $i \leftarrow ... M$ with $Z = \emptyset$
3. $Z = {i}$ blocks all backdoor paths from $M \leftarrow ... j$


### IV 

Application:

- when (unobserved) confounder and no mediator variable

Assumptions: 

- IV is dependent on X
- (unobserved) confounder independent of IV
- IV not directly influence outcome

**2SLS**  

Intuition: 

1. Regress X on IV
2. Construct $\hat X$
3. Regress $Y$ on $\hat X$

**Instruments**  

- Weak: cov(I, X) is small
- Conditional IV


### Counterfactuals

Steps: 

1. Abductions
2. Action
3. Prediction

**Potential outcomes**  

Problem: we cannot observe counterfactual, but can estimate effect on population level, ATE

**Assumptions**  

- SUTVA: stable unit treatment value assumption (treatment assignment of unit i should not affect others)
- Consistency: actual outcome is the potential outcome of the assigned treatement
- (Conditional) ignorability: no unmeasured confounding
- Positivity: no deterministic assignment

# 4. Causal Estimation

### Estimation

**ATE**  

$ATE = E[Y(t=1) - Y(t-0)] = E[Y\vert do(T=1) - Y\vert do(T=0)]$

**ATT** 

$ATT = E[Y(t=1) - Y(t=0) \vert T=1]$

**ATc**

$ATT = E[Y(t=1) - Y(t=0) \vert T=0]$


**CATE**  
$CATE(w) = E[X(t=1) - Y(t=0)\vert W = w]$


### Estimation Methods

**Exact Matching**  

Find most similar person

Balancing: discard unused values

Contiuous: distance matching


**Propensity Score Matching**  
Propensity Score: probability of getting assigned the treatment

**IPW**  
Weight bei inverse of probability of treatemnt received


- ATE, etc.
- Matching
- Propensity Score
- IPW

**Misssing data**  


# 5. Causal Discovery

**Assumptions**  

- Markov: d-separations implies conditional independence (could be more that are not implied)
- Faithfull: if graph faithful, then conditional independence is also d-separated in graph
- Causal sufficiency: no latent confounders
- Acyclicity

**I-Map**  
Satisfy Global markov Property (other way for BN)

**Definitions** 

I-Maps are not perfect maps (could still be more d-separations not in conditional independence). For causal discovery, 
you want perfect maps. 

MEC: markov equivalence class: possibly many DAGs satisfy markov and faithful; all DAGs with same d-separations

Not every distribution has a perfect map

MECs have: 

- same skeleton
- same v-structures

Can be represented with a CPDAG (complete partially directed ayclic graph)

- Global Markov Property
- I-Maps



**Overview**

- Constraint-based: Conditional Independence Tests; Output: CPDAG (or MEC); SGS, PC
- Score-based: Penalized Likelihood; CPDAG (or MEC); GES
- Restricted model: Non-linear additive noise; Linear non-gaussian; DAG; RESIT, LINGAM
- Interventional/Causal Invariance; Observational + Interventional; 


### Constraint based causal discovery

Idea: perform conditional independence test on observational data and use them to constrain possible graphs (using d-separation)

**SGS Algorithm**  

1. determine skeleton (start with completely connected graph)
2. determine v-structures
3. direct as many edges as possible (Meeks rules)

But: computationally inefficient


**PC algorithm**  
1. determine skeleton in optimized way
2. determine v-structures in optimized way
3. direct as many edges as possible (Meeks rules)


Skeleton learning in optimized way: do not try every adjustment set (for independence test) but only
all adjecent to $i$ and $j$ given iteration $k$ (size of adjustment set)

Fails: 

- too few samples
- very weak dependence 
- wrong parametric assumptions
- if there are unmeasured confounders or selection bias -> FCI


### Score-based
Intuition: find graph that maximises score (Bayesian network structure learning)

Idea: find graph and parameters that maximizes liklihood of getting data from this graph, parameters

-> will lead to overfitting, therefore, encourage sparsity with penalty: BIC

**Bayesian Information Criterion** 
Number of edges in G + const

- Score equivalence: all DAGs in a MEC get the same score
- decomposable
- local consistency


**GES**  

- Optimise BIC
- Reduce search space

1. Empty CPDAG
2. Forward: Add edges until local maxima
3. Backward: remove edges until local maxima

--> both involve domain knowledge`


### Restricted models

**Additive Noise Models (ANMs)**

- $f(X)$ is not linear or
- noise term is uniform (not Gaussian) 

cannot do linear models with Gaussian noise


**RESIT**  
Regression with subsequent indpendence test

Do regression X->Y first, then test if residual independent of X; then the other way around; 
if rejected in one direction (dependent), other is causal


**Linear Non Gaussian Acyclic Models (LINGAM)**
Intuition: use causal ordering and linear matrix multiplication to get order of B which is DAG


Assumption: 

- does not need faithfulness
- non Gaussian noises with positive variance


**ICA**  

- the more non-Gaussian noises are combined, the more Gaussian the output becomes
- If assumed: source non-Gaussian and independent; then maximizing non-Gaussianity disentangles signals


# 6. Do-calculus and advanced topics

### do-calculus

**Rules**: 

1. A d-separated B $\vert$ C then $P(A \vert B, C) = P(A \vert C)$
2. A d-separated I $\vert B, C$ then $P(A \vert do(B), C) = P(A \vert B, C)$
3. A d-separated I $\vert C$ then $P(A \vert B , C) = P(A \vert C)$


### Transportability

We have: 

- observational data
- experimental data

from different sources

Use **selection diagrams**: depict multiple distributions in one graph (extension of DAG)


### Invariant Causal Prediction

Interventions: identify parents (what is not connected anymore) + descendants (which variables change)

Find least amount of interventions to reconstruct possible graph

Intervene on "central" nodes


Find causal parents of Y

Non of the environemnts Y is intervened upon 

Intuition: Robust predictor of Y across different environments then parent -> finds subsets of parents

### Joint Causal Inference from Multiple Context

- joint causal graph
- add context variables (multiples) -> disentables which changes happen in which datasets
- Here: also know in which data set which variable is shifted
- try to do: try to recover equivalence class of graph (from conditional independencies)

### Causality-inspired ML

Put source data + target data together, pretend from single distribution, create causal graph

then: try to separate features -> set of features that d-spearates Y from context