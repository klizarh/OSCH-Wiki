# Data Model

## Data Modeling Philosophy
Data is normally used in three ways:
* Operations
* Administrative
* Analytic

Operational data is needed to 'run the business': control the lights and temperature and make sure the MVP is doing what it is suppose to do.  If the operations go correctly, the operational data has little long term value; other than confirming that the recipe was followed correctly.

Administrative data is used to track how efficiently things are going.  How long did a process take, who made the most observations, what is the most common cause of germination failure, is the failure rate of a sensor increasing?  Administrative reporting is usually performed over a period of time, or comparing one growth cycle with another.

Analytic data is the 'heart' of the MVP.  This is primarily the phenotypic data, looking at how one growth cycle improves or worsens the plants (ie. which fertilizer gives the fastest growth, best flavor, ...).

## Goal
The long term value of MVP data will likely [not be the individual observations](https://github.com/futureag/blog/wiki/Data-Model:-Goal), but summary data aggregated at the end of a growth cycle.

## Design and Patterns
Besides the traditional discipline of relational data modeling (Normalizing), the two big influences on my design philosophy have been Peter Coad's modeling patterns, and insights from [Business Process Modeling](https://github.com/futureag/blog/wiki/Business-Process-Modeling).  You will also find similarities with Data Warehouse star modeling.  All of these sources see the 'heart' of the model being an activity (something associated with a data).  Associated with this data are the 'who', 'what', 'where', 'when' (the date) and status of the activity.
* Who is the participant](https://github.com/futureag/blog/wiki/Data-Model:-Participant) and/or the [subject](https://github.com/futureag/blog/wiki/Data-Model:-Subject).  The participant is the person or thing performing the event (taking a measurement), and the subject is what they are measuring.
* What covers the type of activity being performed.
* Where is the location of the activity
* Status indicated if the activity finished successfully, failed, or was canceled.  Status often has more detailed parts such as a qualifier (why it failed), and optionally comments.

## Main Entities
* [Activity Types](https://github.com/futureag/blog/wiki/Data-Model:-Activity-Type)
* [Subject](https://github.com/futureag/blog/wiki/Data-Model:-Subject)
* [Attribute](https://github.com/futureag/blog/wiki/Data-Model:-Attribute)
* [Value](https://github.com/futureag/blog/wiki/Data-Model:-Value)
* [Participant](https://github.com/futureag/blog/wiki/Data-Model:-Participant)
* [Location](https://github.com/futureag/blog/wiki/Data-Model:-Location)
* [Status](https://github.com/futureag/blog/wiki/Data-Model:-Status)
* [Protocol](https://github.com/futureag/blog/wiki/Data-Model:-Protocol) (Recipe)

## Environment Observation Data Model
Environmental observations are measurements about the environment, the context of the plants: temperature, humidity, lights, etc.  These are captured by the participant, which is usually a sensor, but may be done by a person.
![Phenotype Observation](https://github.com/futureag/blog/blob/master/static/images/Environment_Observation.png)
## Phenotype Observation Data Model
These are measurements about the plant, or parts of the plant.  These include height, weight, color, flavor and health.   Normally these are recorded by a person, but could be derived from camera images.
![Phenotype Observation](https://github.com/futureag/blog/blob/master/static/images/Phenotype_Observation.png)

## Participant
![Participant](https://github.com/futureag/blog/blob/master/static/images/Participant.png)
## Administrative
![Administrative](https://github.com/futureag/blog/blob/master/static/images/Admin.png)
## Agronomic Activity Data Model
These are the events of planting seeds, treatments (adding water, fertilizer, etc) and harvesting.