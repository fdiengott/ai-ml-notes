# Gradient descent and Backpropagation

> w - weight
>
> a - activation
>
> b - bias
>

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
      ...\\
      a_n^{(0)}\\
    \end{bmatrix}
     +
    \begin{bmatrix}
      b_0\\
      b_1\\
      ...\\
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


> **Stochastic gradient descent**
>
> It would in practice be too costly to backprop after every example, so we break up the training data into what are called mini-batches, after mixing it up into a random order and run the gradient descent on each batch. This is know as **stochastic gradient descent**
