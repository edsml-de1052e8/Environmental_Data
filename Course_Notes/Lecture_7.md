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
- Create vectors with ```np.linspace``` for x and y
- Then use ```np.meshgrid(x,y)``` which will define the matrix with x and y coords 

Note that Python's numpy.meshgrid commmand has an option called indexing. This means that meshgrid can support both indexing conventions:

Giving the string indexing=‘ij’ returns a meshgrid with matrix indexing (row/column)
Giving the string indexing=‘xy’ returns a meshgrid with Cartesian indexing (longitude/latitude) In the 2-D case with inputs of length M and N, the outputs are of shape (N, M) for ‘xy’ indexing and (M, N) for ‘ij’ indexing. This means that the x-axis is first in 'xy', but 'rows' (i.e. y-axis) are first in the matrix case. So 'ij' and 'xy' are transposes of each other. In the 3-D case with inputs of length M, N and P, outputs are of shape (N, M, P) for ‘xy’ indexing and (M, N, P) for ‘ij’ indexing.

**Scattered or Unstructured Data**

- Scattered data consist of sets of points x and y that are not ordered in any particular way.
- To remedy that and interpolate the scattered data based on Delaunay triangulation technique
- command is: ```scipy.spatial.Delauney```
- Delaunay triangulation uses the data coordinates as vortices of triangles
- Interpolation is limited by coordinates on the outside perimeter
- By design, interpolation cannot extrapolate and as such it can only generate guesses for query points located inside the convex hull of the data. 
- The convex hull is a set of points that defines an envelope containing all points.
- ```scipy.spatial.ConvexHull```
- command for scattered interpolation : ``` scipy.interpolate.griddata```
- NB: even if itnerpolation may look good as output eg. cubic, doesn't mean it is for the right reasons -> may be forcing a fit of data on a curve that isn't there
- Can use ```method='nearest'```, ```method = 'linear'``` or ```method = 'cubic'```

**Krigging/Objective Mapping/ Gauss-Markov Regression**

- fitting process constrained by an underlying Gauss-Markov process model, itself controlled by prior covariances

- Variogram: equivalent of auto-correlation but for space
- Krigging requires estimation of a so-called covariance matrix, which describes the relationship between observations.

- nugget: initial jump


## Plotting Spatial Data

- ```Geopandas``` is an open-source python library that makes working with geospatial data easier. It aims to deliver the benefits of pandas to geospatial data.

- ```Cartopy``` is a python package designed for geospatial data processing and mapping. It makes working with various geographical projections easier.

- ```scipy.spatial``` is a component of the popular scipy library. It contains a few handy algorithms to handle and manipulate spatial data, such performing nearest neighbor queries or applying Delauney triangulation, which is useful for spatial interpolation.

- These packages depend on other libraries
- PROJ: library provides methods for coordinate representation, conversion (projection) and transformation. Usually for global scale and projection 
- GDAL allows reading and writing of spatial raster and vector data in a standardised form, and provides a high-level interface to PROJ for these data structures, including the representation of coordinate reference systems (CRS)

**CRS**

Definition of a GRS generally consists of two pieces of information:

- one coordinate system
- one datum


- The datum roots the coordinate system to an arbitrary object. 
- Projections: are a type of conversions. projected CRS are derived from the base geodetic CRS -> derived CRS
- Compound CRS are mixtures of geodetic and engineering CRS. For example, a CRS with latitude and longitude, but with depth (or altitude) in pressure. In this case, pressure (or altitude/depth) is locally defined: i.e. the vertical axis varies with location.
- The most common CRS is the WGS84 system lat-long projection. Also known as code EPSG:4326
- The origin of the coordinate system for WGS84 is meant to be the Earth's center of mass
-  Note that, although it is called WGS84, referencing its origin in 1984, the geoid component of WGS84 is continuously updated, with a latest iteration in 2020, providing a geoid accuracy better than 10cm.
-  CRS can be described in so-called PROJ strings format, in Well-Known Text (WKT) (now also evolved into WKT2), or in Spatial Reference IDs (SRID)
-  NB: EPSG:3857, which corresponds to a mercator projection, used by Google Maps and OpenStreetMap


TricK:

There are many ways to interact with the system: os and subprocess can both be used to achieve this. Here are a couple of examples show how to execute the 'projinfo' command line operation from with python:

```import os```
 
```command = "projinfo EPSG:4326" #command to be executed```
 
```res = os.system(command)```
```#the method returns the exit status```

```print("Exit code: ", res) # print the exit code```


- Trick to make sure the data is next to each other along the 'edges' of longitudes :
- The ```+lon_wrap``` option can be used, however, to specify a different central longitude (different than 0), so +lon_wrap=180 would yield longitudes between 0:360. The +over switch can be used to exceed these limits, which can be convenient when showing certain features near the edges/limits of the maps.


**GDAL**

- C++ translator library for over 200 raster and vector geospatial data formats
- GDAL itself, used for manipulating geospatial *raster* data
- 

**Geopandas**

- Geopandas is aimed to be like pandas, but to work with geodata and shapefiles.

```quiver``` plot: overlays different maps with ticks etc













