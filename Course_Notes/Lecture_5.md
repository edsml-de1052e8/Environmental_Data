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



















