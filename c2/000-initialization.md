# Normalization

- used to train the nn faster, considering the loss function
- we normalize the data to get a more symmetric loss function
- through transforming each feature to the same scale
- its about centering the data and removing its variance
  - subtract the mean
  - divide by sigma

- use the same mu and sigma for train/dev/test

# Vanishing / exploding gradients

When we have a deep network, if using a liner activation function,
we can generalize it as

yhat = W_L * W_L-1 * W_L-2 * .... * X

if we consider W = [[1.5, 0], [0, 1.5]], soon the W**L will be very large.
if we consider W = [[.5, 0], [0, .5]], soon the W**L will be very small.

Either way, this will impact on the gradient descent, making training more difficult.

In order to prevent this, we should normalize the weights as well.

W[L] = np.random.randn(shape) * sqrt(1/n[L-1])

## Grad checking

check = ||dO_aprox - dO||_2 / ||dO_aprox||_2 + ||dO||_2

Given eps ~ e-7
if check:
  ~ e-7: good
  ~ e-5: double check
  ~ e-3: bad




# initialization

### initialization with 0

- the network never learn anything
- the network fails to break symmetry.
  - z is always 0
  - ReLU(z) = 0
  - sigmoid(z) = .5 always

### random

- it takes more iterations to get better results
- optimization is slowed down, because of the very small slope on the sigmoid for high z values


### Random + Normalization

- Xavier initialization: sqrt(1/(dim L-1))
- He initialization: sqrt(2/(dim L-1))
- works really fine:
  - learn faster
  - prevent gradient problems
  -
