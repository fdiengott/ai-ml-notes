Standardizing or normalizing the ranges of all input features. This is used to set initial values for our weight ($\vec{w}$) vector

The goal is to aim for $-1 \leq x_j \leq 1$ for each feature, but the following are acceptable ranges
$$
\begin{align}
-3 \leq x_j \leq 3 \\
-0.3 \leq x_j \leq 0.3 \\
0 \leq x_j \leq 3\\
-2 \leq x_j \leq 0.5
\end{align}
$$

## Example
$$
\hat{price} = w_1x_1 + w_xx_2 + b
$$
Training data 1: $x_1$ = 2000, $x_2$ = 5, $price$ = $500k

Ranges
$x_1$: size (feet^2) --- range: 300-2000
$x_2$: # bedrooms --- range: 0 - 5

For this example it is best to use a *small* initial $w_1$ given the large range for $x_1$, and a *large* $w_2$ for the small range of $x_2$ 

## Process
### Rescaling (Min-max normalization)
Take our x1 range and an example. Take that value minus the range min, and divide it over the range of max - min.
$$
\frac{x_1 - min(x_1)}{max(x_1) - min(x_1)}
$$
#### Example 
if $300 \leq x_1 \leq 2000$
$x_{1, scaled} = \frac{x_1}{2000}$ 
$0.15 \leq x_{1,scaled} \leq 1$

if $0 \leq x_2 \leq 5$
$x_{2,scaled} = \frac{x_2}{5}$
$0 \leq x_{2,scaled} \leq 1$

### Mean normalization
$\mu$ - mean
find the average of each feature, $x_i$ in the data set - $\mu_1$ 

$$
x_j = \frac{x_j - \mu_j}{max_j - min_j}
$$

#### Example
$$
x_j = \frac{x_j - \mu_j}{2000 - 300}
$$
$$-0.18 \leq x_1 \leq 0.82$$

$$
x_2 = \frac{x_2 - \mu_2}{5 - 0}
$$
$$-0.46 \leq x_1 \leq 0.54$$

### Z-score normalization
$\sigma$ - standard deviation
$\mu$ - average
$$
x_j^{(i)} = \frac{x_j - \mu_j}{\sigma_j}
$$

#### Example
if $300 \leq x_1 \leq 2000, \mu_1 = 600, \sigma_1 = 450$
$x_{1, scaled} = \frac{x_1 - 600}{450}$ 
$-0.67 \leq x_{1,scaled} \leq 3.1$

if $0 \leq x_2 \leq 5$
$x_{2,scaled} = \frac{x_2 - 2.3}{1.4}$
$-1.6 \leq x_{2,scaled} \leq 1.9$

```python
def getNormalizedFeatures(x):
	"""
	Args
	  x           : matrix of m examples and n features
	Returns
	  xNoramlized : input normalized by column
	  mu          : mean of each feature
	  sigma       : standard deviation of each feature
	"""

	mu = np.mean(x, axis=0)
	sigma = np.std(x, axis=0)
	xNormalized = (x - mu) / sigma

	return xNormalized, mu, sigma
```

### TensorFlow #TensorFlow 
```python
import tensorflow as tf

normalization_layer = tf.keras.layers.Normalization(axis=-1)
normalization_layer.adapt(x) # learns the mean and variance

x_normalized = normalization_layer(x)
```