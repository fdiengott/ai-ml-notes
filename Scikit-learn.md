## To create fake data
```python
from sklearn.datasets import make_blobs

# mutli-class clasification data
classes = 4
m = 100
centers = [[-5, 2], [-2,-2], [1,2],[5,-2]]
std = 1.0
X_train, y_train = make_blobs(n_samples=m, centers=centers, cluster_std=std, random_state=30)
```
![[Pasted image 20231224215828.png]]

