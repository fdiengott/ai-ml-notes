In [[Decision Trees]], information gain is the reduction of [[Entropy]]

$$
\text{information gain} = H(p_1^{root}) - \bigg( w^{left} H(p_1^{left}) + w^{right} H(p_1^{right}) \bigg)
$$
> $H$ - [[Entropy]] (impurity) $H(0.5) = 1$, $H(0) = 0 = H(1)$ 
> $p_1$ - ![[Entropy#^bc9d5a]] out of the whole of the branch
> $w$ - the fraction of examples that went to this branch

This equation is run on each possible feature, and the feature that leads to the highest value of information gain is chosen

![[Pasted image 20240125005341.png]]

It is computed by taking the entropy of the root of the current subtree and subtracting from it the weighted average of the entropy for each branch after it has been split by some feature.

## Example
This example has 10 pets: 5 cats, 5 dogs
![[Pasted image 20240125005857.png]]
$p_1^{root}$ is the fraction of the total that are 1 (is cat)
$p_1^{left}$ is the fraction of this branch that are 1 (is cat)
$w^{left}$ is the fraction of examples that went to the left sub-branch 

## Implementation 

Splits the data set at a given node into left and right branches
```python
def split_dataset(X, node_indices, feature):
	"""
    Args:
        X (ndarray):             Data matrix of shape(n_samples, n_features)
        node_indices (list):     List containing the active indices. I.e, the samples being considered at this step.
        feature (int):           Index of feature to split on
    
    Returns:
        left_indices (list):     Indices with feature value == 1
        right_indices (list):    Indices with feature value == 0
	"""

	left_indices = []
    right_indices = []
    
	for i in node_indices:
		if X[i, feature] == 1:
	        left_indices.append(i)
		else:
			right_indices.append(i) 
    
    return left_indices, right_indices
```

information gain on a given feature
```python
def compute_information_gain(X, y, node_indices, feature):
    """
    Args:
        X (ndarray):            Data matrix of shape(n_samples, n_features)
        y (array like):         list or ndarray with n_samples containing the target variable
        node_indices (ndarray): List containing the active indices. I.e, the samples being considered in this step.
   
    Returns:
        cost (float):        Cost computed
    
    """    
    
    left_indices, right_indices = split_dataset(X, node_indices, feature)
    
    y_node = y[node_indices]
    y_left = y[left_indices]
    y_right = y[right_indices]
    
    m = len(node_indices)
    w_left = len(left_indices) / m
    w_right = len(right_indices) / m
    
    entropy_root = compute_entropy(y_node)
    entropy_left = compute_entropy(y_left)
    entropy_right = compute_entropy(y_right)
    
    entropy_change = w_left * entropy_left + w_right * entropy_right
    
    return entropy_root - entropy_change    
```

Get the best feature to split on
```python
def get_best_split(X, y, node_indices):   
    """
    Args:
        X (ndarray):            Data matrix of shape(n_samples, n_features)
        y (array like):         list or ndarray with n_samples containing the target variable
        node_indices (ndarray): List containing the active indices. I.e, the samples being considered in this step.

    Returns:
        best_feature (int):     The index of the best feature to split
    """    
    
    num_features = X.shape[1]
    best_feature = -1
    best_info_gain = 0
    
    for feature_idx in range(num_features):
        info_gain = compute_information_gain(X, y, node_indices, feature_idx)
        
        if info_gain > best_info_gain:
            best_info_gain = info_gain
            best_feature = feature_idx
   
    return best_feature
```