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












