The process of passing data through a neural network layer by layer to generate an output. Each layer's output is based upon the previous layer's input

## Python
- $w_1^{[2]}$ in code would be represented as `w2_1`
- It is convention for a capital variable to be used for a matrix, whereas lower case would be a vector or scalar

### Example
if 
$$
\begin{align}
w_1^{[1]} &=\begin{bmatrix} 1 \\ 2 \end{bmatrix} \\
w_2^{[1]} &=\begin{bmatrix} -3 \\ 4 \end{bmatrix} \\
w_3^{[1]} &=\begin{bmatrix} 5 \\ -6 \end{bmatrix} \\
\end{align}
$$

in code we represent as 
```python
w = np.array([
	[1,-3, 5],
	[2, 4,-6]
])
```

```python
def dense(a_initial, weights, biases):
	untis = weights.shape[1] # number of w columns
	a_out = np.zeros(units)
	
	for j in range(units):
		w = weights[:,j]
		z = np.dot(w,a_initial) + b[j]
		a_out[j] = g(z) # g could be sigmoid or other non-linear fn
	return a_out
```

```python
def sequential(x):
	a1 = dense(x, W1, b1)
	a2 = dense(a1, W2, b2)
	a3 = dense(a2, W3, b3)
	a4 = dense(a3, W4, b4)
	f_x = a4
	return f_x
```

### Vectorization 
`np.matmul` (matrix multiplication) replaces the for loop
```python
X = np.array([[200, 17]]) #2d array
W = np.array([[1,-3,5],
			  [-2,4,-6]])
B = np.array([[-1,1,2]]) # 1x3 2d array

# all inputs are 2d arrays
def dense(a_transposed, W,B):
	Z = np.matmul(a_transposed, W) + B # matrix multiplication
	a_out = g(Z)

	return a_out
```

$Z = A^TW + B$
