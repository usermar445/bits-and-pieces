# Convolution

## Motivation
Feeding each image into network bad idea -> spacial relation lost + scales badly

Before: Extract local features + aggregate features over images + train classical models

## Convolutional Layer
Idea: "filter" that goes over the image; the more the image resembles the filter, the higher the output  
Filter "sliding" over the image

**Convolutional operator**  
$f(x,w) = x \ast w$

Local operator -> shared weights over local regions, dimensionality of $w$ much smaller, ouput same size

**Linear operator**  
$f(x, w) = x^T w$

Dimensionality $w$ same size as $x$ and one output value

**Padding**  

- zero padding: just add zeros around it
- wrap around: top goes to bottom, bottom up, etc. 
- copy: copy last lines
- reflect: mirror padding size 


sum has to be equal to 1, otherwise change volume of image


## Intuition Examples

- just 1 in the middle -> same image
- 1 on right -> shift to left
- with weight -> blur
- enhance + blur -> sharpening (but actually enhances contrast)
- negative left, positive right -> vertical edges 
- 


## Convolutional Network (Images)
-> several layers of convolutional filters, goal is to learn filters that help recognize classes

 - 2 spatial dimension, 1 channel dimension
 - convolutions: locally on spatial dimension, globally on channel dimension
 - stack multiple convolutions -> filter map


Architecture (typically): 

- number of convolutional layers (with ReLu typically)
- Usually max pooling to reduce size
- Then flatten
- Then linear layers and then softmax or sigmoid
- Loss (classification): negative log likelehood

(no detail about how backpropagation of convolutional network )

What layers learn?  

- Increase complexity, from low to high semantics
- from general objects to more class specific


## Pooling
Why? reduces amount of computations, invariance to deformations (does not reduce number of parameters)

Types: 

- average -> average of region
- stride -> sample every x pixels
- max pooling -> only keep max value of region

maintains highest activation of region -> gradient be careful: only through highest activation

--> what it does: learn interesting image parts -> convolution = detector --> filter responses

## Architecture Design

**LeNet**  
Old design 1990, only worked on letters though

**AlexNex**  
8 layers, 5 convolutional layers, 3 fully-connected layers (linear)

**Very deep networks: Google LeNet, etc. (16 layers)**  

--> but at some point adding more convolution layers did not work

**ResNet and DenseNet**  
Output of convolution added to intput itself (hypothesis: learns difference)
-> Residual connections

**Future of convolutions: Transformers**  
Takes image -> makes batches -> inputs into a transformer (self-attention: global operation with all possible pairs)

