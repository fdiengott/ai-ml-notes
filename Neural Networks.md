#architectures
An ML architecture made up of layers of neurons to [[Neural Network inference|predict values based on inputs]]. It uses [[Forward Propagation]] to compute values after it has been trained. 

For training see [[Neural Network Training]].

Neural networks basically do logistic regression on a number of (hopefully) better features than the ones provided (the ones that are computed through the layers).

A neural network does automated [[Feature Engineering]] by allowing the neurons to train and figure out which features we should do logistic regression on. 

The makeup of the neural network is called the [[Neural network architecture]] (i.e. the number of layers and neurons in each layer). 

A neural network is sometimes called a [[Multilayer perceptron]]. 
## Terminology 
**Neuron** - a function that takes in some numerical inputs, and outputs one or more numerical outputs which we call **activations**
**[[Neural Network Layer|Layer]]** - group of neurons

**Input layer** - first layer. Denoted as either $\vec{x}$ or $\vec{a}^{[0]}$ 
**Output layer** - Final layer
Each layer is notated with a superscript $[i]$ (e.g. $\vec{a}^{[2]}$ )
## Example with 1 layer
$$
\vec{x} \rightarrow \text{hidden layer} \rightarrow \vec{a}
$$
> $\vec{x}$ - input layer
> $\vec{a}$ - activations

