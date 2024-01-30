(as opposed to [[Underfitting]])
a common problem in ML
a model is said to be overfit, if it is perfectly suited to the training data, but doesn't generalize to unseen testing data
also known as "high variance"
## Ways to combat overfitting
1. use more training data
	-  The more data the harder it is to overfit it
2. select features to include/exclude feature selection
	- useful features could be lost
3. use [[Regularization]]
	- reduces the impact of large polynomials without deleting them

## Potential Causes
- if there are a lot of features, but insufficient data, that can lead to overfitting

## Degrees
$$
\begin{align}
&w_0x_0 + w_1x_1 + b \\
&w_0x_0 + w_1x_1 + w_2x_0^2 + w_3x_0x_1 + w_4x_1^2 + b \\
&w_0x_0 + w_1x_1 + w_2x_0^2 + w_3x_0x_1 + w_4x_1^2 + w_5x_0^3 + w_6x_0^2x_1 + w_7x_0x_1^2 + w_8x_1^3 + b \\
&w_0x_0 + w_1x_1 + w_2x_0^2 + w_3x_0x_1 + w_4x_1^2 + w_5x_0^3 + w_6x_0^2x_1 + w_7x_0x_1^2 + w_8x_1^3 + w_{10}x_0^3x_1 + w_{ 9}x_0^4 + w_{11}x_0^2x_1^2 + w_{12}x_0^1x_1^3 + w_{13}x_1^4 + b \\
\end{align}
$$
