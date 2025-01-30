# Part 3: Supervised Learning

## Overview Machine Learning classification

General task, there is some unkown, general relationship in the data:

$$ Y = f(X) + \epsilon$$

We can only estimate this by:

$$ \hat Y = \hat f(X)$$

**Goal:** find best estimation of $f$ (most accurate)

**Why?** to make *predictions* and *inferences*

**Two methods**  

- *Parametric*: two stages: 1) make assumption about functional form or shape of $f$, 2) fit data to model
- *Non-parametric*: not make assumptions about $f$, just fit data to model


Two types of problems: 

- *Supervised Learning*: labeled data, i.e. data + response $y$; *classification*: discrete data and *regression* for continuous data
- *Unsupervised Learning*: unlabeled data, i.e. only data without a response $y$; trying to infer structure

**Overview methods**:
<img src="/images/overview_supervised.png" alt="test-training MSE" height="auto">


## Bias-Variance trade-off

*Accuracy* describes how good the model is on predictions. *Flexibility* describes how *flexibel* a model is, that is, 
what kind of shapes for $f$ it allows. More flexible models can lead to higher accuracy (less *bias*). But there are 
several trade-offs: 

**Interpretability vs. flexibility**  

- Higher flexibility (lower bias, higher complexity) leads to lower interpretability and vice versa. 


**Bias vs. variance**  
*Bias* describes how much error is introduced by a certain model. *Variance* describes how much the estimation of $f$
will change if the underlying data changes. It holds: 

- High bias + low variance
- Low bias + high variance
- More flexibility leads to low bias and high variance

Best model: finds "sweat spot" between bias and variance

![Bias Variance trade-off](images/tradeoff_bias_variance.png)

**Under-fitting vs. overfitting**

- Under-fitting: model complexetiy not high enough to capture $f(X)$ (high bias)
- Over-fitting: model complexity too high, following error in training set too closely, missing the point

**Prevent over-fitting: Regularization**  
Use **regularization** to prevent-overfitting. It is the process of penalizing large values of model parameters (through
introduction of a loss function). 

In case of linear regression, there are two options: 

- **Ridge regularization**: Quadratic function $\lambda \sum_{j=1}^p \beta_j^2$
- **Lasso regularization**: forces some coefficients to 0, $\lambda \sum_{j=1}^p \vert \beta_j \vert$


## Feature engineering
Feature engineering = process of creating or transforming features.

**Qualitative features:**  

- e.g. one-hot encoding
- use `from sklearn.feature_extraction import DictVectorizer`

**Text features:**  

- tf-idf: term-frequency inverse-document-frequency
- use `stopwords`
- use `regex`
- use `from sklearn.feature_extraction.text import TfidfVectorizer`

Polynomial features:  

- `from sklearn.preprocessing import PolynomialFeatures`

**Imputer:**  

- `from sklearn.preprocessing import Imputer` e.g. to impute `mean`

**Pipeline:**  

```
from sklearn.pipeline import make_pipeline

model = make_pipeline(Imputer(strategy='mean'),
                      PolynomialFeatures(degree=2),
                      LinearRegression())
```


## Model accuracy and validation
To measure a model's performance (accuracy), different measures can be used:

- **Regression**: *mean squared error (MSE)*, i.e. $\frac{\sum_{i=1}^n(\hat y_i - y_i)^2}{n}$
- **Classification:** *error rate*, i.e. $\frac{1}{n}\sum_{i=1}^n I(y_i \neq \hat y_i)$

**Relationship training, validation, and test accuracy**  
The MSE is computed based on the test data, but we are interested in *test* MSE instead of *training* MSE. Often, test 
data is not available and the *test* MSE has to be estimated. Furthermore, increasing model flexibility leads to a lower
*training* MSE but not necessarily a lower *test* MSE. 

<img src="/images/test_training_MSE.png" alt="test-training MSE" width="50%" height="auto">

**Relationship to bias and variance**  
The *expected MSE* can be decomposed into *variance* of $\hat f(x_0)$, squared *bias* of  $\hat f(x_0)$, and the *variance 
of the error term* $var(\epsilon)$. The best method, therefore, will minimize simultanuously the *variance* and the squared
*bias* of $f$. But the expected MSE can never lie below $var(\epsilon)$. Both quantities determine the MSE:

<img src="/images/bias_variance_mse.png" alt="test-training MSE" height="auto">


**Cross-validation**  
In practice, test data is often not available. We, therefore, need a method to estimate the test MSE. Usually, a **validation**
or **hold-out** set is used: data is trained on *training* set and then predicted on *validation* set to estimate 
the MSE.

Different methods can be used:

- *Hold-out set*: just one set used as validation; problems: just one estimate + data loss for training
- *Leave-One-Out Cross-Validation*: estimates MSE $n$ times and always leaves one data point out, then calculates average MSE; problem: computationaly intensive
- *k-fold cv*: defined number of partitions of hold-outs sets, average MSE calculated

**Scikit-learn**  

Split training set in training-validation data (confusingly, `test`): 
```
from sklearn.cross_validation import train_test_split
# split the data with 50% in each set
X1, X2, y1, y2 = train_test_split(X, y, random_state=0,
                                  train_size=0.5)
```

k-fold cv: 
```
from sklearn.cross_validation import cross_val_score
cross_val_score(model, X, y, cv=5)
```

leave one out cv: 
```
from sklearn.cross_validation import LeaveOneOut
scores = cross_val_score(model, X, y, cv=LeaveOneOut(len(X)))
scores
```

**Learning curves**  
Plot of training/ validation with respect to size of training data:
<img src="/images/learning_curve.png" alt="test-training MSE" width="50%" height="auto">


**Confusion matrix**  
<img src="/images/confusion_matrix.png" alt="test-training MSE" height="auto">

Definitions:

- **Sensitivity** or **True Positive Rate**: $\frac{TP}{TP+FN}$; fraction of actual positives that were predicted positive; how good is a classifier in detecting positives?
- **Specificity** or **True negative rate**: $\frac{TN}{TN+FP}$; fraction of actual negatives that were predicted negative;  how good is a classifier in detecting negatives?
- **Precision:** $\frac{TP}{TP + FP}$; fraction of actual positives of all positively predicted, or: of all positively predicted labels, what fraction was actual positive?
- **Accuracy**: $\frac{TP + TN}{TP +TN + FP + FN}$
- **False positive rate**: $\frac{FP}{FP+TN}$ or $1-specificity$, fraction of false positives of all actual negative cases; how prone is a classifier to falsly identify negatives as positives?
- **False negative rate**: $\frac{FN}{FN+TP}$ or $1-sensitvitiy$, fraction of false negatives of all actual positive cases; how prone is a classifier to falsly identify positives as negatives?

Cases:

- Poisenous mushrooms: cannot afford TN, therefore, maybe have lower "threshold", e.g. $P(C \vert x)$
- Malicious content: contenious to have FP

**Type of errors**  
FPR is equivalent to a *type I error* ($\alpha$), and FNR is equivalent to *type II error* ($\beta$).


**ROC curve**  
For a given threshold, classifiers have always a *trade-off* between TPR and FPR (or sensitivity and specificity). The
ROC curve shows this trade-off for all possible thresholds:
<img src="/images/roc.png" alt="test-training MSE" height="auto" width="50%">
<img src="/images/auc.png" alt="test-training MSE" height="auto"  width="50%">

The higher AUC, the better the classifier. 


## Regression: Linear regression
**Simple linear regression**

```
from sklearn.linear_model import LinearRegression
model = LinearRegression(fit_intercept=True)

model.fit(x[:, np.newaxis], y)

xfit = np.linspace(0, 10, 1000)
yfit = model.predict(xfit[:, np.newaxis])

plt.scatter(x, y)
plt.plot(xfit, yfit);
```

**Problems**  

- more than 1 predictor
- categorical predictors
- non-linear relationships

**Multiple linear regression**  
For categorical, use one-hot encoding. 

```
from sklearn.preprocessing import PolynomialFeatures
x = np.array([2, 3, 4])
poly = PolynomialFeatures(3, include_bias=False)
poly.fit_transform(x[:, None])
```

**Regularization**
Lasso: 
```
from sklearn.linear_model import Lasso
model = make_pipeline(GaussianFeatures(30), Lasso(alpha=0.001))
basis_plot(model, title='Lasso Regression')
```

Ridge:
```
from sklearn.linear_model import Ridge
model = make_pipeline(GaussianFeatures(30), Ridge(alpha=0.1))
basis_plot(model, title='Ridge Regression')
```

## Classification: Logistic regression
**Goal**: Predict $P(C_k \vert X)$

**Why not linear regression?** not bounded between 1 and 0, hard to interpret as probabilities, difficult converting 
continuous output to class

**Formula:** $p(C_1 \vert X) \approx \frac{e^{\beta_0 + \beta_1 X}}{1+e^{\beta_0 + \beta_1 X}}$

$\beta_0$: position of curve, $\beta_1$: "slope"

**Estimator**: Maximum likelihood estimator, equivalent to minimizing negative log-likelihood


**Gradient Descent**  

1. Chose random parameters $\beta$
2. Update according $\beta_{t+1} = \beta_t - \gamma (\nabla f(\beta_t))

With $\gamma$ as step size. **Problems**: computationally expensive

**Stochastic gradient descent**
Randomly choose subset of training data to estimate gradient


## Classification: Generative Models
Instead of estimating *posterior* probability directly ($P(C_k \vert X)$), estimate class-conditioned probability
($P(X \vert C_k)$) and the prior probabilities ($P(C_k)$).

Estimating $P(C_k)$ from data is easy, however, estimating $P(X \vert C_k)$ is hard (because it is the joint
probability distribution of any combination of feature $P(x_1, x_2, ..., x_p \vert C_k)$, therefore, $2^p$ probabilities in case $x\in\{0,1\}$).

## Classification: Naive Bayes
Makes assumption that features are **conditionally independent**, i.e. $P(X \vert C_k) = P(x_1 \vert C_k) P(x_2 \vert C_k)...$ 

Procedure: counting (+ using **smoothing parameter** $\alpha$ to avoid zero probabilities)

## Classification: k-nearest neighbour (kNN)
Nonparametric model

**Idea:** Assume that the probability that $x_0$ belongs to class $C_k$ is equal to the fraction of the nearest $K$
points that also belong to $C_k$

## Classification: Decicion Trees
Non-parametric (and non-linear) approach for classification (and regression).

**How does it work? CART algorithm**  

1. split training set in two sub-sets according to feature value pair
2. Recursively split following subsets

*Greedy* algorithm: select feature **k** and value **t** that produce the purest subsets, i.e. *minimize Gini index*. 


**Problems**  
Easy to overfit, accuracy not competitive with other models

**Prevent over-fitting**  
Hyperparameter $\alpha$: `max-depth`, but trade-of with accuracy.

*Pruning*: grow tree normally, find sub-tree that minimizies loss function

## Classification: Ensemble Methods
Combining multiple decision trees. Improve accuracy but less interpretability.

**Methods**  

- Bagging (bootstrap aggregation)
- Random forest
- Boosting

**Bagging**  
Taking $B$ random samples (bootstraps) from sample and build trees. Then take average (regression) or majority 
(classification).

Problem: correlated features

**Random Forest**  


**Boosting**  
Same as other methods, but **sequentially**.


## Link prediction

**Graphs**  
Graph $G \langle E, N \rangle$ consists of edged $E$ and nodes $N$. Can be either represented as:

- list of edges
- list of adjacencies (for each node, list of neighbouring nodes)
- adjacency matrix

**Properties**  

- degree: number of connections per node
- average path length: average shortest path between any pair of nodes
- clustering coefficient: fraction of triangles
- assortativity: correlation between linked nodes


**Real-life social networks:** degree is highly heterogenous (preferential attachment), low average path length, 
high clustering coefficient, connected nodes are similar


