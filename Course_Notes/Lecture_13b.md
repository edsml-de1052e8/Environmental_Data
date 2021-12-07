# Lecture 13b: Colour Transforms

But for colour perception, a colour is more intuitively and more quantitatively described in terms of
three variables.
• Hue: colour spectral range
• Saturation: colour purity
• Intensity: colour brightness (energy level)
The RGB-HSI colour coordinate transformation within a colour cube is similar to a transformation
from three-dimensional Cartesian to Conical (or 3D polar) coordinates.
We can exploit this relationship between RGB and HSI with two key benefits:

1. Decorrelation Stretch – for image spectral enhancement (2 common methods)
2. Data fusion – for sharpening image texture (3 common methods)


Any colour in a 3-band colour composite is a vector within a colour cube with edge length of 255 (for 24 bits
RGB colour display).
• The major diagonal line connecting the origin and the furthest vertex is called grey line.
• Intensity of a colour vector P is defined as the length of its projection on the grey line (OD),
• The hue is the azimuth angle around the grey line (a), and
• The saturation is the angle between the colour vector P and the grey line (j).


**Spectral Enhancement via decorrelation stretch**

- High correlation generally exists among spectral bands of all multi-spectral images
- HSIDS enhances colour stauration of a colour composite image and thus improves the visual quality on image spectral information without significant distortion of image spectral characteristics. 

**Direct Decoloration Stretch technqiue**

- Performs a saturation stretch without using RGB-HSI and HSI-RGB transformations.

• DDS achieves the same effect as the HSIDS but invol

The final colour saturation of the output image is controlled (scaled) by the
achromatic factor k.
• As already stated in the HSIDS, the 3 bands for colour composition must be well
stretched (e.g. BCET or linear stretch with appropriate clipping) before the DDS
is applied.

**RGB-HSI transformation for pan-sharpening**

- Geo- or co-reference a low- and a high-resolution image of the same area (e.g. a
Landsat 30 m with a SPOT panchromatic 10 m)
- RGB-HSI transformation on the low-res colour composite image
- Replace low-res Intensity component with high-res image
- HSI-RGB transformation for display

• The fused or pan-sharpened image is a mixture of low-resolution spectral information and highresolution spatial and textural detail
• Overall resolution is apparently improved but colour distortion is unavoidably introduced.
• The colour distortion may be significant if the spectral range of the three MS colour
composite bands is very different from that of the Panchromatic band, i.e. the intensity component
(as the summation of the three MS bands) is different from the Pan that is used for intensity
replacement. NB look carefully at band widths first



























