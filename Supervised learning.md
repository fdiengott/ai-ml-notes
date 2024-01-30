The two tasks of supervised learning
- [[Classification]] - the goal is to assign a label
- [[Regression]] - the goal is to predict a continuous numerical value
  - continuous - there aren't any gaps or **discontinuities** in the value that y can take of
  - discrete - when variables that can only take on a finite number of values


$$y = f(x) + \epsilon$$

> x - input
> y - output
> f - function describing the relationship between X and Y
> ϵ (epsilon) - random error term (positive or negative) with mean zero


Ordinary least squares (OLS) regression - a method used to learn a model by minimizing the sum of squared differences between the observed and predicted values of a dependent variable

[[Linear Regression]] is a **parametric method**, meaning it makes an assumption about the form of the function relating x and y
(e.g. that the data is linear)
