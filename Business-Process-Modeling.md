# Business Process Modeling
Business processes focus on events, something that happens at a specific time or over a period of time.  For those with a Data Warehouse background, these are 'fact' tables from which the attributes star from.  The core of the pattern is:
* Who 
* What
* When
* Where
* How

This pattern holds true in almost any context, from selling groceries, manufacturing goods, baseball games or growing plants.  This pattern also applies to many different levels, the pattern is 'fractal'.  For a grocery store this is as small as recording the individual item scans at the check-out, the sales transaction or store sales over a period of time (day, week, year).  For a baseball game this is the individual hits and strikes, a time at bat, an inning, a game or a whole season.  For growing plants this is the individual environment measurement (air temperature) or plant measurement (leaf color), as well as growth stages (germination, vegetative growth, flowering) and agronomic activities (planting, harvesting, watering).  This also summarizes up to cover the a whole growth cycle (a trial or experiment) from start to finish.

Who can take several forms.  There is the "who" that is the subject of the action, and the "who" that participates in making it happen.  The subject could be a plant, a plant part (leaf), or part of the environment (air, water, light).  The participant is usually who performed the action, which could be a person taking a measurement, or a sensor taking a reading.

What: the type of activity

When: the timestamp of the event.  Often this is a momentary or 'punctiliar' event, the recording of a temperature, the time the lights were turned on; but it may cover a span of time with a start date and end date (the experiment started when the seeds were planted on 2/3/2018 and ended when the plant was harvested 5/5/2018).

Where: the location of the event, which pot the seed was planted in, whether the air temperature was recorded for the top of the growth chamber, or in the plant canopy.

How: this is moving into 'meta-data', and would include such things as the protocol for how to measure plant height, or the recipe for how to grow hydroponic lettuce.

Other than descriptive information (the brand and variety of lettuce grown, the model of the humidity sensor), almost everything else is event data. 