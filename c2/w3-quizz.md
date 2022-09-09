# W3 - Quizz notes

- use random values for Hyperparameter search, since we don't know beforehand what's it will look like
- some Hyperparameters are more important than others
  - learning rate
  - the mini batch size
  - the beta on Momentum
- the caviar strategy should be used if possible
- we need to tune the Hyperparameters every time something changes
- when using batch normalization, we can drop b from the forward propagation since it is included in the normalization
- batch normalization helps reducing internal variance
- beta and gamma from batch normalization are variables that will the learnt / updated by the model, using any optimization method
- on tests time, we normalize the sample using mu and sigma estimated through exponential smoothing on the values seen during the training process.
