# Mini batch

By using the regular batch process, where all samples are used to evaluate the loss and cost, we make 1 update to the parameters W and b at each iteration (epoch)

In mini batch, we slice the training set in mini batches containing 1000 samples each.

X{t}

so that on each epoch we are able to update the parameters t times at once, where t is the number of mini-batches, this makes training faster

For every epoch, we will create (shuffle) the mini batches again. Every epoch will see all training examples.


- batch gradient descent
  - when we update the parameters using all the samples to calculate the loss and cost

- stochastic gradient descent
  - when we update the parameters using only the samples available on the mini batch



## Rules for choosing the batch size

- if m < 2000, just use the regular batch
- else, use powers of 2: 64, 128, 256, 512
- make sure that it fits into memory


v0 = 0
v1 = 5
v2 = .5*5 + .5*10 = 7.5
