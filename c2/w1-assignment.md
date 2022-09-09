# W1 assigment notes

- for high count of samples (> E06), the train/dev/test split should be
  - .99 / .05 / .05


- adding more samples from a different distribution to one set (train or test) could be harmful

- for high bias (underfitting to train set)
  - increase the number of hidden units in each layer
  - make a deeper NN


- for high variance (overfitting on train set)
  - use more regularization (increase lambda)
  - get more training data


- for high bias and variance
  - use a bigger network, the model is not learning as it is


- Dropout
  - using it is the default for computer vision
  - however, for NN do not use it if there is no overfitting
  - we do not apply it at the test time


- Vanishing gradients
  - normalize weights
  - use Xavier initialization

- normalizing data is important
  - training is faster
