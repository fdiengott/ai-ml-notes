Taking a model's outputs and manually examining the examples in which the model made a mistake, and sorting them into groups.
(One training example can belong to more than one category)

Ideally you would count how many examples would belong in each group to understand which are the problems the model needs work on. Then, using the bias/variance tradeoff, would decide the most helpful course of action for improvement.

If there are too many examples that were in error to group manually, then it is a good idea to take a smaller sample of the whole 

Error analysis is hard for problems that humans aren't good at

[[Precision and recall]] would also be helpful metrics to have during error analysis