- [[Sigmoid function]]
	- values span between 0 and 1
- [[ReLU]] (Rectified Linear Unit)
	- `g(z) = max(0,z)`
	- if $z < 0$, $g(z) = 0$. If $z\geq0$, $g(z) = z$ 
- [[Linear Activation Function]]
	- `g(z) = z`
	- $a = z$
- [[Softmax Activation Function]]
	- values can take on a small number of discrete categories
	- ![[Softmax Activation Function#^5ecf14]]

## General choosing guidance
### Output layer
binary classification	
	activation='sigmoid'
regression, y can be positive/negative
	activation='linear'
regression, $y \geq 0$ 
	activation='relu'
### Hidden layer
	relu
## How to choose the best fn for the output layer
Here are some general guidelines :

If it is a binary classification problem
- Sigmoid

If it is a non-binary classification problem
- Softmax

If it is a regression problem where y can be positive or negative
- Linear activation function

If it is a regression problem where y can only be non-negative values
- ReLU

## How to choose the best fn for the hidden layers
The most common choice is the ReLU function
Why? 
- ReLU is much faster to compute than the sigmoid function
- Gradient descent works much faster on ReLU than sigmoid where there are two areas where the line is essentially flat
	- Therefore, faster learning
![[Pasted image 20231223183521.png]]

## TensorFlow #TensorFlow 
```python
import tensorflow as tf
from tf.keras.layers import Dense

model = Sequential([
	Dense(units=25, activation='relu'),
	Dense(units=15, activation='relu'),
	Dense(units=1, activation='sigmoid') # or linear, or relu
])
```