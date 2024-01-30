Regression trees are [[Decision Trees]] used for regression problems, meaning they are used to predict a continuous value. 

## Choosing what to output
Once a model reaches its leaves, it will return an average of the values from its training examples 

## Choosing on what to split
We try each feature and try to reduce variance between the examples

This is computed in much the same way as entropy
$$
\text{variance reduction} = \text{variance}^{root} - \bigg( w^{left} \cdot \text{variance}^{left} + w^{right} \cdot \text{variance}^{right} \bigg)
$$
> $w$ - the ratio of the examples on one branch compared to the local root