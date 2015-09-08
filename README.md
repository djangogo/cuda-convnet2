Note July 18, 2014:

I've released an update to cuda-convnet, called cuda-convnet2. The two main new features are faster training on Kepler-generation GPUs and support for multi-GPU training.
This is a fast C++/CUDA implementation of convolutional (or more generally, feed-forward) neural networks. It can model arbitrary layer connectivity and network depth. Any directed acyclic graph of layers will do. Training is done using the back-propagation algorithm.

Fermi-generation GPU (GTX 4xx, GTX 5xx, or Tesla equivalent) required.

Documentation
Compiling -- how to check out and compile this code.
Data -- what kind of data this net can train on.
LayerParams -- how to specify an architecture for the net.
NeuronTypes -- types of hidden unit nonlinearities.
TrainingNet -- how to train the net.
Options -- the command-line arguments that the net takes.
ViewingNet -- how to look inside the checkpoints saved by the net.
CheckingGradients -- how to numerically test the gradients for correctness.
Fast results
11% error on CIFAR-10 in 75 minutes, with image translations and horizontal reflections (def, params).
13% error on CIFAR-10 in 25 minutes, with image translations and horizontal reflections (def, params).
See Methodology for details of training.
Filters learned by this net:

18% error on CIFAR-10 in 20 minutes, without any image translations/transformations/preprocessing (def, params).
26% error on CIFAR-10 in 80 seconds, without any image translations/transformations/preprocessing (def, params).
Recent changes
Jul 17, 2012
Fixed bug in contrast normalization backpropagation code which caused wrong gradients to be computed near image borders. (Thanks Hannes Schulz).
Mar 13, 2012
Added response-normalization across maps layer.
Started modifying the code to support rectangular (i.e. non-square) images. The convolution code now supports rectangular images, but the remaining code does not yet. So the whole package still requires square images.
Feb 8, 2012
Most layer types now should work well with minibatch size 64 or 32.
Fixed --conserve-mem option so it can be combined with -f (i.e. its value can be changed after a net has been saved).
See ChangeLog for older changes.
Features
Supported layer types:
Layers with weights:
Fully-connected
Convolutional, including sparsely-connected convolutional
Locally-connected, unshared
Others:
Local pooling (avg, max), including overlapping pooling regions
Local response normalization
Local contrast normalization
Softmax
Elementwise sum, elementwise max
Gaussian blur + "bed of nails" subsampling
Resize with bilinear filtering
Supported neuron activation functions:
Logistic
Hyperbolic tangent
Rectified linear
Others
Supported objectives:
Logistic regression
Sum-of-squares
Other features:
Efficient implementation of convolution in CUDA.
Supports arbitrary stride size at zero loss of efficiency (except that which comes from reducing the problem size).
Implicitly pads your images with an arbitrary-sized border of zeros without using any extra memory.
Supports block-random sparse connectivity at no performance cost (see LayerParams).
Modular design makes it easy to add new layer types, neuron activation functions, or objectives if you should need them.
Mostly avoids use of temporary memory where it isn't strictly needed.
Optimizes multiple objectives simultaneously.
Saves checkpoints to disk as python pickled objects, so you can write python scripts to probe the mind of your neural net.
Capable of training on one batch of data while simultaneously loading the next from disk (or pre-processing it in some way, if necessary).
Numerically tests gradient computations for correctness.
Contact
My university web page
My email
Acknowledgements
I am grateful to Ilya Sutskever for suggestions that led to many of the features in this package.
