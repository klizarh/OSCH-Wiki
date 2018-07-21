# Recipe
A recipe is a protocol giving instructions for growing a plant.  These instructions are for both the people involved in growing, as well as abstract instructions for controlling a growth chamber.
A recipe should state "what" should be done and not "how"; the how part should be left to the implementation of the growth chamber.  The recipe should state the "daytime target temperature is 24 degrees Centigrade", the implementation is how the thermostat controls exhaust fans, air conditioning, water chillers, or other sensors and actuators.

## Recipe Parts
* Purpose: a high level description of what will be tested or accomplished
* Plant: genus/species, etc.
* Agronomic Activities
  * Life Cycle Activities
    * Planting
    * Germination
    * Vegetative Growth
    * Pollination
    * Flowering
    * Fruiting
    * Harvest
  * Treatments
    * Nutrient
    * Light
    * Temperature
* Environment: Growth chamber to be used (which is a defined set of equipment), or specifications for particular equipment.
* Research Expectations:
  * Data that should be collected
  * Protocol to use
  * Expected results