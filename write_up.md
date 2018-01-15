**The student clearly explains each layer of the network architecture and the role that it plays in the overall network. The student can demonstrate the benefits and/or drawbacks of different network architectures pertaining to this project and can justify the current network with factual data. Any choice of configurable parameters should also be explained in the network architecture.**

- The network follows a `Fully Convolutional` architecure consisting of 5 encoder layers, a 1x1 convolution layer, and 5 decoder layers. The reason for using an `FCN` rather than a normal `CNN` followed by a `Fully connected` layer and a softmax activation funciton, is that we need to find out WHERE an object is in an image, rather than just WHICH object is it, i.e: classification.

- Each encoder layer consists of a `seperable convolution` followed by an applied `relu` activation. The output then is normalized and fed as input to the next layer. We can consider each layer as small neural network of its own.
The encoder stage is used for capturing the important features, with each deeper layer capturing more complex shapes than the one before it. The first layer could for example capture curvers, the one after could then capture a collection of curves that form a circle.

- We then use a `1x1 convolutional layer` to preserve the spatial information of the data, instead of using a typical `Dense` Layer or `Fully Connected` Layer

- Each Decoder layer consists of a `bilinear upsample` layer, then the output is concatenated with an encoder layer, followed by two `seperable convolution` layers. Those are used to upsample the data to higher resolutions.







