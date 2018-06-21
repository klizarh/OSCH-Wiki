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

> activity_type	start_time	field_uuid	subject	subject_location	attribute	Value	Participant_Id	Participant_Type	Status	Status_qualifier		Comment

> Environmental_Observation	01/14/18	b8:27:eb:9b:15:1e	Nutrient	Reservoir	pH	5	hmw	Person	Complete	Success		may be off due to hot water

> Environmental_Observation	01/14/18	b8:27:eb:9b:15:1e	Nutrient	Reservoir	pH	4.5	hmw	Person	Complete	Success		may be off due to hot water

> Environmental_Observation	01/14/18	b8:27:eb:9b:15:1e	Nutrient	Reservoir	EC	2140	hmw	Person	Complete	Success		may be off due to hot water

> Environmental_Observation	01/14/18	b8:27:eb:9b:15:1e	Nutrient	Reservoir	EC	2230	hmw	Person	Complete	Success		may be off due to hot water

### Environmental Observation - JSON format
> {
>   "_id": "010cc0a2e62e5119ead9b176ab000184",
>   "_rev": "1-328bf48fad956d0b3637aca90b8e00f9",
>   "status": {
>     "status": "Complete",
>     "status_qualifier_reason": "",
>     "comment": "",
>     "status_qualifier": "Success"
>   },
>   "participant": {
>     "type": "Device",
>     "name": "SI7021"
>   },
>   "field": {
>     "uuid": "8e89e414-0181-440a-9170-702434c8f400"
>   },
>   "activity_type": "Environmental_Observation",
>   "start_date": {
>     "timestamp": "2018-04-26 13:40:03"
>   },
>   "subject": {
>     "attribute": {
>       "units": "Cenitgrade",
>       "name": "Temperature",
>       "value": "26.8"
>     },
>     "name": "Air",
>     "location": {
>       "name": "Left_Side"
>     }
>   }
> }

State Chanage Example
> {
>   "_id": "10793268116bce2bcec946e5430008cc",
>   "_rev": "1-b44f24b6f58cd400768979359253f509",
>   "status": {
>     "status": "Complete",
>     "status_qualifier_reason": "",
>     "comment": "",
>     "status_qualifier": "Success"
>   },
>   "participant": {
>     "type": "Person",
>     "name": "Solenoid"
>   },
>   "field": {
>     "uuid": "8e89e414-0181-440a-9170-702434c8f400"
>   },
>   "activity_type": "State_Change",
>   "start_date": {
>     "timestamp": "2018-04-25 13:17:18"
>   },
>   "subject": {
>     "attribute": {
>       "units": "on/off",
>       "name": "State",
>       "value": "Closed"
>     },
>     "name": "Solenoid",
>     "location": {
>       "name": "Reservoir"
>     }
>   }
> }
### Phenotype Observation - csv format
> activity_type	Timestamp	Experiment_Week	field_uuid	Trial	Plot_Id	Subject	Attribute	Value	Participant_Id	Participant_Type	Status	Status_qualifier`

> Phenotype_Observation	2018/03/26	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad		1	Plant	Germination	TRUE	hmw	Person	Complete	Success`

>   Phenotype_Observation	2018/03/26	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad		2	Plant	Germination	TRUE	Participant_Id	Participant_Type	Status	Status_qualifier`

>  Phenotype_Observation	2018/03/26	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad		3	Plant	Germination	TRUE	hmw	Person	Complete	Success`

>  Phenotype_Observation	2018/03/26	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad		5	Plant	Germination	TRUE	Participant_Id	Participant_Type	Status	Status_qualifier`

Agronomic Activity variation

> activity_type	timestamp	field_uuid	trial_uuid	Plot_id	Subject	attribute	value	participant_Id	participant_type	status	status_qualifier	comment

> Plant	03/21/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	1	Seed	Count	2	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool

> Plant	03/21/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	2	Seed	Count	2	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool

> Plant	03/21/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	3	Seed	Count	2	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool

> Plant	03/21/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	4	Seed	Count	2	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool

> Plant	03/21/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	5	Seed	Count	2	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool

> Plant	03/21/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	6	Seed	Count	2	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool

> Treatment	01/10/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad		Nutrient	Volume	500	hmw	Person	Complete	Success	6 drops General Hydroponics Rapid Start

> Thin	03/28/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	1	Plant	Thin	1	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool

> Thin	03/28/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	2	Plant	Thin	1	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool

> Thin	03/28/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	3	Plant	Thin	1	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool

> Thin	03/28/18	8e89e414-0181-440a-9170-702434c8f400	d3ca243b-2740-4557-87f9-c07be9d929ad	5	Plant	Thin	1	hmw	Person	Complete	Success	Livingston Seed, Royal Red Lettuce.  Started in rockwool



### Phenotype Observation - JSON format
