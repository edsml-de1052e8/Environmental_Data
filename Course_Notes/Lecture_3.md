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



















