# L2 regularization intuition

- adds L2 regularization cost to the cost J

    J = cross-entropy cost + L2 regularization cost

    L2 = (Sum_l Sum_w^2) * lambda / (2m)

- we need to update the cost and the grads as well

    dW3 = 1./m * np.dot(dZ3, A2.T) + W3*lambda/m


- we can tune lambda on the dev set
- a model with small weights is simpler than otherwise, thus preventing overfitting
- a large lambda will turn W close to zero, thus simplifying the hidden units by making them closer to a linear function
- when lambda is large, z is small and g(z) will be linear, when considering tanh(z) as the activation funtion
- when plotting J as a function of the number of iterations, remember to use the new J equation

# Drop out regularization

For every layer, random chose nodes to be removed, ending up with a smaller network.

This is important because each neuron/node learns to be less dependent on the neurons of the previous layer.

We can implement it as a mask: a matrix of 0s and 1s, to be used to mask A



## Inverterd dropout


dropL = np.random.randn(shape) < keep_prob

aL = aL * dropL
aL = aL / keep_prob

- for different samples, we use a new dropout matrix, to remove different units
- for different iterations, we also use a new dropout matrix, to remove different units
- dont apply it at test time, otherwise we will just add noise
- we can use different keep_prob for each layer
- down side: we cannot measure cost

## intuition

By removing nodes at random on layer L-1, we avoid having too much weigh on a particular node at layer L for any special node at layer L-1

In pratice, it shrinks weights at layer L

## Other methods of regularization

- data augmentation: flipping, rotating, croping, zooming, distorting, to get more free training samples
- early stopping: plot cost for trainning and dev set at the same time. Stop iterating when the cost for the dev set start to rise. Downside: disturbs the eforts for tunning parameters,
