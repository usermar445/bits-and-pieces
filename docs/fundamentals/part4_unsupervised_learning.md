# Part 4: Unsupervised Learning

## PCA
Method to summarize high-dimensional data with lower number of dimensions. Challenge: how to reduce dimensions
with the least information loss. 

**Method**  
Find dimension along which the least information is lost (preserve variability in data).

Maximize variance of centered and projected data.

Components are orthogonal, then repeat process. 

**Scree plot**  
Plots proportion of variance explained vs. number of pc. Tool to choose how many dimensions should be considered.

## K-Means
**Method:** Find partition in data such that the distance/dissimilarity between points in the same cluster 
is minimized. Problem: hard to optimize. 

**Algorithm**  

1. Randomly assign cluster to each data point from $1...K$
2. a) for each cluster calculate centroid ($p$ feature means vector for each cluster), b) assign each cluster to the centroid that is closest

Problem: not guaranteed to find optimal solution + results depend on initial conditions

**Challenges**  

- creates linear boundry (not all datapoints are linearly separable
- choose $K$ often not trivial
- depends on initial conditions


## Community Detection
**Method:** maximize modularity, i.e. maximize in-community links compared to a random network

**Algorithm:**

- Initially, all nodes in separate community
- repeat: a) calculate increase in modularity for each pair of communities, b) join communities that lead to higher gain of modularity
- Select partition that maximizes modularity



