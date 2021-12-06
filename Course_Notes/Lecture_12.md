# Lecture 12 : Physical principles of Earth Observation, orbits, sensors & resolution

- Main place to go for data format descriptors: GDAL

**Remote Sensing**
- aquisition of infor about an object without physical contact. 
- Usually taking images from spacecraft and aircraft and use images to extract infor about the Earth's surface
- Term first used after first Landsat in 1972
- Now 2000 EO satellites in space 
- Major aspects of EO: physical principles, aquisition, applications and processing

**Type of remote sensing**
- Passive remote sensing: naturally reflected rays are processed. Better during the day, at night only thermal part of the spectrum
- Active remote sensing: satellite actively generating the energy and recording eg. lidar, radar

**Workflow before 2000s**

- EO data collection -> level 0 raw data
- Search & order/pay for raw data -> level 0 binary
- Process and produce GIS ready images
- Interpret & analyse locally

**Today's workflow**
- All the processing going towards server side
- Don't need or have raw data locally 
- Geo coded multitemporal multisource data level1 geotiffs
- ATM: Airborne Thematic Mapper
- Planetary remote sensing: now resolution on Mars is similar to that on earth (can be up to cm)
Venus is v rocky, first optical image form Venera 9 in 1975
- Venus is very interesting because it is a 'hot' world that lost all its water, useful for our future

### Physical Principles 

**Electro-Magnetic Radiation (EMR)**

- EMR is an energy wave propagated through space between electric and magnetic fields c= v* lambda
- High frequency = short wave radiation
- Visible: 300-750 nm
- Visible IR: 0.4-0.9 micrometer
- NIR: 0.75-1.3 microns
- SWIR 1.3-

- Passive sensing: visible to SWIR, Thermal sensing in TIR
- Active sensing: long wavelengths eg. radio, microwaves, 


- EMR composed of many discrete units of matter called photons Q= h*v
- With Q as energy of photons, h as Planks cosnstant and v as frequency 
- So energy changes depending on the frequency used
- Higher frequency, shorter wavelength more damaging to humans
- Stefan-Boltzmann law: black body radiance emittance
- all matter at temperaturre greater than 0 Kelvin emits EMR
- How much energy an object emits is dependent on temperature
- sigma * T
- Wien's displacement law: the hotter it is the short the wavelength and higher the frequency
- lambdam = A/T
- Temp of Earth: around 300K, peak at 50 microns so TIR (outside visible range so can't see it)

**Interaction between EMR and atmosphere**

- Scattering: diffusion of radiation by particles in the atmosphere
- Rayleigh scattering: when particles are smaller in diameter than the wavelength, usually at short wavelength (effective on blue colour hence why sky is blue)
- Where there be no atmosphere such as on the Moon, the sky would be black
- Mie: when particle diameter essentially equals wavelength of EMR being sensed eg. water vapour
- Non-selective scattering: light is blocked or scattered in all directions, particles much larger than the wavelength
- So all these interfere with the amount of energy we have to measure

- SWIR bands can penetrate thin clouds and smoke, so get rid of them for better visibility
- Also problem of cloud shadows

- Absorption: effective loss of EMR energy to atmospheric constituents. Normally occurs at particular wavelengths
- Most efficient absorbers of solar radiation: water vapour, carbon dixoide and ozone

- Older generation sensors were designed to emit blue radiaition so not covering this wavelength
- That was to factor in the Rayleigh scattering
- Now sensors are more efficient at dealing with it 
- Terra Modis has large footprint and covers a lot of wavelengths up to TIR and mostly for global models

- EMR: either reflects, transmits or absorbs when it hits the ground 
- Can be diffuse reflectance (scattering by the surface), reflectance back and transmittance
- Reflectance depends on things such as surface roughness
- Two types of surfaces interacting with EMR: specular aka smooth and diffuse aka rough
- Surface will be smooth depending on Rayleigh criterion wich depends on surface irregularity height 
- Key parameters of spectral properties: spectral reflectance reflectivity of material at particular wavelength
- Albedo: intergral of reflected spectral radiation over spectral range
- Note that at night for passive sensors we can only see thermal part of spectrum (long wave radiation) but geothermal is also produced
- For satellites like Sentinel 2, need to separate daytime heating from nightime heating and compare as these satellites span 24 hours
- Emissivity and reflectance are inverse of each other
- In visible, ocean is black as it;s absorbing light and low reflectance, clouds are white due to high reflectance
- However with thermal sensor, this gives a reversed scaling -> clouds are white because they are cold and have low intensity and emission while land and ocean are darker due to high intensity and emission














