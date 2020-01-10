# Pyramid Convolutions

General idea - HVS sees luma/chroma with different frequency response.

We see luma with high precision, eg, we have many more luma sensitive cones
than we do chroma sensitive cones. Chroma added "after the fact" by the brain
by reconstructing image from luma and downsampled chroma information.

Can we do the same thing in convolutional layers? Eg, we have only one "layer",
but several filters - one which a linear combination of 1x1 convolutions, then
another one which is a low-pass of the image (a 3x3 filter), then downsampled, then
another one which is 5x5 then downsampled and so on.

This gives us several planes, each of different sizes. The big plane should capture the
low level features, the small planes the higher ones.

An interesting experiment would be to try and reproduce the color of the image eg, as a
convolutuonal autoencoder, but compressing away color information in the same way that
HVS works.
