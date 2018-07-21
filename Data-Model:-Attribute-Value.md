# Attribute Value & Units
These are the measurements recorded
We need standardized data, so there needs to be agreement on measurement units.  Without standardization, analytics get bogged down in data conversions.
* Temperature should be Centigrade (to the nearest degree)
* Dimensions should be millimeters (to the nearest mm)
* Weights should be grams (to the nearest gram)

## Separate capture and display
Data should be consistent in the database, with the same unit used consistently for a given attribute.  However, charting should allow the user to specify what unit they want to see displayed (Fahrenheit, Kelvin, pounds, ton, stone).

## Normative Unit Standards
The 'standard' units should be consistent as to type and precision.  I call this 'normative' as special circumstances may require more precise measurements than is what normally performed.  We may want normal plant measurements to be in millimeters, with precision to the nearest millimeter; but the height of a tree might be precise to the nearest meter.

## The Storage is not the Standard
The agreed standard and the physical storage may be different.  We may store values in a long, even though we know the units should be treated as an integer.  This accommodates corner cases where the decimals are actually needed, and the fact that most electronic sensors use a long, even though most of the decimals are worthless.

I saw this problem with geo-spatial data recording longitude and latitude, there was agreement to use decimal notation and values were stored to the eighth decimal, which is [1.1 mm at the equator](https://en.wikipedia.org/wiki/Decimal_degrees).  The problem was that many people were using cell phones which are only accurate to about 3 meters (4 or 5 decimals).  Only an RTK GPS system can get sub-centemeter readings, and without meta-data (type of GPS, DOP, ...) it is impossible to know how precise this data actually was.

