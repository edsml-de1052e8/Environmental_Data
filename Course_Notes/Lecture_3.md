# Lecture 3 


**OLS (Ordinary Least Squares)**

- Trying to find the beta that minimises error
- || x || means the norm 
- There exists mathematical solvers to minimise Beta

- Gradient descent: calculate the slope (so derivative) of the Loss function.
- Loss function is the error
- then move by a step in opposite direction of the derivative (because we want to go down the gradient)
- one epoch is the adjustement of each parameter
- as loss approaches minimum, the slope gets smaller. So away from it you take big steps

Stopping Points:
- When steps get really small (depends but eg. 0.001)
- When steps reach maximimum (eg. 1000)

- Descent always converges faster when features are scaled


Loss is not the same as performance metric

**Performance**

- Loss is used to fit the model, and even if the loss and performance metric may be the sme (eg. MSE) the loss needs to be differentiable so for it to be smooth.
- Accuracy or recall for example can't be loss
- RMSE, absolute mean error can be tho

**Regression Loss Functions**

- L1 is the mean absolute error
- L2 is the Mean square error 
- Errors and outliersare a problem for MSE as it increases them 
- MAE requires learning rate n which decreases at every epoch 

**Huber loss (mixed L1 and L2 losses aka Smooth Absolute)**
- Uses 1 MAE when appropriate and switches to MSE when error becomes small

**Classification Losses**
- we can apply sigmoid to our hypothesis function
*insert maths*

**Likelihood function**
- In binary classification the outcomes follows a Bernoulli distribution and we can write our probability function as follows:
P(Y= y)| X =x) = sigma(beta^Tx)^y [1-sigma(beta^T x] 

**Log Likelihood**
- Hard to look at sigmlid function, easier to put in log scale -> log likelihood
- log likelihood/ cross entropy loss is the negative of this function 
- NB: lossfunction is valid for one data point, vs. cost function is the average of all the losses -> some use them interchangeably but there is a slight difference
- Log loss is the negattive of the log likelihood so that we can maximize it with gradient descent.

**Algorithm of the Day: K-Nearest Neighbour**
- KNN is a non-linear distance based model capable of solving both regression and classification tasks
- Scaling is vital here
- Look at K closest samples to make a prediction
- What you do: calculate the distance from sample and all the other samples in the data set, thn look at the k nearest samples 
- look at class at your k and determine what your og sample is
- Choosing k: optimal k will vary from dataset to dataset
- Lower k values, less observations to use to make a prediction, prone to overfitting
- 



















