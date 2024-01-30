## Gradient descent for [[Linear Regression]]

Cost function  $J(w,b)$
Want $\underset{w,b}{min} \; J(w,b)$

Start with $(w=0, b=0)$
keep changing $w,b$ to reduce $J(w,b)$ until we settle at or near a min


## Algorithm(s)
$$
w = w - \alpha \frac{\partial}{\partial w} J(w,b)
$$
> equal sign here is the assignment operator (as in coding)
> $\alpha$ - *learning rate* (how big/small the step downhill is)

$$
b = b - \alpha \frac{\partial}{\partial b} J(w,b)
$$

These two equations, updating w and b, should be done simultaneously 
$$
\begin{align}
&tempW = w - \alpha \frac{d}{dw} J(w,b) \\
&tempB = b - \alpha \frac{d}{db} J(w,b) \\
&w = tempW \\
&b = tempB
\end{align}
$$

Repeat until convergence

### Computing [[Batch gradient descent]] for [[Squared error cost function]] 
gradient descent on a linear regression model, with a squared error cost function

To update $w$ and $b$ we need to do:
$$
\begin{align}
&w = w - \alpha \frac{\partial}{\partial w} J(w,b) \\
&b = b - \alpha \frac{\partial}{\partial w} J(w,b)
\end{align}
$$
and given that: 
$$
\begin{align}
	 & \frac{\partial}{\partial w} J(w,b)  = \frac{\partial}{\partial w} \frac{1}{2m} \sum_{i=1}^m(f_{w,b}(x^{(i)}) - y^{(i)})^2 \\
	& \frac{\partial}{\partial b} J(w,b)  = \frac{\partial}{\partial b} \frac{1}{2m} \sum_{i=1}^m(f_{w,b}(x^{(i)}) - y^{(i)})^2 
\end{align}
$$

for the squared error cost function, then we can use the chain rule from calc to get the following

$$
\begin{align}
	& w = w - \alpha\frac{1}{m} \sum_{i=1}^m(f_{w,b}(x^{(i)}) - y^{(i)}) x^{(i)}\\
	& b = b - \alpha\frac{1}{m} \sum_{i=1}^m(f_{w,b}(x^{(i)}) - y^{(i)})	
\end{align}
$$

because $f_{w,b}(x^{(i)}) = wx^{(i)} + b$ we can translate above to this:
$$
\begin{align}
	& w_j = w_j - \alpha\frac{1}{m} \sum_{i=1}^m(wx^{(i)} +b - y^{(i)}) x_j^{(i)} \\
	& b = b - \alpha\frac{1}{m} \sum_{i=1}^m(wx^{(i)} + b - y^{(i)})	
\end{align}
$$

*squared error cost function only has one, global minimum* because it is a convex function
	So we don't need to worry about finding a local minimum that is not the global minimum

### Considerations
If $\alpha$ is too small
	gradient descent may be slow
If $\alpha$ is too large
	gradient scent may overshoot and/or never reach the minimum
	it may fail to converge, and diverge

## Types of gradient descent
- batch
- subsets

## Transformers
> w - weight
> a - activation
> b - bias  

$$
\sigma{

  \Bigg(

    \begin{bmatrix}

  w_{0,0} & w_{0,1} &...& w_{0,n} \\

  w_{1,0} & w_{1,1} &...& w_{1,n}\\

  w_{2,0} & w_{2,1} &...& w_{2,n}

    \end{bmatrix}

    \begin{bmatrix}

      a_0^{(0)}\\

      a_1^{(0)}\\

      \vdots\\

      a_n^{(0)}\\

    \end{bmatrix}

     +

    \begin{bmatrix}

      b_0\\

      b_1\\

      \vdots\\

      b_k\\

    \end{bmatrix}

  \Bigg)

}

$$

Shortened to
$$
a^{(1)} = \sigma{
  (Wa^{(0)} + b)
}
$$
## Stochastic gradient descent
> It would in practice be too costly to backprop after every example, so we break up the training data into what are called mini-batches, after mixing it up into a random order and run the gradient descent on each batch. This is know as **stochastic gradient descent**

