# Lecture 13: Algebraic Operations



...

**Image subtraction**
Subtraction is one of the simplest and most effective techniques for selective spectral
enhancement.  produces a difference image from two input images.
It is also useful for change detection and removal of background illumination
bias.
In general though, a subtraction operation reduces the image information and decrease
image SNR. 

**Image multiplication**

Usually used for masking . Y = Xi * Xj
Here image multiplication is performed on each image pixel - band i DN is multiplied by band j DN.
NB: This is fundamentally different from matrix multiplication - remember a digital image is a 2D
array, it is not a matrix.

- Key applications of image multiplication:

a) Masking – e.g. using an image to remove part of another image. For instance, if Xi
is a mask image
composed of DN values 0 and 1, the pixels in image Xj which corresponding to 0 in Xi will become 0
(masked or clipped out) and the other DN values remain unchanged in the output image Y.
• This operation can also be done (more efficiently) using a logical operation of a given condition,
i.e. if ... then … else

b) Modulation – e.g. using one image to modulate another. For instance, topographic shading can be
added to a coloured (flat) map or classified image by using a panchromatic image (intensity
component) to modulate the three colour components (red, green and blue) of the scanned map or to
a pseudocolour classification image as below:

**Image Division (Ratio)**

- Very popular Y= Xi/Xj
- For processing involving image division, certain protection is usually needed to avoid overflow
(where a number is divided by zero).

• A common trick is to shift up the value range of denominator image by adding 1 to avoid zero.
• The output ratio image Y is an image of real numbers instead of integers.

• NB If both Xi and Xj are 8-bit images, the possible output value ranges for Y are 0, [1/255, 1], or [1,
255]. The value range [1/255, 1] may contain just as much information as that in the much wider
value range [1, 255] !

• NB If you then linear stretch the result, you could achieve up to 50% information loss because the
information recorded in value range [1/255, 1] could be compressed into a very few DN levels. So
beware and stretch carefully!

Can think of ratio as a cartesian to polar coordinate system.

Ratio and difference produce a similar output, more a question of which one looks best. Both supress the topography and flatten it out.

Ratio image Y is actually a tangent image of the angle a. The information in a ratio
image is evenly represented by angle a in the value range [0, /2] instead of
in value range [0,255].
• Therefore, to achieve a ‘fair’ linear stretch when displaying a ratio image, it is desirable
to convert Y to a. An automatic linear scale can then be performed as

Ratios are often designed to highlight particular target features in high value DNs.

• Direct stretch of ratio image Y may enhance the target features better, at the cost of losing
the information represented by low ratio DNs.

• Thus it is important to notice that, although ratios TM1/TM3 and TM3/TM1 are reciprocal of
each other and contain the same information, they will be different after linear scale contrast
enhancement!

• NB when you design a ratio, make sure the target information has high DN values in the
output ratio image (more intuitive).

• Ratio is very useful for selective enhancement of spectral features. Ratio images derived from
different band pairs are often displayed in RGB system to generate ratio colour composites.

- For a given incident angle of solar radiation, the radiation energy received by an area of
land surface depends on the angle between the land surface and the incident
radiation.
- Therefore, solar illumination on land surface varies with terrain slope and aspect, which
causes topographic shadows. The DNs in different spectral bands of a multi-spectral
image are proportional to the solar radiation received by land surface and its
spectral reflectance. 

**Topography Suppression**
- Topography accounts for 90% information of a multi-spectral image
- Assuming same material, the impact of the sun on one pixel and the shaded pixel can be mitigated by doing the ratio of these two
- so we get R1i,j =R2i,j


**Spectral Index derivations & Supervised Enhancement**

- Unlimited combinations of algebraic operations can be derived using basic arithmetic
operations and algebraic functions.
- For a meaningful and effective operation, knowledge of the spectral properties of the
target is essential. 

- Vegetation indices
- Healthy vegetation has a high reflection peak in near infrared (NIR) and an absorption
trough in red (R) because of the spectral properties of chlorophyll. 

- Vegetation Ratio Index (VRI): 
Y= NIR - min (NIR)/Red - min (Red) +1

eg. for Landsat TM
Y = TM4 - min (TM4)/TM3 - min (TM3)+1

- Normalised vegetation Index (NDVI): between 0 and 1.
NDVI = NIR - Red/ NIR +Red

- These indices allow for comparison between time at specific place
- Other indices include the Soil Adjusted Vegetation index (SAVI), Normalised Difference Water Index (NDWI), Brightness Index of soils (BI), Normalised Difference Snow Index (NDSI)
- SAVI aims to reduce the effect of soil brightness on the measurement of NDVI for example, as NDVI might pick up the fact that 20% of NDVI is soil eg. in cropland

SAVI = (1+L)(NIR - Red)/(NIR +Red +L)
NDWI = (Xnir - Xswir)/(Xnir + Xswir)
NDsI = (Xgreen - Xswir)/(Xgreen + Xswir)

**Geological indices**

- Iron-oxides are one of the most common and widely spread mineral groups in the natural
environment.
- They appear in red or reddish brown as a result of high reflectance in Red and absorption in
Blue parts of the spectrum. 
NB: these are very sensitive so be careful as to what they pick up that you are not interested in

- Hydrated clay minerals: The typical spectral signature making
hydrated minerals different from
unaltered rocks is that they all have
strong reflectance in SWIR ~ 1.66 μm
(corresponding to TM band 5) and
strong absorption ~ 2.2 μm
(corresponding to TM band 7) – more
on this later
- Thus all hydrated minerals can be
enhanced by the ratio between these
two SWIR bands (TM5 & TM7).








