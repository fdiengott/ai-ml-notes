See also [[Backpropagation]]
The below is an implementation [[Logistic Regression]] with tensorflow
## #TensorFlow 
```python
import tensorflow as tf
from tensorflow.keras import Sequential
from tensorflow.keras.layers import Dense

model = Sequential([
	Dense(units=25, activation='sigmoid'),
	Dense(units=15, activation='sigmoid'),
	Dense(units=1, activation='sigmoid'),
])

from tensorflow.keras.losses import BinaryCrossentropy

model.compile(loss=BinaryCrossentropy())
model.fit(X,Y,epochs=100) # number of steps in gradient descent
```
### More optimal way to reduce numerical rounding errors
```python
model = Sequential([
	Dense(units=25, activation='sigmoid'),
	Dense(units=15, activation='sigmoid'),
	Dense(units=1, activation='linear'),
])

model.compile(loss=BinaryCrossentropy(from_logits=True))
model.fit(X,Y,epochs=100)
logit = model(X) # this outputs the z's instead of a's, so need to be mapped 
f_x = tf.nn.sigmoid(logit)
```
## Details
### Steps generally
1. specify how to compute the output given the input x and params w, b 
	ex. 	
		`z = np.dot(w,x)`
		`f_x = 1 / (1+np.exp(-z)`
2. Specify loss and cost
	ex. 
		Logistic loss `loss = -y*np.log(f_x) - (1-y)*np.log(1-f_x)`
3. Train on data to minimize $J$
	ex. gradient descent: `w = w-alpha * dj_dw`

### Neural Network steps
1. ```model = Sequential([Dense(...), Dense(...), Dense(...)])
2. `model.compile(loss=BinaryCrossentropy())`
3. `model.fit(X,y,epochs=100)`
	1. this is doing backprop

###  Adding regularization
```python
# 0.01 here is lambda
layer1 = Dense(units=25, activation="relu", kernel_regularizer=L2(0.01))
layer2 = Dense(units=15, activation="relu", kernel_regularizer=L2(0.01))
layer3 = Dense(units=1, activation="sigmoid", kernel_regularizer=L2(0.01))
model = Sequential([layer1, layer2, layer3])
```