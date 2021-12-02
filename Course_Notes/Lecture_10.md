# Lecture 10 : Seismic Data II


- To convert time on y axis to depth -> formula v=d/t 
- inline: left to right on 3D seismic model
- crossline: along the depth z from middle to deeper in diagonal (only in 3D)

Sampling (Digitzation)
- having a sample in 4ms period allows the conversion to create a wave of 20 Hz (?)
- 3D volume: 10 km x 10 km at 25m CDP interval (aka inline/crossline interval) contains 400 x 400 traces
- For time smaples recorded every 4 ms for crustal scale surveys that results in 6.4 x 10^8 samples for our 100 km2 3D seismic survey
- Viewing it: in vertical view
- Time slice 3D: is good for detecting faults that are not very deep
- Variable density plots: take amplitude plots and gridding them on the 'wiggles' (white is zero amplitude)
- Dynamic range: note that it is important to use the range of data that has good min and max otherwise data will show as uniform colour

**Data Format**
- SEG-Y file format: established back in 1975 by the Society of Exploration Geophysicists to store seismic data
- Built for reading and writing data to tapes, but not efficient for viewing inlines, xlines and time slices
- SEG-Y mostly contains trace data and some headers: a text header, binary header, a header for each trace
- Converting SEG-Y: need to convert SEG-Y to a format that is more efficient for viewing inlines, etc and do calculations with it eg. ```segyio```
- NB: data loader problems will occur if the data is not a perfect cube and inline/xline spacing is not regular

**Data Access**
- Seismic data is often proprietary although after a moratorium period academics and industry are often required to make data open access
- No single centralized location to access these datasets
- The Marine Geoscience Data System has loads of academic datasets

- Recognising inline: x axis and y-axis, with geographic location at single depth value -> dip in section

**Uncertainty in seismic interpretation**

- It is subjective: different people will interpret the same section differently

**Geologic features in seismic data **

- Vertical aggradation: sedimentation in areas of high relative sea level eg. there is lots of accomodation space for sediments to fill
- Angular unconformity: (two types) surface of erosion or non-deposition that separates younger less-tilted strata from older more steeply dipping rocks. This is proof of sea-level fall.
- Down-cutting unconformity: surface of erosion or non-deposition separating younger strata from older rocks. Caused by changes in SLR (may be caused by tectonics)
- V shaped valley:  formed by river
- U-shaped valley: wider at the base, after carving by glacier 
- horizontal slice helps to identify these patterns
- Active faults: need to know the different stratas, figure out their length and so slipping rate to know how much of a hazard it will be
- Inactive faults: buried and aren't deformed

- Structure Maps: using one time stamp, old DEM style cut (?)
- Picking techniques: pick a window centered around seismic event to be precise about making it into a section. But be careful in setting the window as a too narrow window will hide faults but too big will lead to mixing of faults 
- 
































