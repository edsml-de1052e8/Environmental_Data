# Lecture 4: Fine Tuning Models


Generalisation: applyt to train set but needs to be applicable beyond!
But there will be a trade off between bias and variance
- bias: will fit to datapoints, curve will go through all points but if you add an extra one then it won't mark it -> underfitting
- variance: smoother curve, doesn't go through all data points. -> will cause overfitting


**No free lunch Theorem**

- Some models oversimplify, while others overcomplicate a relationship between features
and target
- It's up to the data scientists (you) to make assumptions about the data and evaluate
reasonable models accordingly.
- There is no one size fits all model

**Learning Curve**

- Learning curves are used to diagnose three aspects of model behaviour on the dataset:

-> Underfitting

-> Overfitting

-> Whether the model has sufficient data to learn the patterns of the dataset

Learning curve: looks at training set (used to fit model), make a predicition for it  and the validation set (not training)
NB: keep validation size set constant, not changing it
- Adding more samples, mean that validation set will be better fitted and able to capture trend correctly
- At some point the learning curve will flatten out when there is no need for more training points
- At some point validation will converge with training points, which means that training data points are generalisable

How do you calculate score?
Is the validation set always 'the truth' can we question and test whether the validation dataset is valid?

**Bias-Variance Tradeoff**

- Measuring the error on an unseen Test set
- Total Error = Bias
2 + Variance + Irreducible Error
- as you increase model complexity, you decrease bias but will increase variance
- black line is the total error 
- Want to be where total error is at its minimum
- Best model complexity is the one reducing the Total Error on a unseen dataset
- NB: don't touch test until the model is fully formed
- Don't use the test set but a Validation Set for this!

- Can use holdout method
- Even better: cross-validate using train set, instead of a using single holdout val set


- If you have a lot of datapoints only then can you deal with more complex models
- More than 100,000 datapoints: Parametric models (SGD, Neural Nets)
- Less than 100,000 datapoints: Non-parametric models (KNN, SVM, Decision Trees)

- Get more observations
- Feature selection (manual or automated)
- Dimensionality reduction (Unsupervised Learning eg. PCA)
- Early stopping (Deep Learning)
- Regularization of your Loss function

**Regularization**

- Regularization means adding a penalty term to the Loss that increases with
- Calculated using penalties of beta
- NB: regularization only affects coefficient not the intercept

👉 Penalizes large values for

👉 Forces model to shrink certain coefficients or even select less features

👉 Prevents overfitting

Two famous Regularization penalties:
- Lasso (L1): adds alpha (hyperparameter) times sum of the absolute error of beta
```lasso = Lasso(alpha=0.2, max_iter=1200).fit(X, Y)```


- Ridge (L2): same but squared

```ridge = Ridge(alpha=0.2, max_iter=1200).fit(X, Y)```


- Introduces the new hyper-parameter :
- Dictates how much the model is regularized
- Large force model complexity and variance to decrease, but bias increases
- Notice starts from , i.e. intercept coefficient is not penalized
⚠️ Always scale your feature before regularization to penalize each fairly

**Finding Hyperparameters**

- Grid search method: Explores different hyperparam value combinations to find those optimizing performance, always done using validation set. 

Select which grid of values of hyper-parameters to try out
For each combinations of values, measure your performance on the validation set
Select hyperparams that produce the best performance

``` sklearn.model_selection.GridSearchCV```

- all the methods in the model eg. Ridge () such as alpha, max_iter or solver are considered hyperparams
- Finding best scores and hyperparams:
```search.best_score_```

```search.best_params_```

```search.best_estimator_```

**Limitations**
- Computationally costly
- The optimal hyperparameter value can be missed
- Can overfit hyperparameters to the training set if too many combinations are tried out
for too small a dataset

**Random Search**

- Randomly explore hyperparameter values from:
- A hyperparameter space to randomly sample from
- The specified number of samples to be tested
- scoring parameter is v important: if you want to maximise recall choose recall, r2 etc 
- Needs to import ```from scipy import stats```
- 'alpha': stats.loguniform(0.01,1)```
- Think of number of iterations as the number of models you want to build

- Using a probability distribution in RandomSearch
- ```dist = stats.loguniform(0.01, 1)``` on log scale
good for things that vary over order of magnitudes 

### Pipelines###

- **Pipelines**: chain operations together in sequences
- makes your workflow easier to read, and easier to make same transformation on trainsets
```from sklearn.pipeline import Pipeline```
NB: in pandas a datatype of the form 'object' is usually a string
- Pipeline: basically in the form of a list of tuples with the name of objects. 
- Note that the order in which you start your pipeline and input commands are the steps appied to the data.
- in order to check what steps are inputed in your pipeline then use ```pipe[1]``` with this being the second step
- Anything in pipeline cna be accessed by name

```pipe = Pipeline([```
``` ('imputer', SimpleImputer()),```
``` ('scaler', StandardScaler())```
])```



```# Fit the pipeline```
```pipe.fit(data[['dmin']])```
```pipe.transform(data[['dmin']])```
```pipe.fit_transform(data[['dmin']])```

- You can also put your own functions in it. 

**Column Transformer**
- When you're not using features the same way
- Apply specific changes to specific columns in parallel
- A Pipeline object can be passed in ColumnTransformer and vice-versa
- input then scale numerical variables, encode categorical variables

```preprocessor = ColumnTransformer([('num_transformer', num_transformer, ['depth','gap','rms']),```
 ```('cat_transformer', cat_transformer, ['type', 'magType'])])```

- all the features that were not included in our list have been removed. To keep them, use the
option "remainder='passthrough'"

- Can also apply column transformers based on data types, instead of doing manually:
```from sklearn.compose import make_column_selector```
- Since it's a model, we can also cross-validate the pipeline and also use grid search! 

**Suport Vector Machine (SVM)**
- What's a good decision boundary for **classification**?
- The hyperplane that generalizes best to unseen data is the one that is furthest from all
the points (maximizes the margin), the one that maximises their distances (known as the 'street')
- The points on the margin boundary are called support vectors
- Finding them is a convex optimization problem (one single best solution)
- Maximum Margin Classifier algorithm
- Max Margin is super sensitive to outliers
- It overfits to the training data

- For generalization purpose, we may want to allow some points to be inside the margin, or
even on the other side of the decision boundary. Allow them to be misclassified basically
- Using a soft margin classifier using penalty for the points that are misclassified
- The Hinge Loss is the penalty applied to each point on the wrong side

- The deeper a point lies within the margin, the higher the loss
- The penalty is linear from margin all the way to the clssification, like MAE

- Hyperparameter C for this purpose: 
- Stength of the penalty applied on points being on the wrong side of the margin
- The higher C , the stricter the margin
- A "maximum margin classifier" has C = + inf
- The smaller C , the softer the margin, the more it is regularized
- C similar to in Ridge

```from sklearn.svm import SVC```
```svc = SVC(kernel='linear', C=10)```

```from sklearn.linear_model import SGDClassifier```
```svc_bis = SGDClassifier(loss='hinge', penalty='l2', alpha=1/10)```
Here alpha is 1/C but does the same

- IN SVM, all vectors require scaling
- General rule of thumb: scale everything apart from decision trees

**SVM Regressors**
- Reverse the objective:
- Classification: fit the largest possible street between two classes
- Regression: fit as many points as possible *within* the street
- For regression: parameter E epsilon controls how strict your margin is
```from sklearn.svm import SVR```
```regressor = SVR(epsilon=1, kernel='linear')```

-> For the assessment: not on lecture 3

















