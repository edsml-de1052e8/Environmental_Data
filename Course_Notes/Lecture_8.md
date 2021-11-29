# Lecture 8: Rivers & Landscape


**Morphometrics**

- Describing a stream: Strahler Stream Order
- Aims to describe the position in the stream.
- 1: higher part of the stream, the head
- 2: where 2 channels first come together
- 3: next time the channels from 2, the second order channels, flow together

- NB: only when the channels have the same order and join can you augment the river order

Horton's Laws of stream order
- Number of streams of given order related to order
- Exponential relationship between stream order and stream length
- other laws for mean stream length, law of basin areas, law of stream slopes

Hack Law:

stream law and basin area follow a power law relationship
k: constant
h: typically undere 0.6

- Erosion as a function of slope and upstream area

Fluvial data:
- HydroSheds

- D8 algorithm: flow is routed to one of 8 adjacent cells depending o steepest slope
- So steepest slope will be drainage patg
- But note that erroneous sinks must be filled first. When data has a break/v steep slope followed by ghigher elevation, which the algorithm  will interpret as sink
- To avoid that you have to fill in the break BUT note that you are tweaking the data
- In that algorithm flow only goes in one direction but flow is often divergent flowing into multiple adjacent cells
- Some advannced algorithms deal with that such as the D algorithm

**Landlab**

LandLab is 'a python toolkit for modeling earth surface processes'. It provides open-source and (mostly) user-friendly functionality to wide-range of surface-process related tools





















