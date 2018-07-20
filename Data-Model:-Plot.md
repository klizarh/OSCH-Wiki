# Plot
A plot is a collection of plants growing in a location (the current MVP definition)

In agriculture field trials, a field is often divided up into 10x20 foot areas, where each area is dedicated to a specific plant type (genome).  A plot is treated with the same agronomic practices (watering, fertilizer, light), and having the same genetics it should have a consistent phenotype expression.  In other contexts (like a greenhouse) a plot may be an individual pot with a single plant.  The key thing about a plot is it has consistent genetics and treatment.

There are several problems here:
* In some contexts a plot and a geographic location have a one-to-one relationship, and it is easy to interchange the concepts (and identifiers).  This is the case with the MVP where there are fixed wells in the reservoir.
* In some contexts a plot and an individual plant have a one-to-one relationship, and identifiers are easily interchanged.
* A plot may be related to an individual plant, but it may also be related to a collection of plants (which may be treated as individuals, or as a mass unit).
* A plot (ie a pot) may have a fixed location, or it may get moved around.

With the MVP model, a plot is defined as a well of the reservoir, and I have equivocated the plot_id with a plant_id.  This basically works, but cheats a bit as multiple seeds can be planted in a pot, though they are thinned out to a single plant (or at least that is the intention).

This model was challenged by Fairchild, where plants are grown on 'pillows' containing growing medium and slow release fertilizer, as well as the plant seed.  A growth chamber could have different numbers of plots at different times.  To them, it seems the identifier is primarily associated with the plant, and secondarly with the 'pot' or 'location'.

Technically there is a distinction between a plot and a 'plot usage'.  If a plot is a well of the reservoir, this is a permanent identifier of a location for the life of the MVP.  The 'plot usage' is the temporal function of the well for a particular experiment, ie the well may have a different plant with different treatments in each experiment.  Thus the experiment_id and plot_id identify this temporal 'plot usage'.  An individual plant is associated with this 'plot usage', and technically not directly to the plot.  Entities with three primary keys are problematic (experiment, pot/plot/location and plant), as the combination of any two keys often reveal such 'hidden entities'.  This is further complicated when a plot id (or experiment and plot id) are equivocated with the plant.

## Conclusion
This is a difficult space to model and will need some discussion.
The MVP models plot as a location, and assumes there is one plant per plot.  The 'holes' are given an identifier (1 through 5) and these identifiers are re-used from experiment to experiment.  Plot_Id, Experiment_Id and Field_Id (the box) are a universal unique identifier.
Fairchild does not database their data, but it seems that each 'pillow' in a unique equivocation of a 'pot' and a 'plant'; and location is not a factor.
I think we can get by with this equivocation of plot and plant, though we need to dynamically assign plots to a growth chamber at the time an experiment is started (ie, how many may change for each experiment).