A [[Tree ensemble]] implementation, which is itself a collection of [[Decision Trees]].
## Bagged decision implementation
![[Bagged decision tree ensemble#Implementation]]
## Random forest
Is the same as the [[Bagged decision tree ensemble]] implementation above, except for one small change:
- at each node, when choosing a feature to split, if $n$ features are available, pick a random subset of $k<n$ features that allow the algorithm to only choose from that subset of features

Traditionally the value of $k$ (when $k$ is large) is $\sqrt{n}$ 

## Boosted Trees
Similar to bagged trees above except for one major point
![[Boosted Trees#Implementation]]