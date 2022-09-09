# Deep Learning

Coursera - 2022-01-17


## Basic Concepts

- Neuron: applies a function to input data. Computes a function and then an activation function.
- ReLu: Rectified Linear - output is zero until some threshold, then we have the linear function
- Neural networks: a stack of neurons, containing the input layer, the hidden layers and the output.
- On densily connected networks, every neuron will receive all the features, and it is up to the NN figure out which are the best features by itself.
- structured data: tabular data
- unstructured data: audio, images, text

## Types of NN

- standard: classification, regression
- Convolutional NN: image classification, photo tagging
- Recurrent NN: speech recognition, machine translation, NLP
- Images and radar info: custon hybrid

## Scale - why are NN taking off?

- for smaller datasets, usually the model performance depends on feature engeneering and machine learning could perform better than NN
- for larger datasets, NN tend to perform better
- the more data, the better performance a NN will achieve - but this relies on the size (layers) of the NN.
- The bigger the NN, more time it takes to train
- switching from sigmoid to ReLu makes the gradient descent functions faster


## Conventions

- m: size of the dataset
- n: number of features
- X: matrix where every sample from the dataset is represented in one column
- X.shape = (n, m)
- Y.shape = (1, m)

## Cost function

- squared error doesn't work well with the gradiend descent
- Loss function: applyies to one sample
- L(yhat, y) = -(y.log(yhat) + (1-y).log(1-yhat))
- Cost function applies to the dataset
- J(w, b) = mean(L)

## Gradient descent

Given yhat = sigma(wx + b),  find w and b in order to minimize J(w, b)

We will updated w[i] and b as follows:

w[i] := w[i] - alpha*dJ/dw
b: = b - alpha*dJ/db

## Foward and backwards propagation

Forward propagation is about following the regular computation graph, from left to right, to compute the outcome of a function, i.e. a logistic regression.

Backward propagation is about following the computation graph backwards in order to calculate the derivatives of the function.
This is required in the gradient descent process.


## Common steps for pre-processing datasets:

- figure out dimensions and shapes
- reshape every sample to a vector (flatten)
- standardize the data
