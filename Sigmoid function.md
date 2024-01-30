$$
g(z) = \frac{1}{1 + e^{-z}} \quad 0 < g(z) < 1
$$

aka the logistic function

Used in logistic regression. Outputs between 0 and 1, with $g(1) = 0.5$ 

```python
# z: a scalar numpy array of any size
def sigmoid(z):
	g = 1 / (1 + np.exp(-z))
	return g
```
