# Structuring ML Projects

## Metrics

- orthogonalization: switches that changes independent things
  - we need a single evaluation metric: more than one metric expands the choices and tradeoffs we have to decide
- optimize one metric, satisfice the others
  - satisficing metrics will have thressholds
  - the optimizing metrics is unbounded


## Preparing train / dev / test sets

- ensure all sets cames from the same distribution
- Rules of thumb:
  - up to 10,000 samples: 60, 20, 20%
  - more than 1,000,000: 98, 1, 1%

- if more samples came in, use then on train set, because it is not a problem when train and dev set are from different distributions. It is a problem if dev and test are. Also, adding more samples to test could harm the project because the test set must reflect the reality we will see in production

## Human level performance

- Bayes error: the best possible error. In some cases, the human error is a proxy of the bayes error.
- Avoidable bias: the difference between bayes error and train error
- We should not get better results than the bayes error, that would be overfitting
- to define HLP, consider the level of specialists on the subject
- We should act where the biggest gap is:
  - between bayes error and train error: bias
  - between train and test sets: variance


## Error analysis

- if error on train/dev >> HLP, train a bigger model, try different parameters
- if dev >> test, increase the size of the dev set
But we can do error analysis:

- take 100 missclassified samples from dev set
- manually count how many are class X
- tabulate problems
- if problem X > 50%, go for it
  - but also take cost and difficulty into consideration
- check error on train/dev/test and compare to bayes error, to understand whether we should act to fix avoidable bias (error on train) or variance (error on dev set)
-

### Incorrectly labels on training set

- Deep Learning is robost to random errors on the training set, but no to systematic errors
- if you decide to fix label errors on dev, do it on test set as well


### Train set is from a different distribution

- create a new training-dev set, using part of train, so it will have the same distribution
- if error on train-dev >> train, then we do have a variance problem
- if error on train and train-dev are close but error on dev is much larger, then we have a data mismatch problem

### Rule of thumb

- check for human level error vs train error to determine the avoidable bias
- check the dev error
- if dev >> train, create a train-dev subset to understand whether train and dev are from the same distribution
- if train << train-dev, we have variance problem
- if dev >> test, data mismatch


## Data mismatch

- when we have train/train-dev error >> dev/test error
- happens when we introduce more samples from a different distribution to the train set 
- try to understand the differences between train/dev/test by manually looking at samples
- measure human level error on each set
- if they are from a different distribution,
  - try getting more data, to make the sets more similar
  - try creating syntetic data
    - add it to train set


## Transfer learning

- when we have a lot of data on task A and not a lot on task B, we can use transfer learning to do a better job on task B
- take all layers and optimezed weights from model A, except the output layer
- use the data on task B to train the output layer
- adding more layers on to of the transfer is an option
- the idea is to use the basics about the problem, learnt on task A, and apply it on task B, the low level features
  - basics of how human voice sounds like
  - basics of image detection (edges)


Only appliable when:

- task A and task B have the same input
- we have a lot more data on task A than task B, but we want to predict on task B

## Multitask

Build one deep NN for N classes, but dont use the softmax actvation layer.

Makes sense when:

- each class has only a few samples
- but when combined, the dataset is a lot larger
- each task benefits from learning the basic, low level features available on every sample
- if a sample is not fully labelled, we still can use it to train the model. We just need to ignore those samples when calculating the loss function


## End-to-end deep learning

Historically, people have been splitting problems into smaller problems,
intermediary steps.

End-to-end is about aiming at the final goal in one step only.

Pro: we don't need to hand-design any intermediary feature
Con: it needs a big dataset
