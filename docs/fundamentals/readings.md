# Readings

## 2. Statistical Learning
### What is statistical learning?
**Why estimate $f(X)$**

Mainly two reasons:

- Prediction
- Inference


**How to estimate $f$**


- Parametric methods: make assumption about functional form of $f$
  - fit training data
  - then estimate $f$ (often with **ordinary least squares**)
- Nonparametric methods

**Tradeoff accuracy and interpretability**

**Supervised vs. unsupervised learning**

**Regression vs. classification problems**
### Assessing Model Accuracy
**Measuring quality of fit**

$$\text{MSE} = \text{mean squared error}$$

Important:

- training MSE is always smaller than test MSE
- MSE dependent on flexibility
- increasing flexibility leads to lower (better) training MSE, but not necessarily test MSE (U-shape curve)
- small training MSE but high test MSE $\rightarrow$ *overfitting*
- in praxis: usually test MSE is unkown; cross-validation used to estimate test MSE and find optimal point

**The Bias-Variance Tradeoff**

- MSE can never lie below $Var(\epsilon)$
- In general, more flexible methods lead to higher variance
- Less flexible have a higher bias


**Classification setting**

Instead of MSE, the **error rate** is used.
## 3. Linear Regression
### Simple Linear Regression
### Multiple Linear Regression
### Other considerations
### Comparison k nearest neighbour
## 4. Classification
### Why not linear regression?
### Logistic Regression
### Generative Models
### Generalized Linear Models
## 5.1 Cross-Validation
## 8.1 Decision Trees