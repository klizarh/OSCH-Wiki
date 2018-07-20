# Location
Location is where the activity took place.

It is easy to confuse the location of the sensor with the location of the reading, principally because we usually read something like air temperature where the sensor is located.  There are two use cases that show the potential of this not always working.

## Sensor Location
On large vertical farms, sometimes the sensors are mounted on a track or robotic arm that moves over the plants.  The sensor has no fixed 'home'.  This may not be the best example, because at any given moment the sensor and the measurement could be identified with the same transient location.  A better example is an IR thermometer, such as is used at zoos to measure the temperature of reptiles in an enclosure; in this situation the observer is standing outside the enclosure and the sensor is pointed at a lizard that could be 20 feet away.  Here the location of the sensor, and the location of what is being measured are two very different different things.

## Subject Location
From my agriculture background, I tend to associate location with a plot; a 10x20 foot section of a field that has one genetics and the same agronomic treatment.  Because a plot often had multiple plants, it was easiest to think of the plot as the subject, and the location was often the identifier.
This model broke down when I encountered a greenhouse where each plant was in an individual pot (plot), and all the pots were on conveyor belts that were constantly moving (a way to randomize possible differences in different locations within the greenhouse).  The pot/plant needed a unique identifier, but it could not be associated with a location (location had to be an optional attribute of a plot).

For more on subject location, see the discussion of [Plot](https://github.com/futureag/blog/wiki/Data-Model:-Plot)

## Conclusion
The location of the sensor and the location of the measurement (Subject) are different, both may be important, but I think we are primarily interested in the subject and its location.  Sensor location is important for maintenance and analysis of the performance of the sensors.  We may not be tracking maintenance issues with our boxes, but larger operations want to know if a particular location has a high frequency of failure (due to moisture, vibration or corrosion), or a particular type of sensor tends to fail more often than another.  I am inclined to consider sensor location an attribute of the particular sensor, and not a part of the measurement record.
Plant identifiers and location will be a judgment call.  Normally we will be working with an individual plant in a pot/well of the growth chamber, and not with a collection of plants (population studies).  I would be inclined to reference a plant id, but in practice if someone is told to measure the height of plant #123, the first response is "Where is it?"; a location identifier is more helpful than the plant identifier (row 1, column 3).  Since plant/location is a one-to-one relationship, it is easy to use them interchangeably.  We need to discuss this and see what is the best practical solution.
