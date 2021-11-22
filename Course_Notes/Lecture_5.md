# New Module: Climate Data and Models
### Lecture 5: 

- CMIP: Climate model Intercomparison Project
- 2 sources of errors: natural variability and model errors 
- Current one: CMIP6

- Ensemble runs: running multiple models with similar parameters
-> perturbed physics (eg. where do you put the clouds in the model) + Initial condition ensemble


**Climate Models**

- Reminder that models are not reality


- First thing when building a model: an understanding of the environment eg. physics, requires equations (differential equations = hypotheses about underlying physics)
- Have to parametrise it, requires initial and boundary conditions 
- A model aims to solve an integral with range as boundary conditions
- Need for a grid as well, has to be both spatial and temporal grid -> discretising earth basically 
- Discretisation: choice of discretisation affects the development of the model 
- Choice of solvers will affect quality of model
- Requires use of Forward Euler but could be smthg else
- Can also take centred difference which requires knowing about more things from more points
- Also need to define time and space scales 

- As there are about 60 centers that do climate model, remember that they all use different discretisation techniques
- Coupling of energy systems is vital (coupler): interconnection of energy momentum and mass (eg. water and carbon dioxide etc)
- Modules are ran independently, but every so often are interfaced and exchange info through the coupler to calculate exchange fluxes
- Challenges: grids of different modules may not match 

Reminder about models:
- all models are wrong and the main goal is not data fitting to be perfect
- models can be wrong in different ways, main skill of analyst is to interpret results less so how to model (eg. computer science, maths).

**Model Resolution**

- Increasign complexity: means more processes are described
- Increasing spatial resolution:instead of complexity, so wil account for turbulence, but increases time, memoty and computational cost
- With decreased time-step , 16x time slower and more demanding


---

Data often come aggregated and compressed. These will typically have the following suffixes:

- .tar: The .tar suffix represents an aggregation of data, i.e. many files grouped togeter into a bundle of joy called a 'tar ball'. 'Tar balls' have to be 'untarred' (disaggregated) before being usable.

- .zip, .gzip, ...: This relates to data compression (this is different than aggregation). Compressed data have to be uncompressed before being usable. Uncompressing will increase the size storage requirement of the data! Because they are smaller, it is convenient to exchange compressed files.

- TEXT: Files in text formats, typically encoded as ASCII or Unicode (often UTF-8, or UTF-16), simply have bytes that can be interpreted as text characters. ASCII represents the first 128 charcters of UTF-8, so ASCII is a subset of Unicode. ASCII was developed as 7-bit code, but since UTF-8 kept the ASCII definitions when moving to 8-bits, UTF-8 (and subsequent) are backwards compatible with ASCII. Text formats are very attractive and useful as the file content is directly human-readable but this only works well for small files because data storage of such data is inefficient.

- BINARY: More commonly, we will encouter files in binary formats. Sadly, binary files are not human-readable. They need to be interpreted, using sets of rules set by whoever prescribed the format. These rules have to be known to decode the data effectively (this can be a source of problem...and cause for frustration!).

Some of the most imporant, or common, file formats in climate studies are:

- .csv: These are comma-separated-values,i.e text separated by commas. This format (or the related tab-delimited text format) is ypically used for small datasets, such as when saving an Excel spreadsheet into a format useful for other programmes. Certain data-loggers can also produce text-based datasets. Data in this format will tend to be in the form of small tables or as 1-D data, such as time-series data.

- .hdf: The so-called Hierarchichal Data Format is the format commonly associated with satellite imagery, where they typically hold raster data. HDF files tend to be very large and can have quite complext structure. The current version is HDF5, which differs from legacy HDF4. Common HDF file suffixes are: .hdf, .h4, .hdf4, .he2, .h5, .hdf5, .he5. pandas is able to read HDF data into python using pandas.read_hdf. The more specific h5py python package (HD5 For Python) could provide more control, if needed.

- .nc : NetCDF files are a typical format for gridded datasets with more than one dimension (i.e 2D to ND data), for example data with a latitude, longitude, depth/altitude and certain values. It is the data currency format used to exchange climate model outputs. Note, this does not mean that raw output of climate models comes as .nc files. Generally, models use their own binary formats during computation, to improve speed and storage. Results are only transformed into convenient .nc format at the end, where the goal is data communication and interpretation. The xarray python library is tailored to work with netCDF data formats.

- grb: GRIB files, which stands for 'GRIdded Binary' or 'General Regularly-distributed Information in Binary form', are often used in meteorology. They are the types of files used by ECMWF. There have been 3 versions: i) version 0 is legacy, no longer in use, version 2 is slowly replacing version 1, but version 1 is used by most meteorology center today. The cfgrib python library from ECMWF will help translate .grb into xarray, netcdf or hdf. Alternatively, the pygrib python package will provide a way to read .grb files, and modify existing ones, but not create them.




**Climate and Forecast (CF) Metadata Conventions **
- NetCDF is one of the most common data format used to store climate data. NetCDF files allow the user to insert metadata in the data file by design, ensuring the data file is self-describing (amongst other properties).


-  CF Conventions aim to ensure that files contain sufficient metadata that they are self-describing in the sense that each variable in the file has an associated description of what it represents, including physical units if appropriate, and that each value can be located in space (relative to earth-based coordinates) and time

- Variables: NetCDF variables are a bit like python arrays from numpy. Variables can have any number of dimensions (i.e. 1D, 2D, 3D, 4D, ...). 
- One can create a new variable with Dataset.createVariable, where we must provide a name and a data type for the variable. The dimensions of a variables are provided as a 'tuple'. One can also create a 0D variable (i.e. a scalar variable), in which case we simply leave out the dimension information.

- Variable names can be changed with ```Dataset.renameVariable```

- Attributes: The last category of information required are 'attributes'. Attributes can be `global' or 'variable'-specific. 'Global' attributes are for the whole Dataset or the group. 'Variable' attributes only inform on a specific variable (or coordinate variable). It typically represents metadata.

Dataset.ncattrs can be used to retrieve attributes from a NetCDF file. Alternatively, the __dict__ attribute of a Dataset, Group or Variable will return the name/value pairs for all the attributes.

- Slicing and indexing: Definition of slices are similar to numpy, i.e. start:stop:step triplet can be used, and so can an integer index i to take the i-th element, blicing rules in NetCDF4 works a little differently than in numpy. For example:

```temp[0, 0, [0,1,2,3], [0,1,2,3]].shape```

returns (4,4), so this would be a 4 rows x 4 column array, corresponding to the first time point and the first level only.

In numpy, this would result in only 4 elements (e.g. a vector with 4 elements).


- Masks: Masks are often used in climate science data to separate data from different regions (e.g. ocean vs land, etc.). By default, the python NetCDF4 API returns numpy arrays that mask entries that equal the missing_value or _FillValue attribute. One can force unmasking (i.e. return all values, regardless) using the Dataset.set_auto_mask method. To switch back auto-masking, use Dataset.set_always_mask



















