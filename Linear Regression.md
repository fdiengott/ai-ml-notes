## Univariate linear regression
### Equation
$$
f_{w,b}(x) = wx + b
$$

Simpler notation: $f(x)$

Above is linear regression with one variable (feature)
	aka "univariate linear regression"

### Cost function
In univariate linear regression, w and b are considered
- parameters
- coefficients
- weights

error: $\hat{y} - y$ 
	the difference between the prediction and the actual value

Cost function: [[Squared error cost function#Equation|squared error cost function]]
$$
J(w,b) = \frac{1}{2m}\sum_{i=1}^m(\hat{y} - y)^2
$$
> This is the most common cost function for linear regressions.

[[Gradient descent]] is used to find the proper values for $w$ and $b$

## Gradient descent alternatives
- [[Normal Equation]]
## Multiple linear regression

### New notation
$x_j$ = $j^{th}$ feature
$n$ = number of features
$\vec{x}^{(i)}$ = features of $i^{th}$ training example (a list of values)
$x_j^{(i)}$ = value of feature $j$ in $i^{th}$ training example

### Equation
$$
f_{\vec{w},b}(\vec{x}) = w_1x_1 + w_2x_2 + ... + w_nx_n + b
$$

weight vector, parameters of the model
$\vec{w} = [w_1\; w_2\; w_3\; ...\; w_n]$

vector
$\vec{x} = [x_1\; x_2\; x_3\; ...\; x_n]$

The above can be rewritten (with the dot representing the [[Dot product]]):
$$
f_{\vec{w},b}(\vec{x}) = \vec{w}\cdot\vec{x} + b
$$
In code, this is best implemented through [[Vectorization]]

### Multivariable gradient descent

Using [[Vectorization]], updating $w$ can be done as follows:
```python
w = np.array([...])
derivative_cost = np.array([...])
...
w = w - alpha*derivative_cost
```

#### Math notation
$$
\begin{align}
w_1 &= w_1 - \alpha \frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)})\; x_i^{(i)}\\
& \vdots \\
w_n &= w_n - \alpha \frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)})\; x_n^{(i)}\\
\\ 
\\
b &= b - \alpha \frac{1}{m}\sum_{i=1}^m(f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)})

\end{align}
$$

### How to choose proper starting parameters for weights and biases and learning rate 
Weights: use [[Feature Scaling]]

Alpha: 
- plot a [[Learning Curve]]
- [[Automatic convergence test]]

## Regularization 
### Cost #cost-functions
$$
J(w,b) = \frac{1}{2m}\sum_{i=1}^m(f(x^{(i)}) - y^{(i)})^2 + \frac{\lambda}{2m}\sum_{j=1}^nw_j^2
$$
### [[Gradient descent]]
$$
\begin{align}
w_j = w_j - \alpha \frac{\lambda}{m}w_j - \alpha\frac{1}{m} \sum_{i=1}^m \bigl[ (f_{w,b}(x^{(i)}) - y^{(i)}) x^{(i)} \Bigr] \\
w_j = w_j(1 - \alpha \frac{\lambda}{m}) - \alpha\frac{1}{m} \sum_{i=1}^m \bigl[ (f_{w,b}(x^{(i)}) - y^{(i)}) x^{(i)} \Bigr] \\
\end{align}
$$

## Notes
Choosing features is important. One might also want to employ [[Feature Engineering]] to create new features from original features

## Scikit-learn
```python
import numpy as np
from sklearn.linear_model import SGDRegressor

x = np.array([...])
y = np.array([...])

model = SGDRegressor(max_iterations=1000)
model.fit(x,y)

b = model.intercept_
w = model.coef_

y_predictions = model.predict(x)
```

If normalized data is desired
```python
from sklearn.preprocessing import StandardScaler

normalizer = StandardScaler()
x_normalized = normalizer.fit_transform(x)
```