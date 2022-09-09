# Tunning

- don't use grids to explore hyper parameters
- rather, use random values
- Coarse to fine: zoom/focus on a region


## Scale for searching parameters

- in some cases (l, L) it is ok to explore a linear space
  - from 5 to 10 hidden layers l
  - from 2 to 6 layers L
  - usually for discrete values
- in other cases, however, it is best to use log scale
- learning rate:
  - instead of exploring from .0001 to 1 evenly,
  - use the log scale: E-4, E-3, E-2, E-1, E-0


## Trying different parameters

- pandas approach: babysitting one model
- caviar approach: spamming multiple machines to train different models in parallel

## Batch normalization

- makes hyper parameter searching easier
- we saw that normalization for the input features helps the learning process
- lets do it for the output of the linear functions of each neuron on every hidden layer


    z_norm = z - mi / sqrt(sigma^2 + epsilon)
    z_til = gamma * z_norm + beta

### Intuition

We fit a liner model to data. If the distribution changes, the fit will stop working as expected.

On hidden layers, every time we update the parameters W,b, the output of the activation function changes,
thus rendering the linear model on the next layer obsolete.

However, we can mitigate this problem by making sure that at least this new distribution will have mean 0 and variance 1.

### Side effect

Because the normalization happens on each mini batch, we will introduce noise to the process.

This will act as regularization.

The bigger the size of the mini batch, the less regularization will be observed. 
