# Classic Networks

# LeNet-5

- input 32x32x1 (hand writter digits)
- conv layer f=5, c=6, s=1 (156 parameters)
- avg pooling f=2, s=2
- sigmoid
- conv layer f=5, c=6, s=1 (156 parameters)
- avg pooling f=2, s=2
- sigmoid
- conv layer f=5, c=16, s=1 (416 parameters)
- avg pooling f=2, s=2
- sigmoid
- fully connected layer, 120 neurons (120x416 = 49920)
- fully connected layer, 84 neurons (120x84 = 10080)
- output layer (sigmoid)
- ~ 60k parameters

## AlexNet

- input 227x227x3
- conv layer f=11, c=96, s=4
- max pooling f=3, s=2
- conv layer f=5, c=256, s=1, same
- max pooling f=3, s=2
- conv layer f=3, c=384, s=1, same
- conv layer f=3, c=384, s=1, same
- conv layer f=3, c=256, s=1, same
- max pooling f=3, s=2
- fc 9216
- fc 4096
- fc 4096
- fc softmax

## VGG - 16

- input 224x224x3
- 2x conv 64, f=3, s=1, same,
- max pooling f=2, s=2
- 2x conv 128, f=3, s=1, same,
- max pooling
- 3x conv 256, f=3, s=1, same,
- max pooling
- 3x conv 512, f=3, s=1, same,
- max pooling
- 3x conv 512, f=3, s=1, same,
- max pooling
- fc 4096
- fc 4096
- softmax 1000

## Inception

1x1 filters
