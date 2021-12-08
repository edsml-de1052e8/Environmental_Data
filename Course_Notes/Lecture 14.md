# Lecture 14: Radar Data


- An imaging radar is an active sensor system
• RADAR = RAdio Detection And Ranging
• Sends microwave radiation pulses to illuminate a ground target area and
receives the returned signals to produce an image 
- Microwave based
- Operates at much longer EMR wavelengths, usually from 1 cm to 100 cm, so
is not subject to any atmospheric scattering and absorption effects

• Radar beam can penetrate thick clouds because the size of water droplets in
clouds is much smaller than the radar wavelength
• As an active sensor, radar can operate in day and night



- Coherent 
- Travel path changes can be measured with the
accuracy of a fraction of the wavelength
4. Very sensitive to water, roughness, soil moisture and
dielectric constant
5. Sensitivity to man made objects „& use of polarimetry) „
6. Subsurface penetration

Disadvantages

1. Complex interactions (difficulty in understanding, complex
processing) „
2. Speckle effects (difficulty in visual interpretation) „
3. Geometric distortions„
4. Complex effect of surface roughness

- Most imaging radars are side looking (SLR)
- Azimuth: travel direction of satellite
- Range direction: perpendicular to azimuth, composed of slant range (how slanted it is) and ground range (circular beam)
- Range is dependent on incidence angle theta which produces a cone-shpaed beam to the ground

**Bands**

- Naming dates back to ww2
- K bands are usually used for telecommunications (shorter wavelengths)
- Sentinel 1 SAR works at C-band (older system)
- S band: not too utilised but ENviSAR by ESA planned to be sent with S-band in 2031
- L and P bands: not too common, but can penetrate through vegetation (longer wavelengths)

- Differences between C band and L band, sensitive to different things eg. crop systems

- SAR signal: amplitude
- Amplitude: measur eof strenght of the signal and includes magnitude and the phase
- The image you look at is basically amplitude
- Smooth objects with SAR will look dark, because of less back scatter 
- Corner reflections and buildings will have more complexity so will appear brighter

**Real Aperture radar**

In the azimuth direction, the image is built in strips corresponding to the pulse number
sequence.
• As the platform moves forward, the radar antenna transmits microwave pulse
beams to scan on one side of the flight path strip-by-strip and meanwhile records
the backscattered signals.
• Thus a two-dimensional radar image is built in ground range and azimuth.

**Synthetic aperture radar (SAR)**

- Essentially processing to ensure you are using a smaller antenna 
- The motion of SAR antenna with a small length of Ds along its
flight path simulates a virtual long antenna Dr

• This enables to achieve a high azimuth resolution Ra much
smaller than the SAR footprint width via a digital signal
processing procedure called matched filtering on the
overlapped footprints based on Doppler frequency shift (higher frequency at the front of beam and lower frequency at the back) df
from the SAR carrier frequency fc

- Equivalent to half of the length of its real antenna. This
means that the shorter antenna diameter of SAR achieves
higher azimuth resolution.

Ra =Ds/2

- The smaller the antenna, the higher the resolution you can achieve

**Ground range resolution of SAR**

- Chirp: multi-frequency pulse, can be ascending or descending (increase or decrease in frequency)
- GR resolution is extracted from the return time of radar echo signal: far range signal returns later than near
range signal. Rr
is generally lower than Ra
- But the precision of recording time differences is limited so to achieve a high ground range resolution, SAR
emits a chirp pulse with a bandwidth of tens of MHz modulating a carrier wave frequency f
c (the nominal frequency of the SAR).
- High spatial resolution in a SAR image is achieved in azimuth direction by Doppler
effects and in range direction by chirp.
- For metre-scale resolution in the image, you would need an antenna with a length of several km!!
- In SAR, a metre-scale real antenna is used on board, while a longer antenna is ‘synthesized’ by
computation, combining hundreds of echoes of the same target acquired from different positions along
the satellite path 
- Using range compression to produce the image

**Distortions**

- The side looking component means more distortion due to slopings of terrains though
- B, a= 90 - beta
- Foreshortening: mountain peaks seem to be leaning to one side, local incident angle is positive, slope will appear compressed and length of slope is not represented correctly
- This is because at points C and D where C is at mountain bottom and D mountain top, both back scatters arrive at same time due to the slope of the emitted wavelength
- Negative layover: reverse
- Shadow: from radar only, Shadowed areas will appear dark on a SAR image as
no energy is available to be backscattered. Radar
shadow is particularly dark because atmosphere does
not scatter micro-wave EMR!

- ERS-1 image shows more distortion
from foreshortening than JERS-1
image because ERS-1 has a smaller
view angle than JERS-1. 
- if you got less mountains and such on other planets then you can use a lower incidence angle

**Interactions between radr signal and ground**

- Since radar waves are coherent (i.e. in phase), the
backscattered waves, from every element in the scene
constructively and destructively interfere with each other,
creating a 'salt and pepper' effect across images, called
speckle noise.
- These can be reduced by filtering - to remove these
high-frequency speckles
- Can also reduce by multilooking, speckles are randomly dsitribtued so they can be reduced
- Need to find a middle point as too manu 'looks' may smooth the image too much
- Demand for higher spatial res reduces number of looks possible
- Corner reflections: eg. in urban area, beam hits flat surface like the road, but then will also hit a building or a tree. 
- Double bounce effect of a corner reflector will result
in the incident radar energy reflect back to
radar antenna directly. 

- SAR image roughness: radar less sensitive in near range then far range. smooth surfaces like mud flats will give a specular reflectance and low radar backscatter while eg. limestone with rougher surface will have higher backscatter
- Dielectric content: affected by soi moisture and water content, tis affects surface brightness

**SAR penetration and volume scattering**

- If the target is very dry and the surface appears smooth to the
radar, the radar energy may penetrate below the surface, either
through:
i. Discontinuous (e.g. forest canopy with leaves and branches),
or
ii. Homogeneous surface (e.g. soil, sand, or ice).
For a given surface, longer wavelengths can penetrate
farther/deeper than shorter wavelengths. 
- Volume scattering: If the radar energy manages to penetrate through the topmost surface, then volume scattering may occur
= Scattering of radar energy within a volume or medium, and usually consists of multiple bounces and
reflections from different components within the volume. 

- SAR imaging can penetrate considerable depth
of dry sand (and ice) -> bc of dielectric constant

- If you use multiple radar then through growing season of vegetation you can notice the differences in scattering

**Radar polarization**

- Polarization refers to the orientation
of the electric field.
- Radar systems can be designed to
transmit/receive microwave radiation
either horizontally polarized (H) or
vertically polarized (V) or both. 
- Also cross polarised (HV)
- vertical polarisation: if it is a bushy crop, nothing hits the ground  so good representation of the crop of interest
- Horizontal polarisation : if it is barley crop, then it may be hitting the crop but mostly the ground

## Applications


- Oil slick detection: Oil slicks appear as dark features because
the oil smoothes out the small waves by increased viscosity.

- On a smooth sea surface, most of the SAR
signal is specularly reflected away from the
antenna, causing dark features.
- Environmental factors, e.g. wind, can alter
the behaviour of the sea in the vicinity of
slicks. 
- In strong wind, the sea surface will
be rough (whether oil slicks or not) and
wind speeds of <8-9 m/s are required for
reliable detection. 

- Sea surface roughness eg. impact of offshore windfarms on sea current

### InSAR

- Interferometry  uses the differential phase of the reflected radiation,
either from multiple passes along the same trajectory and/or from
multiple displaced phase centres (antennas) on a single pass
- Both Amplitude and Phase information are needed for
interferometric processing.
- SAR SLC records both real or in-phase (I) and
imaginary or quadrature-phase (Q) components of
the backscatter echoes, to reconstruct the intensity
and location of each echo.

- Using two coherent beams of radar
energy, from a satellite, separated in
time and space, we can extract the
distance as a function of the phase of
the wave – Differential InSAR
- by using hundreds of SAR images you can track objects which scatter consistently over time
- Now with this you can get analysis of change by 1 mm/year!!

- Can be used to monitor the effect of tunelling on buildings collapsing eg. few centimeters per year on Blackfriars bridge in London
- 
- 






























