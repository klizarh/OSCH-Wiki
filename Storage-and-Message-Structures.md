# Data Structures

All data is considered to be an event - something with a timestamp associated with it.  All records have the following common attributes:
* Timestamp - when the event occurred.  This is normally standardized to Greenwich Mean Time (UTM or GTM)
* MVP - a unique identifier to associated this data record with a particular MVP
* Subject - what this event is about, the plant, air or nutrients
* Attribute - what is being measured (temperature, humidity, plant height).  Associated with the attribute is the value of the measurement, and the units in which the measurement was taken.
* Status - status of the activity, whether is it an ongoing event that is in process, or completed.  On completion there is a status qualifier indicating if the activity was a success or failure (or was canceled).  There can be more details to the status explaining why it failed, and optional comments.
* Participant - who or what made the observation.  This is the name of the device sensor, or a person.

There are two patterns of data structures:
* Environmental Observations
* Phenotype Observations

## Environmental Observations
These cover sensor readings of the environment (Air temperature, CO2 concentration).  These records do not apply to any individual plant, but to the whole environment.  The subject of these records have an additional location attribute - so you can tell the difference between the temperature at the top of the chamber, and the temperature in the leaf canopy.
The structure of the Environmental Observations is also used for Device State records (whether the lights are on or off).

## Phenotype Observations
This is the valuable information that is needed for analytics, it tells us how well we grew the plants and how they respond to the environment.  These records have an experiment id associated with them.
In addition to records about the plants (height, width, weight), there are more general 'Agronomic Activity' records that describe events applicable to a group of plants or the environment, things like planting, watering, pruning or harvest.  An experiment is a high level event that encompasses all the activities from its start to finish.

## Example Records
### Environmental Observation - csv format
### Environmental Observation - JSON format
### Phenotype Observation - csv format
### Phenotype Observation - JSON format
