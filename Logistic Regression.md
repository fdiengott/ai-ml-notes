Most common logistic regression algo.

Y-axis is 0 or 1. 

Uses the [[Sigmoid function]] / logistic function
$$
\begin{align}
z &= \vec{w} \cdot \vec{x} + b \\
g(z) &= \frac{1}{1 + e^{-z}} \\
f_{\vec{w}, b}(\vec{x}) &= g(\vec{w} \cdot \vec{x} + b) = \frac{1}{1 + e^{-(\vec{w} \cdot \vec{x} + b)}}
\end{align}
$$

Outputs the probability that the class outputted is 1 (e.g. if outputs 0.7, there's a 70% chance that y is 1)

sometimes denoted as 
$$
f_{\vec{w}, b}(\vec{x}) = P(y =1|\vec{x};\vec{w},b)
$$
The probability that y is 1, given input $\vec{x}$, parameters $\vec{w},b$ 

## Cost Function 

### Loss Function
To get the loss for one training example we use the [[Logistic Loss Function]]
$$
L(f_{\vec{w},b}(\vec{x}^{(i)}, y^{(i)})) = \Biggl\{ 
\begin{align}
-log(f_{\vec{w}, b}(\vec{x}^{(i)})) \quad if \; y^{(i)} = 1 \\
-log(1 - f_{\vec{w}, b}(\vec{x}^{(i)})) \quad if \; y^{(i)} = 0
\end{align}
$$
In one equation
  $$
  loss(f_{\mathbf{w},b}(\mathbf{x}^{(i)}), y^{(i)}) = (-y^{(i)} \log\left(f_{\mathbf{w},b}\left( \mathbf{x}^{(i)} \right) \right) - \left( 1 - y^{(i)}\right) \log \left( 1 - f_{\mathbf{w},b}\left( \mathbf{x}^{(i)} \right) \right)
  $$

Or more simply
$$
L(f^{(i)}, y^{(i)}) = -y^{(i)}log(f^{(i)}) - (1 - y^{(i)})log(1 - f^{(i)})
$$
### Cost #cost-functions 
$$
J(\vec{w}, b) = -\frac{1}{m}\sum_{i=1}^m[y^{(i)}log(f^{(i)}) + (1 - y^{(i)})log(1 - f^{(i)})]
$$
#### Regularized
$$
J(\vec{w}, b) = -\frac{1}{m}\sum_{i=1}^m\Big[y^{(i)}log(f^{(i)}) + (1 - y^{(i)})log(1 - f^{(i)})\Big] + \frac{\lambda}{2m}\sum_{j=1}^{n} w_j^2
$$

## [[Gradient descent]]
$$
\begin{align}
w_j &= w_j - \alpha \frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)})\; x_j^{(i)}\\
b &= b - \alpha \frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)})
\end{align}
$$

Same as linear regression except that $f(x)$ is the [[Sigmoid function]], 
$$
f_{\vec{w},b}(\vec{x}) = \frac{1}{1 + e^{-(\vec{w}\cdot \vec{x} + b)}}$$
### Regularized
we don't regularize $b$ 
$$
\begin{align}
w_j &= w_j - \alpha \frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)})\; x_j^{(i)} + \frac{\lambda}{m}w_j\\
b &= b - \alpha \frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)})
\end{align}
$$

## Scikit-learn

```python
import numpy as np
from sklearn.linear_model import LogisticRegression

x = np.array([...])
y = np.array([...])

model = LogisticRegression()
model.fit(x,y)

y_predictions = model.predict(x)
accuracy = model.score(x,y)
```

If normalized data is desired
```python
from sklearn.preprocessing import StandardScaler

normalizer = StandardScaler()
x_normalized = normalizer.fit_transform(x)
```

## Improving fit
Could add more features like the following
$$
\begin{align}
z = &w_1x_1 + w_2x_2 \\
	&w_3x_1^2 + w_4x_2^2 \\
	&w_5x_1x_2 + b \\
	\\
f_{x,b}(x) =& g(z)
\end{align}
$$