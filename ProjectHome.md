This is an update to [cuda-convnet](https://code.google.com/p/cuda-convnet/). **Update**: this project is being moved to GitHub, since Google Code is shutting down. [Click here](https://github.com/akrizhevsky/cuda-convnet2) for the GitHub project.

This project has three major new features relative to cuda-convnet:
  1. Improved training times on Kepler-generation Nvidia GPUs (Geforce Titan, K20, K40).
  1. Multi-GPU training support implementing data parallelism, model parallelism, and the hybrid approach described in [One weird trick for parallelizing convolutional neural networks](http://arxiv.org/abs/1404.5997).
  1. Less-polished code and incomplete (but improving) documentation.

# Documentation #
## Usage ##
  * [Compiling](Compiling.md) -- how to compile the code
  * [Data](Data.md) -- how to generate training data
  * [TrainingExample](TrainingExample.md) -- how to train an example network
  * [LayerParams](LayerParams.md) -- how to specify a custom network
  * [MultiGPU](MultiGPU.md) -- how to train multi-GPU networks
  * [ShowNet](ShowNet.md) -- how to look inside trained networks

## Reference ##
  * [Arguments](Arguments.md) -- listing of command-line arguments
  * [NeuronTypes](NeuronTypes.md) -- listing of supported neuron activation functions
  * [LearningRates](LearningRates.md) -- listing of supported learning rate schedules

# Contact #
  * My [email](mailto:akrizhevsky@gmail.com)

# Contributions #
  * This code includes contributions by Anker Guo of the [Tencent BestImage team](http://bestimage.qq.com/):
    * 50% acceleration of batch-32 convolution kernels; 10% acceleration of batch-128 convolution kernels.