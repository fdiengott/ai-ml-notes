Add a penalty to the loss function for taking too much influence from a single feature or allows too many features to be taken into account. 

This is often applied after doing [[Feature mapping]]

$$
Cost = \frac{ \sum_{1}^n((\beta_1x_i + \beta_0) - y_i)^2}{2*n} + \lambda\sum_{i=0}^1\beta_i^2
$$

the 2nd piece above is the regularization term. It adds a penalty for large beta coefficients that give too much explanatory power to any specific feature. 

$\beta_1$ and $\beta_2$ are our model parameters. 
$\lambda$ is our [[Hyperparameter]] (the coefficient of the regularization term in the cost function above)

## Simply
This is a way to reduce the effect from higher order polynomials without setting them to 0

## In practice
First one needs to do [[Feature mapping]] to get higher order polynomials. 
$$
J(w,b) = \frac{1}{2m}\sum_{i=1}^m(f(x^{(i)}) - y^{(i)})^2 + \frac{\lambda}{2m}\sum_{j=1}^nw_j^2
$$

$\lambda$ - regularization parameter
Lambda balances the two goals:
1. fit data
2. keep $w_j$ small

If lambda is small, the model will likely [[Overfitting|overfit]]
If lambda is large, the model will likely [[Underfitting|underfit]]

## Gradient descent 

$$
\begin{align}
	& w = w - \alpha\bigg[\frac{1}{m} \sum_{i=1}^m \bigl[ (f_{w,b}(x^{(i)}) - y^{(i)}) x^{(i)} \Bigr] + \frac{\lambda}{m}w_j\bigg]\\
	& b = b - \alpha\frac{1}{m} \sum_{i=1}^m(f_{w,b}(x^{(i)}) - y^{(i)})	
\end{align}
$$
* we don't regularize $b$

$w$ can be rewritten like this
$$
\begin{align}
w_j = w_j - \alpha \frac{\lambda}{m}w_j - \alpha\frac{1}{m} \sum_{i=1}^m \bigl[ (f_{w,b}(x^{(i)}) - y^{(i)}) x^{(i)} \Bigr] \\
w_j = w_j(1 - \alpha \frac{\lambda}{m}) - \alpha\frac{1}{m} \sum_{i=1}^m \bigl[ (f_{w,b}(x^{(i)}) - y^{(i)}) x^{(i)} \Bigr] \\
\end{align}
$$

The difference for the above between [[Linear Regression]] and [[Logistic Regression]] is: 
### Linear regression 
$$
f_{w,b}(x^{(i)}) = w \cdot x + b
$$

### Logistic Regression
$$
\begin{align}
f_{w,b}(x^{(i)}) &= \frac{1}{1 + e^{-z}} \\
z^{(i)} &= w \cdot x^{(i)} + b
\end{align}
$$
