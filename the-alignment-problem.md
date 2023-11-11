
Techniques:
- Temporal difference learning
    The model, rather than waiting until it gets a reward, will check its prediction of some goal, do something, and then make a second prediction. It will compare the two predictions and learn from the delta.

- Inverse Reinforcement Learning
    The model's goal is to learn another agent's underlying intent, goals, or reward function

- Imitation learning
    Instead of giving a model a point system to optimize, you have it learn from another agent and try to imitate.

- Dropout uncertainty
    A method, whereby a model during training will randomly leave out some of the neurons in its computation to make the overall model more robust. This is also done after training and the smaller models answer is compared to the full models answer to derive a proxy confidence score.

- Iterated distillation and amplification
    During training, a model will create a guess of the outcome of some process and then have an expensive Monte Carlo Tree Search (MCTS) settle on the best choice. The two are then compared and this process is repeated over and over again until the model can't be improved. The benefits are that this approach reaches the capabilities of the expensive approach while vastly improving on speed.


- Corrigible
    A willingness to accept that one's goals might be incorrect, a "caution". This approach will likely stop a model from fearing being turned off.

- Inverse Reward Design
    A model takes a given reward function as evidence for an agent's goal, but not as the goal itself. As in it doesn't take it literally, but as steering toward a goal.
