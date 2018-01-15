**The student clearly explains each layer of the network architecture and the role that it plays in the overall network. The student can demonstrate the benefits and/or drawbacks of different network architectures pertaining to this project and can justify the current network with factual data. Any choice of configurable parameters should also be explained in the network architecture.**

- The network architecure used consists of 5 encoder layers, a 1x1 convolution layer, and 5 decoder layers.

- Each encoder layer consists of a `seperable convolution` followed by an applied `relu` activation. The output then is normalized and fed as input to the next layer. We can consider each layer as small neural network of its own.

- We then use a `1x1 convolutional layer` to preserve the spatial information of the data, instead of using a typical `Dense` layer.

- Each Decoder layer consists of a `bilinear upsample` layer, then the output is concatenated with an encoder layer, followed by two `seperable convolution` layers.





