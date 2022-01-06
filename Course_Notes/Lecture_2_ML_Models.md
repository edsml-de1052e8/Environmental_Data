# Lecture 2: Evaluating Machine Learning Models

**Baseline score**

- Using simple strategy, for prediction use class probability.
- NB: check if training dataset is imbalanced
- Classification: Predicts a random (balanced) or most frequent (imbalanced) class
- Regression: Predicts a central tendency measure e.g. mean, median or mode

```random_state``` sets seed, most common number is 42

Why use dummy models?
- scikit learn objects can be created, just need to apply one fit to the object so quite easy to use and also swap it at the end of the process

**Regression Metrics**

- Mean Squared Error (MSE): difference between predicted value and true value and squared
- Root Mean Squared Error (RMSE): that is just the MSE with a root, same unit as MSE
- Mean absolute error: absolute value of the error, corrects for the sign. Less sensitive to outliers.
- Max error: absolute error and using the one data point that is the outlier
- Coefficient of determination (R^2): all features are all the same unit so can be comparable.


In Sklearn:
- note that there isn't a RMSE function, but using ```import math``` you can just add square root to MSE

**Classfification Metrics**

Errors:
- Type I Error: false negative
- Type II Error: false positive

These are represented using the confusion matrix
On horizontal axis: true values
Vertical axis: predicted
Diagonal represents the well classified variables in dataset

**Accuracy**

- SUm of true positives and true negatives, over the sum of everything (eg. true positives, true negatives, false positive, false negative)
- However, you can still get a high accuracy although the model is imbalanced (eg. 99 false negs and 0 true positives)


**Recall**
- measures ability of model to detect occurence of a class
- using TP divided by TP and FN
- But that model accepts many false positives 
- Good to detect if you're missing out on TPs in precision metric

**Precision**

- Ability of model to identify TPs.
- TP/ TP+FP
- eg. so 67% of the time you will get a TP

**F1 Score** 
- Combination of precision and recall
- Good to have a rough estimate of model performance
- F1= 2x (precision x recall)/(precision + recall)
- So F1 very much influenced by low values

**To sum up:**

Use Accuracy when you have balanced classes and predicting each class is
important

👉 Use Recall when it is important to identify as many occurences of a class as possible.

👉 Use Precision when it is important to correctly identify the positive class.

👉 Use when you want a generic metric to compare across models and dataset


**Precision-Recall Tradeoff**

- inverse relationship between precision and recall 

**Receiver Operating Characteristic Aread Under Curve (ROC-AUC)**
- true positive rate = sensitivty = recall= TP/TP+FN
- Want true positive rate to be higher than false positive rate
- As it's a curve you can look at the area under the curve which gives an indication of overall model performance
- If model B has a lower AUC than a model A, then model B is closer to the line whereby TP=FP (which is where we don't wanna be)
- Here you can't adjust threshold, this gives a clear comparison of (binary) classification 

## Decision Trees ##

- Decision Trees are hierarchical supervised learning algorithms.
- Classification and Regression
- Non-linear modelling
- Break down the data through binary decisions

**Jargon**

- Root node: top part, then splits into true and false -> internal node -> leaf node
- NB: You don't 'train' decision trees, you 'grow' them
- Gini Index: ability of each feature to separate the date, the lower the score the better

**Training**

Tries all combinations of (feature, threshold) tuples - each would split the dataset into
2 child nodes
For each combination, compute weighted average gini index of both child nodes
(weighted by number of instances)
Select (feature, threshold) yielding the lowest index (i.e the "purest child nodes")
Split dataset in two using this rule. Repeat step 2 for both subsets.
Stop when no feature improves node impurity

Threshold is done by algorithm can't change it (rip)

- Decision treese are almost always overfitting so need to tune them
- Controlling the splitting is a way to control that

- ```min_sample_leaf``` : The minimum number of samples required to be at a leaf node

👍 Advantages

- No scaling necessary
- Resistant to outliers
- Intuitive and interpretable
- Allow feature selection (see gini-based feature_importance_ )
- Non-Linear modelisation


















