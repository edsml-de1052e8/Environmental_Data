# Lecture 7: Introduction to Spatial Analysis

- **Contouring** : guessing what the measured scalar or vector field looks like where it was not sampled
- One can either interpolate between available samples or fit a function that minimizes the error between the predicted values and the measured data.
- Note that interpolation doesn't filter the noise out, regression does. Interpolation is better when you have a lot data.

**Surface Interpolation**

Just as it was the case for the 1D case (remember interp1d), 2D interpolation can be used to fill in the space between existing control data points and predict values for the field at given query points.
- control points: points you have info for
- query: points you want to interpolate or ge tnew value from]
- Interpolation is not the same as fitting: here surface will pass through every single control point
- command : ```.interp1d``` 

There are two types of interpolation problems:

- interpolation from gridded data
- interpolation from scattered data (don't do that on bug files = high computational cost in this case)

**Gridded Data**

- Data that is on grid, an ordered sequence of coordinates
- Sometimes you are given just a x and y (in a square array) -> fine that represents lat/long
- However in any other case when the grid is different, you get a matrix of x and a matrix of y (not lat/long)
- Python function: ``` numpy.meshgrid```

























