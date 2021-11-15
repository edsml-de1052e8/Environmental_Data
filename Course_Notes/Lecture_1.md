# Introduction to Machine Learning & Pre-processing




- Machine Learning: area of computation


- Unsupervised learning vs Supervised learning
- Unsupervised not covered but includes clustering, dimensionality and anomaly detection
- Supervised: ranking, classification and regression

- features: numerical data that you give in as input, the x.
- samples: rows/observation

- Scikit-learn: ML library
- organised by modules, with each containing classes
- NB: don't import Scikit in its entireity

- Workflow: usually is an iterative loop, sometimes when you're not satisfied with modelling outputs
come back to data prep (eg. data processing, feature extarction etc)


### Data Preprocessing
- Data exploration: plot your data to see what it looks like
- Cleaning: steps include -> removing duplicates, missing data, outliers, scaling the data, balancing dataset
- Feature engineering
- Feature selection: which are the variables/x that we are selecting

**Duplicates**

- it's issue to be removed before splitting the dataset, do it early so this it doesn't affect results
- Note that you should be able to run code form top to bottom
- ```data.duplicated()``` outputs True when there is a duplicate (1 and 0 for False)
- ```dara.drop.duplicates()``` to remove
- note that it just creates a new dataset or version of data, doesn't change it. 
- This means that you need to assign it to a new variable UNLESS you use ```data.dropduplicate(inplace = True)```

Keyboard shortcut:
- press m and enter -> changes jupyter notebook to markdown
- escape -> to get out of cell
- shift tab : gives the params that you can code

**Ensuring Generalisation**

- Performance of ML model evaluated based on capacity to generalise on unseen data
- So need to test it
- Split it into training set and test set
- All further transformations on training set 
- Test set 
- Usually the testing data is not all 'lost' you will use it again later
- Use 70/30 split

**Splitting** 
- using skleanr.model_selection import train_test_split
- split into train and test

- NB: using ```data.copy``` ensures you're not messing your og data

**Training & Scoring**

- in Sklearn training is called 'fit' : ```model.fit(X,Y_variabels)```
- ```model.score``` gives the RMSE of data


- Cross validation: used on train dataset, not used for whole dataset validation. Dataset is split into K number of folds
- Trains an algorithm for each K
- ```cross_validate(cv=5``` for 5 folds, will evaluate 5 folds and give the scores as an array from 5 folds, they all vary!
- can also take the mean of the results
- Avoid naive Python instead use np or pds
- The more K the more submodels to score from
- rule of thumb: K= 5-10

**Missing Data**

- NaN (not a number)
- large negatives
- ?
- infinity


- Handling missing data: be critical when handling missing data, dropping or filling 
- Can change N/A categories in some categories with 'Others' if it makes sense
- Greater than 30% data missing maybe drop them

**Imputer**

- Tool to replace missing values by strategy of choiceeg. mean, median etc
- imputer can be used to replace missing values in dataset with specific strategy for example 
- ```transform``` function replaces values using previously defined startegy

- Do that before splitting!

**Outliers**

- They affect distribution and patterns, tendency metrics like mean, ML model performance
- Use your knowledge to determine if it is an outlier or just a rare observation

**Feature Scaling**

- Requires you to fit all features on same scale, otherwise creates different weigthing 
- scaling to smaller magnitudes improves computational efficiency
- increases interpretability of coefficients
- To scale you can: 

**standardise data** z= (x-mean)/std
- Good when data is normally distributed, but doesn;t ensure everything is between 0 and 1 and v sensitive to outliers

**normalise**
- puts all data between 0 and 1: (x-xmin)/(xmax-xmin)
- but doesn't correct skewness of distribution or reduce effect of outliers

- Scaling in Sklearn using ```StandardScaler()```
- Robust scaling: takes the interquantile, good if your data is non-Gaussian and don't want to change that. Using ```RobustScaler()```

**Dataset Balancing**
- ML learn by exmaple so underepresentation will be an issue
- 30-70 split for binary classification would be considered imbalanced

- Undersampling: probs better than oversampling bc you're not repeating data in train and test
- Oversampling: kind of like replicating datapoints, data leakage
- Only use balancing techniques on training set

- SMOTE: oversampling algorithm generating minority instances frome existing ones

**Feature Engineering**
- Preprocessing category including encoding, discretizing and creating new featueres
- Target encoding: assing number to each category eg. mangrove = 1, forest =2, water =3
- But machine will probs think that mangrove is less than forest and latter less than water (despite being wrong) -> ordinal encoding
- Alternative: feature encoding/one-hot encoding so one feature per row takes 1 value and the other take 0 values eg. mangrove =1 forest and water take 1 until next row with forest= 1 and rest = 0

- Command uses ```OneHotEncoder```

**Discretizing/Binning**

- Useful for turning regression task into classification task
- Can split data into cutoffs eg. mean or low/high

**Creating new features** 
- potentially improve performance

**Feature selection**

- As the number of features or dimensions grows the amount of data grows exponentially eg. 5 in 1D, 5^2 = 25 in 2D system, 5^3 in 3D etc

- Feature Correlation: high correlation = redundant info
- Pearson Correlation 
- To look at correlation of 2 features: can use ```unstack```for each row you get correlation for each column
- try to keep the feature that has the highest correlation with target variable (?)

**Feature Permutation**
- 2nd feature selection algorithm evaluating importance of each feature predicting the target
- Trains and records test score of base model containing all features
- randomly shuffles (permutation) feature within the test set 
- records new score on shuffled test set
- compares new score to original score

**Reducing Complexity**
- most simple solution is the best solution, reducing number of features makes model more interpretable


#### Algorithm of the Day: Linear Models ####

- Oridnary least square (OLS) regression: use the beta that minimises residual sum of square
- Multi-variate linear regression: with more features, (multi-features/vector of dimensions)


**Logistic Regression**
- Want to predict whether class is 0 or 1. Can be done using logistic function (aka sigmoid function)
- odds: probability/1-probability
- logit function gives you logistic regression is linear system (?)
- Logistic regression can also be used for multinomial functions

- Typically apply threshold of 0.5 to determine if it's 1 or 0 













