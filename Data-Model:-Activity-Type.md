# Activity Type
As previously stated, activities are the heart of Business Process Modeling (BPM) or Data Warehouse modeling.  This is a fractal pattern where an activity is made up of many smaller activities.  A critical part of modeling is determining the boundaries of what to capture and what to leave alone; what is conceptually and logically there, but not worth the time and effort (or interest) to capture.  In a large commercial agriculture operation there would be many details like maintenance records, employee time charting and energy consumption that are critical to the profit or loss of the business.  However, with a small growth chamber; while there is maintenance and energy consumption, these are things that are usually not significant to capture and hence are left out of the database and data model.

## Time Frames
BPM comes in three 'flavors': templates, plans and actions.
Templates define abstract actions.  They are the 'recipe' of how to bake a batch of cookies, not the actual action of baking real eatable cookies.
Plan is the proposed realization of a recipe; it is the schedule of when the action will take place, and identifying the physical ingredients that will be used.
Action is the execution of the plan, what was actually done, by whom and with what.
For the MVP, we will focus on capturing actions, and secondarily look at trial recipes.  Planning and scheduling are out of scope for the database.

## Agriculture Activities
Agriculture (focusing on annual plants) centers around the life-cycle of the plant, from planting of the seed through harvest.  The life of the plant can be sub-divided into smaller cycles of germination, vegetative growth, flowering and fruiting.  These life-cycle events are usually captured as phenotype observations.
Accompanying these plant cycles are agronomic activities, things done by the grower to the plant and its environment.  Many of these activities are planned and scheduled, while others are done in response to changes in the plant or environment.  These activities can include:
* Environment preparation
* Planting
* Thinning
* Watering (Irrigation)
* Fertilizer application
* Insecticide application
* Light application
* Chemical adjustment (adjusting pH)
* Harvest
* Clean-up

## Observations
Observations are notes about the plants and the environment.  These activities may be scheduled around the plant life-cycle, or they may be done ad-hoc.  Observations fall into two main groups, those that are of the plant (Phenotypic Observations) and those of the plant environment (Environment Observations).

### Phenotypic Observations

## Environment Observations
Environment observations are independent of the Experiment, Trial or live cycle of the plant; though correlated to them for analysis.  I think of this in terms of weather data.  The National Weather Service (NOAA) makes recordings of weather and publishes daily summaries (min, max, average temperature; min, max, average wind speed; humidity; cloudiness; amount of sun; amount of precipitation; precipitation type; sun rise, sun set).  This data is not made for any one group of people (farmers, sports stadiums, ...) but exists as an independent set of data.  People of all interests then access this data for different needs: farmers plan their planting and harvest (and irrigation); individuals plan their vacations, golf games and whether to take an umbrella to work; pilots determine their flight plans, etc.
In a similar manner I see the sensor data of the MVP being of a similar nature.  I can collect sensor data regardless of whether there is anything growing in my box or not.  As long as there is a timestamp on the observation, I can correlate it to the time and dates of an experiment.

## Main Activities
[Experiment and Trial](https://github.com/futureag/blog/wiki/Data-Model:-Experiment-and-Trial)
