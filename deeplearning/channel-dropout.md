# Channel Dropout

Basically like regular dropout, but instead of applying it to activations,
apply it to channels in a CNN.

In principle this should make you more robust to features, allowing you
to incrase the number of filters without overfitting.

This was done in this[0] CVPR paper but I've not seen it cited anywhere. Would
be interesting to try it on some common CNN architectures.

[0] http://openaccess.thecvf.com/content_cvpr_workshops_2015/W03/papers/Huang_Channel-Max_Channel-Drop_and_2015_CVPR_paper.pdf
