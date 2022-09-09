# W2 - Quizz notes

### NN Notation: a[4]{3}(7)

The activations for 4th layer, the 3rd mini-batch, using the sample 7

### mini-batches

- When the mini-batch size is the same as the training size, mini-batch gradient descent is equivalent to batch gradient descent.
- Batch gradient descent uses all the examples at each iteration, this is equivalent to having only one mini-batch of the size of the complete training set in mini-batch gradient descent.
- If the mini-batch size is m, you end up with batch gradient descent, which has to process the whole training set before making progress.
- If the mini-batch size is 1, you lose the benefits of vectorization across examples in the mini-batch.
- If you’re using mini-batch gradient descent, the updates on cost will oscilate. This should not happen on regular batch gradient descent

### Gradient descent optimization

- Momentum: greater values for beta will increase the number of observations taken when averaging the values, resulting in a smoother output
- Momentum results in faster learning because it reduces the oscilation introduced by mini-batch training on the gradient descent
- Momentum is based around moving averages, which smooths out the gradient descent process
- Increasing beta makes the process more smooth, as beta increases the amount of observations that will be averaged.
- normalizing the the input data could help speeding up the training process
- ADAM optimization combines Momentum and RMSProp
