# Network Architectures

## ResNet
-> contain residuals, e.g. adding intput together with output of layer ("skipping" layers)

## Convolution Network
with convolutions

## Recurrent Network
For sequential input, have cyclicel loops, adding output of a layer to the input of next

Shared parameters

But problem: cannot process in parallel (slow) and e.g. long sentences, foget beginning of word 

## Transformers
Encoder + Decoder 

Encoder generates attention

Decoder handles tasks

Key: Self-attention

Takes whole input and then adds output to input again

Can be used for any task, as long as sequentially

## BERT
Language-processing network based on transformer architecture

Stacking Encoders on each other

## GPT
Stacking Decoders