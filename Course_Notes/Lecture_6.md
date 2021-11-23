# Lecture 6: Time-Series Data


- Time series data has: time or index variable or multiple columns that have to be combined to creat the time variable
- other data


- First establish that the time series is regularly spaced

- Stationarity: mean, variance and autocorrelation data structure don't change along time duirng time series.
- In that case you will be looking at 'how often does a specific value come up in the dataset'.
- So by implication non-stationary data: varies across time.
- First order stationary: mean is constant but not the other variables
- Second order stationary: mean and variance are constant but not other variables etc

**Making data stationary**

- Differencing: take the difference between a point at time t and the data at point t-1 and make a new function from it. Doing this through entire dataset the time series could be stationary 
- Another approach is to detrend the data by fitting low order polynomial through data. With regression then take difference between the data and regression prediciton for each time point and work with new data series of residuals
- Can also use LOESS fit of the data (Locally Estimated Scatterplot Smoothing). Sequential regression on small pieces of data.
```LOESS``` package
- NB: pay good attention to the range of the LOESS as this affects the smoothing of the data
- Aim to always make a simplified model of the data, in order to have a calibration model for your data
- ```data.date_range``` creates a time axis for the data (can parametrise the periods and frequency too)
- NB: consider the data you're working, some data cannot be normalised and have equal distribution (eg. when it goes to zero as some environmental data cannot be negative)
- 























