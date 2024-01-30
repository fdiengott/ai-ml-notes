An implementation of boosted trees, which are an implementation of a [[Random forest]] algorithm which is an ensemble of [[Decision Trees]].

It is similar to the [[Bagged decision tree ensemble]] algorithm, with the difference being that each newly trained tree focus more attention on where all previous trees misclassified the training data

## Implementation
Given a training set of size $m$
For $b = 1$ to $B$:
- use sampling with replacement to create a new training set of size $m$
	- instead of picking from all examples with equal ($1/m$) probability, make it more likely to pick misclassified examples from the previously trained trees
- train a decision tree on the new dataset

## XGBoost (eXtreme gradient boosting)
- open source implementation of boosted trees
- fast efficient implementation
- good choice of default splitting criteria and criteria for when to stop splitting
- built in regularization to prevent overfitting

Doesn't use sampling and replace to collect training data, but instead assigns different weights to the training examples

## Code 
```python
from xgboost import XGBClassifier
from xboost import XGBRegressor

classifierModel = XGBClassifier()
regressorModel = XGBRegressor()

model = classifierModel if task == 'classification' else regressorModel

model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```