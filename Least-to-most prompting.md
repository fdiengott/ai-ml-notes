#expert-learning 
Similar to [[Chain of thought prompting]]

Two stages:
1. Decomposition. Decompose the problem into a list of easier subproblems. 
	- Before the specific question, demonstrate a bunch of examples of proper decomposition. 
2. Subproblem solving. Solve each problem in series, feeding the answer of the previous problem into the current one. 
	- Before the specific question, demonstrate examples of how subproblems are solved. 

This in practice is like starting with a simple prompt asking for an easy answer, then re-prompting and adding that easy answer to the initial prompt while asking the next subproblem. 

