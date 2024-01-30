#cost-functions 
Most common cost function for all linear regression problems and very common for all regression problems

### Equation
$$
J(w,b) = \frac{1}{2m}\sum_{i=1}^m(\hat{y} - y)^2
$$
*$J$ - cost function*
*w - weight*
*b - balance*
*m - number of training examples*
*$\hat{y}$  - model's prediction*
> get the average square error (the 2m is added to clean up some later steps)

error: $\hat{y} - y$ 
	the difference between the prediction and the actual value

$\hat{y}$ is the output from $f(x)$ aka $f_{w,b}(x)$ so the equation above could be rewritten: 
$$
J(w,b) = \frac{1}{2m}\sum_{i=1}^m(f(x^{(1)}) - y^{(1)})^2
$$
## Goal
$$\underset{w,b}{minimize}\; J(w,b)$$
> minimize $J$ as a function of $w$ and $b$

Try to find values for w and b that make $J$ as small as possible

## Graphed
The output of this function graphed on a 2d axis with $w$ on the x-axis and $J(w)$ on the y-axis is a parabola
In 3d it is also parabolic with $w$ on the x-axis and $J(w,b)$ on the y-axis and $b$ on the z-axis


[[Gradient descent]] is used to find the proper values for $w$ and $b$
