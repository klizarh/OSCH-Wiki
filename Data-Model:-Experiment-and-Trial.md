# Experiment and Trial
I am going to set aside Experiment for the moment, as I do not think it is a true activity in its own right; but I think we will be using it as a convenient activity for record keeping.

## Trial
A trial is the activity that covers the growth cycle of a collection of plants with the same genetics and agronomics, grown at the same time.  It starts with the first agronomic activity (the first recorded is often planting) and usually ends with harvest.  The plants should all be the same species and variety, and ideally have identical genes.  How the plants are grown (agronomics), the fertilizer, light, temperature, etc. should also all be the same.  In large trials, with lots of plants; the location of the plants may be randomized to avoid the differences of location.  We see this with Fairchild, where the placement of individual plant pillows is randomized in the growth chamber.

Originally with the MVP, I thought that since there was a single reservoir, and that the same plants would be grown at any time; that each MVP experiment was a single trial.  Alternate MVPs with multiple reservoirs, and Fairchild with individual 'pillows' required a more dynamic trail.  It is now necessary to define experiment trials; ie. define the number of trails per experiment, and assign individual plant/locations to each trial.  An MVP could run a single trial for an experiment, or each well/pillow could represent a different trial.

## Experiment
Properly, an experiment is a set of trials where the results are compared against each other.  For example, two plants of the same variety are grown in two separate pots with different amounts of fertilizer, to see how the difference in fertilizer affect the size.  It is assumed that all other factors (light, temperature, ...) are the same.
Informally, an experiment may be a single trial, where we just want to see what happens, or are informally comparing the outcome to our imagined/assumed 'standard'.
In this usage, an experiment has the same start and end dates as the collection of trials of which it is composed; thus it looks like an activity.  However, technically an experiment is the analytic comparison of trials (something that takes place after the plants have been harvested), and so the dates are meaningless.  This is especially true when we look at synthetic experiments.

## Synthetic Experiments
Experiments are actually the analytic operation of comparing trial data.  It is not the growing of the plants but the analysis process.  The goal and beauty of the MVP (and sharing data across different food computers) is the ability to create synthetic experiments; finding trials with similar attributes but finding novel variables and combinations.  It will be possible to take trials performed from different years and in different parts of the world, and come up with new insights.  Such experiments can be performed by data scientists who have never grown a plant, as such they are an activity independent of any particular trial or plant growth cycle.  In fact, the particular dates of the data records will only be used to correlate the records (using growth phase, growing degree days, etc), and the actual date will be irrelevant. 

## Conclusion
The dynamic experiment/trial setup will require a user interface to create these relationships at the time an experiment is started. These relationships are currently in the environment.py dictionary of the MVP code.
I think we need to live with this dual definition of experiment:
* A dated collection of trials
* The analysis of a collection of trials (independent of date)