# Lecture 12: Afternoon Practical Lecture

- A digital image is not a matrix but an array (2D) of numbers in lines and columns or raster dataset
- Display this in monochromatic display (black and white)
- Implemented by converting DNs to electronic singals of a series of energy levels to generate different grey levels to form the monochromatic image display
- Most image encoded as 8bit integeres 
- Tristimulus colour theory and RGB colour display: equal mixtures of the 3 primary colours are white or grey.

**Color composities**

- Simulated True Colour compositie: display of 3 image bands red, green and blue spectral ranges in RGB
- False Colour composite: image bands displayed do not match the spectra of these three primary colours
- Pseudo color display: displays monochrome image as a colour image

**Contrast Enhancement (Point Operations)**

- Also called a radiometric enhancement or histpgrsm modification 
- This transforms ...

- Every image will have a unique histogram but not every histogram has a unique image
- Contrast enhancement should *not* change the information in the histogram
- Also may want multiple occurences to stretch the function
- Alternative is to create a Look Up Table (LUT): point operations, stretch values in the y column, and inout values in x

**Linear contrast enhancement (LCE)**
- Simplest and most effective contrast enhancement technique

**Piecewise Linear stretch (PLS)**
- For contrast enhancement and thresholding. Can be used this double peaked histogram to mask partd of the image.

**Logarithmic & Exponential CE**
- Streches out histogram if data is skewed ot the left
- Exponential contrast enhamcement: same but if data is skewed to the late

**Balance Contrast Enhancement Technique**
- Colour bias is major cause of poor colour composite image w/ coefficients based on min, max and mean of high input X

- When you do a color composite you are normalising all the other data

**Cut-off Clipigng**

-








































