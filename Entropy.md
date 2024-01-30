A measure of impurity. The reduction of entropy is called *information gain*

Often defined as $H(p_1)$
![[Pasted image 20240124200457.png]]

$p_1$ is the fraction of examples that are equal to 1 in a binary classification problem  ^bc9d5a
	(probability of a 1)

$p_0 = 1 - p_1$

$$
\begin{align}
H(p_1) &= -p_1\log_2(p_1) - p_0\log_2(p_0) \\ 
&= -p_1\log_2(p_1) - (1 - p_1)\log_2(1 - p_1)
\end{align}
$$

## Implementation
```python
def get_entropy(y):
    """
	y (ndarray): Numpy array        
	Returns: entropy (float): Entropy at that node    
    """
    if len(y) == 0:
        return 0.
    
    p_1 = sum(y) / len(y)
    
    if p_1 == 0 or p_1 == 1: 
        return 0.
    
    return -p_1 * np.log2(p_1) - (1 - p_1) * np.log2(1 - p_1)
```