**The student clearly explains each layer of the network architecture and the role that it plays in the overall network. The student can demonstrate the benefits and/or drawbacks of different network architectures pertaining to this project and can justify the current network with factual data. Any choice of configurable parameters should also be explained in the network architecture.**

- The network follows a `Fully Convolutional` architecure consisting of 5 encoder layers, a 1x1 convolution layer, and 5 decoder layers. The reason for using an `FCN` rather than a normal `CNN` followed by a `Fully connected` layer and a softmax activation funciton, is that we need to find out WHERE an object is in an image, rather than just WHICH object is it, i.e: classification.

- Each encoder layer consists of a `seperable convolution` followed by an applied `relu` activation. The output then is normalized and fed as input to the next layer. We can consider each layer as small neural network of its own.
The encoder stage is used for capturing the important features, with each deeper layer capturing more complex shapes than the one before it. The first layer could for example capture curvers, the one after could then capture a collection of curves that form a circle.

- We then use a `1x1 convolutional layer` to preserve the spatial information of the data, instead of using a typical `Dense` Layer or `Fully Connected` Layer

- Each Decoder layer consists of a `bilinear upsample` layer, then the output is concatenated with an encoder layer, followed by two `seperable convolution` layers. Those are used to upsample the data to higher resolutions.


Each of those were implemented in their respective functions provided by the starter code, undert he `TODO`s


#add model architecture#

**The student explains their neural network parameters including the values selected and how these values were obtained (i.e. how was hyper tuning performed? Brute force, etc.) Hyper parameters include, but are not limited to:**


- learning_rate = 0.005
In the classroom, it was mentioned that low learning rates converge better than high learning rates, although they are slower. 

- batch_size = 48
According to what Vincent said in the lectures about `SGD` and normal `gradient descent` it makes sense (to me at least) that trying to optimize the parameters of,for example, the whole data set at the same time, would be better since every input has a voice, thus we are able to have a democary and reach better weights. Using `SGD` although minimizes that for the favor of speed, i found it logical to have a batch size also high, following the logic stated above.

- num_epochs = 20
Monitoring the plotted losses each time i trained the network, i noticed that it was not necessary to have a high number of epochs (although it may be necessary for other cases) as the losses reached satisfactory levels relatively early.


Those remaining three parameters were left as was recommended, except number of workers was increased asi was training on a AWS instance, which had enough processing power and good hardware.

- steps_per_epoch = 200
- validation_steps = 50
- workers = 4



**The student demonstrates a clear understanding of 1 by 1 convolutions and where/when/how it should be used.**

1 x 1 convultions are used instead of FC layers because they preserve the spatial information of the image, which is important to us, since we not only are interested in classifying the object of interest, but also its location in the image.

**The student demonstrates a clear understanding of a fully connected layer and where/when/how it should be used.**

Fully connected layers should be used when the spatial information is to be disregarded and when we are only interested in the classification of an object.


**The student is able to clearly articulate whether this model and data would work well for following another object (dog, cat, car, etc.) instead of a human and if not, what changes would be required.**

The model would not work well on any other object, since it was only trained to recognize the hero in the red outfit. In order to make it do so, retraining from scratch with appropriate relevant classified data to the target would be used. Another idea would be to freeze the weights of for example the first four or five layers and only retrain the fifth and the 1x1 convolution layer. As the early layers contain basic geometries and nothing very specific.




**Data used**

Udacity default provided dataset


During the early trials, i designed a small network, which could not give me good results, but after searching through slack and getting some advice, i implemented a deeper network, which increased the accuracy tremendously using only the provided dataset


**Future improvements**

- Adding manually connected good data
- Experimenting with already successful network architectures such as AlexLeNet and Vgg


