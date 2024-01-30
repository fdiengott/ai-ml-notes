The process of using a trained neural network to make predictions on unseen data.

A neural network uses [[Forward Propagation]] to compute values. 

## Code #TensorFlow
[[TensorFlow]]
### Simple example
![[Pasted image 20231212000815.png]]
```python
import numpy as np
from tensorflow.keras.layers import Dense

x = np.array([[200.0, 17.0]])
layer_1 = Dense(units=3, activation='sigmoid')
a1 = layer_1(x) #[[0.2, 0.7, 0.3]] a 1x3 matrix

layer_2 = Dense(units=1, activation='sigmoid')
a2 = layer_2(a1) # will be a 1x1 matrix e.g. [[0.3]]

if a2 >= 0.5: # this probably needs to be keyed into
	yhat = 1
else:
	yhat = 0
```

> Dense - here is a type of layer
> a1 - the first activation values

### Slightly more complex example
```python
x = np.array([[ 0.0,...245,...240...0]])
layer_1 = Dense(units=25, activation='sigmoid')
a1 = layer_1(x)

layer_2 = Dense(units=15, activation='sigmoid')
a2 = layer_2(x)

layer_3 = Dense(units=1, activation='sigmoid')
a3 = layer_3(x)

if a3 >= 0.5:
	yhat = 1
else: 
	yhat = 0
```

### Automatic way
![[TensorFlow#Neural Network]]

