#expert-learning 
#alignment-technique 
Using a team of AI systems as a teacher for a more capable model, and recursively improve

**One-step amplification** - imagine delegating tasks to up to 100 versions of fast copies of oneself. 

This is a system of having models learn from an expert, except in this case, the "expert" is a group of models that are almost as capable (at least at first) as the model they are training


We start with a sampling of small subtasks and train a model by having it follow an expert who can do these small tasks. We then sample slightly larger tasks, solving them by asking humans to break them up into small pieces, which the model can now solve. This becomes the training signal for a model to handle larger tasks. This process is iterated until the model can solve highly composite tasks despite starting with no direct training signal for those tasks. 

