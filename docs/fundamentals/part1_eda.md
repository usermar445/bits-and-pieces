# Part 1: Data Science Lifecycle, EDA, Basic Libraries

## What is Data Science?
Data science today:

- Statistics & Math: statistical methods are foundation
- Computational methods: build on statistics, due to resource constraints, complex data, etc. 
- Substantive Expertise: domain knowledge

Goal: data for prediction, exploration, understanding, and intervention

## Python
**Pointers**: Python variables are pointers! Caveats when comparing

Basic data structures:

- lists (ordered and mutable)
- tuple (ordered and immutable)
- set (unordered collection of unique)
- dictionary (key: value)


## Numpy

**Why?** Python `list` flexible but inefficient (alot of unnecessary information). Numpy: efficient storage of
numerical data.

(see cheatsheet)

## Data science life-cycle

Steps involved: data preprocessing, exploration, selection, transformation, analysis, interpretation, communication

**Life-cylce**   

Consists of: 

- Problem - Plan - Data - Analysis - Conclusion

Takeaways: 

- statistics just one part
- Problem-driven: start with a question
- cycle: answers can lead to new questions

**Types of questions**  

- Descriptive: summary
- Explanatory: quantify whether holds in new sample, e.g. trends, correlations, etc. 
- Inferential: infer population state, changing average of one variable affects another
- Predictive: features to predict outcome, predictions for individuals
- Causal: average effect, changing what happens when changing average
- Mechanistic: deterministic effect


Most popular: correlaction is not causation

**Explanatory data analysis**  
Definition: process of transforming, describing, visualizing data set to better understand it, identify problems and 
inform hypothesis and subsequent analysis

Steps: 

- collect raw data
- clean and pre-process data
- describe data set
- visualize
- conclusions

## Pandas

**Advantage**: built on top on `Numpy`, but easy manipulation of labeled arrays (multiple dimensions) of heterogenuous data


**Data structures**

- Series
- Dataframe


(see cheatsheet)