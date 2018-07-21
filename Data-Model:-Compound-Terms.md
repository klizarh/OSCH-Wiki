# Compound Terms
Compound terms are usually a 'give away' that someone is abusing data.
Attribute names like:
* "Number of mature insects between the 2 and 5th node"
* "Fruit color three days after harvest"
* "Percentage of plants flowering three days after initial flowering"
* "Percentage of leaves with 50% mosaic virus scaring"

Such names indicate that several data items have been compounded into one record.  Such records are needed for special analytics, but should not be allow as the 'base' observations.

## Date deltas
Date deltas (time from) indicates two data records have been added or subtracted to derive this record.  The individual dated records should be recorded, with the delta derived as a part of analytics.

## Population percentages
Percentages are often an indicator of semi-derived data (Summing the individuals and dividing by the whole population).  This is common in large field trials when dealing with a whole plot or field of corn.  Often these are estimates and not formal calculations.  I hope we can avoid this with food computers, as we should be dealing with individual plants.  Population data suffers from being [mass objects](https://github.com/futureag/blog/wiki/Data-Model:-Mass-Objects).  Such records are necessary, but the naming should be cleaned up to:
1. Indicate this is a population value, not an individual value.
2. Properly make percentage the units and not part of the attribute name.

Above all avoid such things as: "Number of plants with shattered stalks".  If the total population size is not known (but assumed by the person doing the experiment), this value is useless beyond the present experiment.  Either record the individual plant (Subject: Stalk, Attribute: shattered, Value: True), or make this a percentage.

## Mixing of subject attribute unit and value
"Percentage of leaves with 50% mosaic virus scaring" should be broken up into the appropriate fields.  The subject is "Leaf: Population", the attribute is "Mosaic Virus scaring" and the value is 50 with a unit of "Percent".