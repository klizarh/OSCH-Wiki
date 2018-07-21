# Derived Data
Derived data is data synthesized from two or more other data records, or manipulated in some way.  It is impossible to avoid derived data, as almost every data record is derived in some way.  A temperature reading is usually derived from the voltage through a resistor which changes resistance due to temperature.  We record temperature, not voltage; because the sensor performs calculations for us to convert the reading into something meaningful.
For some sensors, it is necessary to average a group of readings and possible exclude outliers before returning a value.  Such processes make assumptions (which may or may not be documented) and affect the value.  For sensors, this is a 'known' of the sensor we are using.  What I want to avoid are values created by user code that are not identified as such.
Derived data is necessary, and will likely be stored in the database.  I am not against it, but I want it identified.  For example, I have Dewpoint as a value, this is derived through a python program that takes temperature and humidity, runs this through a function and outputs dewpoint.

## Custom Derived Data
I want to avoid in the centralized database custom derived data that should be generated during analytics.  I am thinking of attributes like "Color of fruit three days after harvest" (I have actually seen this!!).  It was probably a direct entry, but should have been captured with more records and then derived - ie. harvest data should have been stored, and the date of the color measurement should have been stored, then the dates of the two records should have compared to derive the difference.
There are a lot of similar data conversion issues when doing analytics:
* Converting dates to days since planting (or germination) for comparing trials performed at different times.
* Converting dates and temperature into growing degree days or growing degree days since planting (or germination)
* Any time span delta measured from a growth stage date.
This sort of stuff in necessary, and may be captured and stored as part of a analytic package, but we should not have it in the common database, or as a part of the summary data.

## Conclusion
I propose that we come up with a convention where the "Participant" is not a person or the sensor, but somehow identified as the deriving algorythm.  This could be as simple as using "Derived" as the participant, and noting the function in the documentation; or by having the participant be a url to the function (in github).