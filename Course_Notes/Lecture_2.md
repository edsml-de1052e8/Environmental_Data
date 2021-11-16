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
























