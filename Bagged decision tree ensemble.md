A [[Tree ensemble]] implementation, which is itself a collection of [[Decision Trees]].
## Implementation

^ba75a9

Given a training set of size $m$
For $b = 1$ to $B$:
- use [[Sampling with replacement]] to create a new training set of size $m$
- train a decision tree on that dataset

> $B$ - bagged decision tree

$B$ values generally span between 64 and 128, meaning this algo would train approx. 100 trees. 