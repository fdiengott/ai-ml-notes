#TensorFlow 
## Data
TensorFlow only handles matrices, not vectors
```python
x1 = np.array([[200, 17]]) 
x2 = np.array([[200], 
			  [17]]) 
x3 = np.array([200, 17]) # 1d vector
```
$$
\begin{align}
x1: [200, 17] \\
x2: 
	\begin{bmatrix}
	200 \\
	17
	\end{bmatrix}
\end{align}
$$

$x1$ is a row vector
$x2$ is a column vector
$x1$ and $x2$ are matrices, where as $x3$ is a vector with no rows or columns

## Loss functions
```python
from tensorflow.keras.losses import BinaryCrossentropy

model.compile(loss=BinaryCrossentropy())
# L = -y*np.log(f_x) - (1 - y)*np.log(1-f_x)


from tensorflow.keras.losses import MeanSquaredError

model.compile(loss=MeanSquaredError())
```

## Neural Network

```python
layer_1 = Dense(units=3, activation='sigmoid')
layer_2 = Dense(units=1, activation='sigmoid')
model = Sequential([layer_1, layer_2])

# usually written more implicitly
model = Sequential([
	Dense(units=3, activation='sigmoid'),
	Dense(units=1, activation='sigmoid'),
])

model.compile(...)
model.fit(x,y)
mode.predict(x_new) # forward propagation
```

### x and y data passed to TensorFlow
```python
x = np.array([[200.0, 17.0], # a matrix
			  [120.0, 5.0],
			  [425.0, 20.0]])
y = np.array([1,0,0]) # a simple array
```

## Larger Example
```python
model = Sequential([
	Dense(units=25, activation='sigmoid'),
	Dense(units=15, activation='sigmoid'),
	Dense(units=1, activation='sigmoid'),
])
model.compile(...)

x = np.array([[...],
			  [...],
			  ...
])
y = np.array([...])
model.fit(x,y)
model.predict(x_new)
```

## Normalization 
![[Feature Scaling#TensorFlow TensorFlow]]

## Viewing model info
```python
model = Sequential([
	Dense(3, activation='sigmoid', name='layer1'), 
	Dense(1, activation='sigmoid', name='layer2'),
])

model.summary()

w1,b1 = model.get_layer('layer1').get_weights()
w2,b2 = model.get_layer('layer2').get_weights()
```

### Optimizations/variations
```python
model.compile(
	loss = tf.keras.losses.BinaryCrossentropy(),
	optimizer = tf.keras.optimizers.Adam(learning_rate=0.01)
)

model.fit(
	x_tiled, y_tiled,
	epochs=10
)
```

## Neural networks
use the `nn` class functions
```python
import tensorflow as tf

model.compile(loss=SparseCategoricalCrossEntropy(from_logits=True))
model.fit(X,Y,epochs=100)

logits = model(X) 
f_x = tf.nn.softmax(logits)
```

SparseCategorialCrossentropy
- expects the target to be an integer corresponding to the index. For example, if there are 10 potential target values, y would be between 0 and 9. 
CategoricalCrossEntropy
- Expects the target value of an example to be one-hot encoded where the value at the target index is 1 while the other N-1 entries are zero. An example with 10 potential target values, where the target is 2 would be [0,0,1,0,0,0,0,0,0,0].