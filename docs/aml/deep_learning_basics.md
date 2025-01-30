# Deep Learning Basics

## Essentials

In the ML pipeline: forget about the features (data + labels)

"Definition:" a family of

- parametric, non-linear, hierarchial represetation learning functions
- massively optimized with stochastic gradient descent
- to encode domain knowledge



## History of Deep Learning

- 1958 Perceptron: Only linear classification, Convolution networks, recurrent networks
- 1970s/80s AI winter -> due to overhype -> but important discoveries (backpropagation)
- 2012 Deep learning revolution (Imagent -> classification)
- 2015 Resnet
- 2017 Go, Deepmind

Why new AI hype?

- before computationally too expensive
- new hardware: especially GPU + storage
- availability of huge amounts of training data (+ storage)
- open source software -> community shares
- Tricks
- Deep learning beyond recognition

## Perceptron

- single layer perceptron for binary classification
- each input one weight, multiply input with wight, sum, add bias, if result larger than threshols 1, otherwise 0

Algorithm: 

- initialize weights randomly
- take one sample and predict label
- if erroneous, update weights (increase weights if prediction = 0 and label 1, otherwise decrease)
- repeat until no errors

Problem: only used for linear seperably problems (e.g. counterexample: XOR function)

## Multi-layer perceptron (MLP)
Multiple layers: solves problem of single layer perceptron (only linear seperably problems)

Basic steps: 

- Forward pass: Maps intput to predicts output
- Calculate loss: compare predicts value to ground truth
- Backpropagation: propagate error back through the network to update weights (propagating gradients)

Crucial point: **activation function**

- after each layer: activation function
- transforms the output of each layer -> makes each layer a *non-linear* function
- otherwise: not learning anything (combination of linear functions still a linear function)

## Example MLP


## Acitvation functions*
**Sigmoid $\sigma(z) = \frac{1}{1+e^{-z}}$**

Advantage:

- Range (0,1) -> bounded (advantage, depends on application)
- Differentiable: $\frac{d}{dz} \sigma(z) = \sigma(z) (1- \sigma(z)$ -> easily defined, pleasing math (advantage)

Problem: 

- Gradient always smaller than signal -> vanishing gradient problem


**ReLu $R(z) = max(0, z)$**

- Range [0,inf )-> unbounded
- Differentiable: $\frac{d}{dz} R(z) = 1$ if $z\leq 0$, 0 otherwise

Advantages:

- easy to implement
- strong gradient signal

ReLu often used because on a grand scale, sigmoid is almost linear, whereas ReLu is very non-linear


**Softmax**
used for multi-class classification

## Hyperparameters

- number of layers
- number of parameters per layer
- number of training iterations
- Learning rate for stochastic gradient descent
- Regularization weight

Many more, have large effect, hard to give rules. 

## Tricks

- Dropout -> randomly leave out neurons; not learn bias that is in data, e.g. learn classify cats, examples of sofa-> avoid coadaptation -> prevent over-fitting -> 
- Mixup -> a way of "generating" more data -> creates a more robust network -> improves classification a bit but mostly tasks that are not normal
- Batch normalization -> after each layer, re-normalize 
- Class separation






