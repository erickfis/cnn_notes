# Classification with localization

We need to output

    bx, by, bw, bh, class label

y = [pc, bx, by, bh, bw, c1, ..., cn]

- bounding box
- landmarks

## Sliding windows detection

Striding a window through the image, trying to classify
a closely cropped object. Then, increment the window size and repeat.
