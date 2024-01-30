Used with [[Neural Networks]].
If you don't have a lot of specific data, you can train your NN model on some large dataset that is similar, copy the model, copying over all of the weights and biases except for the last layer. The last layer will be replaced with a new number of notes and new weights and biases. 

2 options:
- only train the last layer's parameters
	- Better if your training set is really small
- train all of the parameters

The two steps of this process are:
1. supervised pretraining
	- training on a large, similar dataset
2. fine tuning
	- taking initialized parameters from pretraining and running gradient descent further

The input must be the same type for the pretraining as the fine tuning (images, audio, text, etc.)