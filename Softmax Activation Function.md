An activation function used in neural networks for [[Multiclass classification]] problems. Very similar to [[Logistic Regression]] except generalized for more than binary classification.  ^188035

$a_j$ is the probability, for each neuron, that y = j. $P(y=j|\vec{x})$. 
All of the activations summed up equal 1. 

$$
\begin{align}
&z_j = \vec{w_j} \cdot \vec{x} + b_j \qquad j = 1,2,...,N \\
&a_j = \frac{e^{z_j}}{\sum^{N}_{k=1}e^{z_k}} = P(y = j | \vec{x})
\end{align}
$$

^5ecf14

^07d686
## Example
$$
\begin{align}
z_1 = \vec{w_1} \cdot \vec{x} + b_1 \qquad & a_1 = \frac{e^{z_1}}{e^{z_1} + e^{z_2} + e^{z_3} + e^{z_4}}
\\
z_2 = \vec{w_2} \cdot \vec{x} + b_2 \qquad & a_2 = \frac{e^{z_2}}{e^{z_1} + e^{z_2} + e^{z_3} + e^{z_4}}
\\
z_3 = \vec{w_3} \cdot \vec{x} + b_3 \qquad & a_3 = \frac{e^{z_3}}{e^{z_1} + e^{z_2} + e^{z_3} + e^{z_4}}
\\
z_4 = \vec{w_4} \cdot \vec{x} + b_4 \qquad & a_4 = \frac{e^{z_4}}{e^{z_1} + e^{z_2} + e^{z_3} + e^{z_4}}
\end{align}
$$
All values of $a$ need to add up to 1. So if for example
$a_1 = P(y = 1|\vec{x}) = 0.30$ 
$a_2 = P(y = 2|\vec{x}) = 0.20$ and
$a_3 = P(y = 3|\vec{x}) = 0.15$ , then
$a_4 = P(y = 4|\vec{x})$  must equal 0.35 ($1 - 0.3 - 0.2 - 0.15 = 0.35$)

## Cost function

### Loss
$$
\begin{align}
a_1 &= \frac{e^{z_1}}{e^{z_1} + e^{z_2} + ... + e^{z_N}} \\
&\vdots\\
a_N &= \frac{e^{z_N}}{e^{z_1} + e^{z_2} + ... + e^{z_N}} \\
\end{align}
$$

$$
loss(a_1,...a_N, y) = \Bigg\{ 
\begin{align}
-log \;a_1 &\quad \text{if}\; y = 1\\
-log \;a_2 &\quad \text{if}\; y = 2\\
&\vdots \\
-log \;a_N &\quad \text{if}\; y = N\\
\end{align}
$$

### Cost
The average loss over all values

    $$\mathbf{1}\{y == n\} = =\begin{cases}
    1, & \text{if $y==n$}.\\
    0, & \text{otherwise}.
  \end{cases}$$
$$
\begin{align}
J(\mathbf{w},b) = -\frac{1}{m} \left[ \sum_{i=1}^{m} \sum_{j=1}^{N}  1\left\{y^{(i)} == j\right\} \log \frac{e^{z^{(i)}_j}}{\sum_{k=1}^N e^{z^{(i)}_k} }\right] \tag{4}
\end{align}
$$
> where $m$ is the number of examples, $N$ is the number of outputs. This is the average of all the losses

## #TensorFlow 

### Not optimal way 
```python
import tensorflow as tf
from tf.keras import Sequential
from tf.keras.layers import Dense
```
1. specify the model $f_{\vec{w},b}(\vec{x}) = ?$ 
```python
model = Sequential([
	Dense(units=25, activation='relu'),
	Dense(units=15, activation='relu'),
	Dense(units=10, activation='softmax'),
])
```
2. specify loss and cost $L(f_{\vec{w},b}(\vec{x}),y)$ 
```python
from tf.keras.losses import SparseCategoricalCrossentropy
model.compile(loss=SparseCategoricalCrossentropy())
```
3. Train on data to minimize $J(\vec{w},b)$
```python
model.fit(X,Y,epochs=100)
```

### Optimal way
```python
model = Sequential([
	Dense(units=25, activation='relu'),
	Dense(units=15, activation='relu'),
	Dense(units=10, activation='linear'),
])

model.compile(loss=SparseCategoricalCrossentropy(from_logits=True))
model.fit(X,Y,epochs=100)

logits = model(X) # this is now outputting z_1 ... z_10, not a_1 thru a_10
f_x = tf.nn.softmax(logits)
```

basically what it is doing is, instead of computing 
$a_j = \frac{e^{z_j}}{\sum^{N}_{k=1}e^{z_k}} = P(y = j | \vec{x})$ 
and then using that to compute $-log\;a_j$
it does 
$$
- log \frac{e^{z_j}}{\sum^{N}_{k=1}e^{z_k}} \quad \text{if}\; y=j
$$
allowing tensorflow to rearrange terms to come up with a more numerically accurate way to compute this loss function
