## Concepts referenced below
[[Inverse Reinforcement Learning (IRL)]]
[[Mechanistic interpretability]] - in reference to inner alignment's goal of transparency
[[Reinforcement Learning from human feedback (RLHF)]] - "learn from feedback" in outer alignment
[[Adversarial Training]]
[[Inner Alignment]]
[[Outer Alignment]]

```mermaid
graph RL
	competent[Make AI competent] --> main[Make AI go well]
	Reliability --> competent
	align[Make AI aligned] --> main
	understand[Make it understand humans] --> competent
	meta[make it good at making AI good] --> competent
	cope[cope with impacts of ai] --> main
```

Alignment tax: the cost of making systems that do what we want. Cost of insisting on alignment


```mermaid
graph RL
	 at[Adversarial training] --> ia[Inner alignment]
	Transparency --> ia
	Verification --> ia
```

```mermaid
graph RL
	teacher[Learn from teacher] --> oa[Outer alignment]
	imitate[Imitate Teacher] --> teacher
	feedback[Learn from feedback] --> teacher
	irl[Infer preferences] --> teacher
	beyond[Go beyond teacher] --> oa
	extrap[Learner extrapolation] --> beyond
	infer[Infer robust preferences] --> beyond
	better[build a better teacher] --> beyond	
```

[[Iterated Amplification]]: Using a team of AI systems as a teacher for a more capable model, and recursively improve

