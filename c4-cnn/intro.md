# Convolutional Neural Networks

- filters for edge detection
  - can be learnt from the samples, as if they were weights
  - new size = h - f + 1

- padding: adding more pixels on the borders of the image, creating new borders
  - new size: n + 2p - f + 1
  - prevents shrinking
  - prevents loosing information on the original edges
  - valid: no padding
  - same: the output image has the same size as the input
    - p = (f-1)/2

- stride: how many pixels we should squid between convolutions?
  - new size: 1 + (n + 2p -f)/s
- volume: considering the colors, the image dimensions are x,y,3 - the filters in this case will also be x3, but the resulting matrix will be x1

- pooling layers: almost like a filter but without parameters. It aggregates data: max, min, mean

Why use convolutions:

- without convolutions, a small image (32x32x3) would require 3072 weights on the first layer x at least the same amount at the second layer, leading to +14M parameters to be learnt.
- with convolutions, we need to learn the parameters for the filters instead, leading to a much smaller set of parameters to be learnt.
