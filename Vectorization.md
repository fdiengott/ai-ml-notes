> Utilizing specialized hardware to calculate [[Dot product|dot products]] in parallel, rather than in series


Linear algebra is 1 indexed

$\vec{w} = [w_1\; w_2\; w_3] \qquad n=3$
$b$ is a number
$\vec{x} = [x_1\; x_2\; x_3]$

## Without vectorization
```python
f = w[0] * x[0] + 
	w[1] * x[1] + 
	w[2] * x[2] + b

# or

f = 0
for j in range(n):
	f += w[j] * x[j]
f += b
```

## With vectorization
$f_{\vec{w},b}(\vec{x}) = \vec{w}\cdot\vec{x} + b$
```python
f = np.dot(w,x) + b
```

## Matrix multiplication
```python
A = np.array([[1,-1,0.1],
			  [2,-2,0.2]])
A_transposed = A.T # [[1,2],
				   #  [-1,-2]
				   #  [0.1,0.2]]

W = np.array([[3,5,7,9],
			  [4,6,8,0]])

Z = np.matmul(A_transposed, W) # A_transposed @ W
```