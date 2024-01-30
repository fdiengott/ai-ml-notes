Ways to improve [[Neural Networks]], [[Linear Regression]]s, [[Logistic Regression]]s

Also look at [[Error Analysis]]
If it is concluded that more data should be added, check [[Adding data|here]].

## Evaluating a model
### Linear Regression
Split the dataset (for example 70/30) into train and test examples

Minimize cost based on the training data
$$
J(\vec{w},b) = \Bigg[\frac{1}{2m_{train}} \sum_{i=1}^{m_{train}} (f_{\vec{w},b}(\vec{x}^{(i)}) - y^{(i)})^2 + \frac{\lambda}{2m_{train}}\sum_{j=1}^n w_j^2 \Bigg]
$$

Compute the test error
$$
J_{test}(\vec{w},b) = \Bigg[\frac{1}{2m_{test}} \sum_{i=1}^{m_{test}} (f_{\vec{w},b}(\vec{x}_{test}^{(i)}) - y_{test}^{(i)})^2 \Bigg]
$$

Compute the training error. 
	Same function as the test error above but on the training data and doesn't include the regularization term

### Logistic Regression
$$
J(\vec{w}, b) = -\frac{1}{m_{train}}\sum_{i=1}^{m_{train}}[y^{(i)}log(f^{(i)}) + (1 - y^{(i)})log(1 - f^{(i)})] + \frac{\lambda}{2m_{train}} \sum_{j=1}^n w_j^2
$$
Test Error:
$$
J_{test}(\vec{w}, b) = -\frac{1}{m_{test}}\sum_{i=1}^{m_{test}}\bigg[y_{test}^{(i)}log(f^{(i)}) + (1 - y_{test}^{(i)})log(1 - f^{(i)})\bigg]
$$
Train Error
	Same as above except with the training data and doesn't include the regularization term

For regularization it is more common to count up all of the instances where $\hat{y} \neq y$ to get the fraction of the test set (and the fraction of the training set) that the algorithm has misclassified

## Cross validation
Split the data into 3 parts: training / cross validation / and test
60% / 20% / 20%

Cross validation set aka "validation set" aka "development set" aka "dev set"

Run $J_{cv}$ (cost for the cross validation data) on higher order polynomials
$$
\begin{align}
&d = 1 &&f_{w,b}(x) = w_1x + b \\
&d = 2 &&f_{w,b}(x) = w_1x + w_2x^2 + b \\
&d = 3 &&f_{w,b}(x) = w_1x + w_2x^2 + w_3x^3 + b \\
& &&\vdots \\
&d = 10 && f_{w,b}(x) = w_1x + w_2x^2 + ... w_{10}x^{10} + b \\
\end{align}
$$
whichever has the lowest $J_{cv}$ pick that polynomial. (i.e. $J_{cv}(w^{<4>},b^{<4>})$)
Then to estimate the generalization error, find the cost on the test set, $J_{test}$ (i.e. $J_{test}(w^{<4>},b^{<4>})$)

### Neural network
Can train a number of different architectures (different number of layers and neurons per layer) and train those models based on the test data. Then the cost can be found for each model on the cross validation test set. This can be used to find the architecture with the lowest cost 

## Deciphering bias/variance & regularization parameter
This next bit relates to [[Bias-variance tradeoff]]
### Figuring out whether you have High bias or high variance

If high bias (underfit)
- $J_{train}$ is high
- $J_{cv}$ is high

If high variance (overfit)
- $J_{train}$ is low
- $J_{cv}$ is high

A good balance of bias/variance has low for both

### Choosing regularization parameter
![[Pasted image 20240117003833.png]]
a small $\lambda$ (e.g. 0) overfits (high variance) and a high $\lambda$ underfits (high bias)

### Example numbers
Ways to get an accurate estimate of how good a model can be: compare against 
- human level performance 
- competing algorithms performance
- guess based on experience

![[Pasted image 20240117004902.png]]
In the example above, we compare the gap between the first two numbers with the second two numbers (e.g. 10.6%/10.8% then 10.8%/14.8%)

### Things that will improve bias/variance

#### If high bias do these things
- Try adding additional features
- Try adding polynomial features
- Try decreasing $\lambda$

#### If high variance do these things
- Get more training examples
- Try smaller sets of features
- Try increasing $\lambda$

### Should you get more data?
If a model has high bias, more data will not help.
If a model has high variance, more data will help. 

## Neural Network considerations
Large neural networks are low bias machines

![[Pasted image 20240121112530.png]]
In the diagram above:
- If in the first state, there is a high bias problem 
- If in the second state, there is a high variance problem 

A larger neural network (more layers/neurons per layer) will pretty much always perform better than a smaller network if regularized appropriately at the cost of increased computation time/intensity
