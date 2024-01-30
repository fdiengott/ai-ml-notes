An implementation of [[Unsupervised Learning]] which takes unlabeled data and groups similar data together. The most common implementation is the K-means clustering algorithm. 

## Applications of clustering
- Google news grouping by subject
- Market segmentation
- DNA analysis
- Astronomical data analysis

## K-means Clustering
The algo does fundamentally 2 things:
1. Assign points to cluster centroids
2. move cluster centroids

It starts out by randomly choosing points as centroids

For example, if there are two centroids, we would then assign all of the values to the centroid that is closest. The centroids are then moved to a new location that is the average of all of the data points that we assigned to it. 

These two steps are repeated until the algorithm converges, meaning the centroids no longer change. 

### Algorithm 
Randomly initialize $K$ cluster centroids $\mu_1, \mu_2, ...,\mu_K$
> $\mu$ are vectors with the same dimensions as the training data

Assign points to cluster centroids
```pseudocode
for i=1 to m
	c^(i) = index (from 1 to K) of cluster centroid closest to x^(i)
```
$$
\text{distance} = L2_{norm} = || x^{(i)} - \mu_k ||
$$
$$
\text{index} = min_k|| x^{(i)} - \mu_k ||^2
$$

Move cluster centroids
```pseudocode
for $k=1$ to $K$
	$\mu_k$ = average (mean) of points assigned to cluster $k$
```

If a cluster has no points assigned to it, most commonly that cluster is eliminated and we are left with $k - 1$ clusters