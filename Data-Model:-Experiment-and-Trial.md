# Experiment and Trial

## Experiment
Properly, an experiment is a set of trials where the results are compared against each other.  For example, two plants of the same variety are grown in two separate pots with different amounts of fertilizer, to see how the difference in fertilizer affect the size.  It is assumed that all other factors (light, temperature, ...) are the same.
Informally, an experiment may be a single trial, where we just want to see what happens, or are informally comparing the outcome to our imagined/assumed 'standard'.
It is also possible to have a 'synthetic' experiment, where the data results of trials from different times and locations are virtually compared.

## Trial
A trial is a collection of plants with the same genetics and agronomics, grown at the same time.  The plants should all be the same species and variety, and ideally have identical genes.  How the plants are grown (agronomics), the fertilizer, light, temperature, etc. should also all be the same.  In large trials, with lots of plants; the location of the plants may be randomized to avoid the differences of location.  We see this with Fairchild, where the placement of individual plant pillows is randomized in the growth chamber.

Originally with the MVP, I thought that since there was a single reservoir, and that the same plants would be grown at any time; that each MVP experiment was a single trial.  Alternate MVPs with multiple reservoirs, and Fairchild with individual 'pillows' required a more dynamic trail.  It is now necessary to define experiment trials; ie. define the number of trails per experiment, and assign individual plant/locations to each trial.  An MVP could run a single trial for an experiment, or each well/pillow could represent a different trial.

## Conclusion
The dynamic experiment/trial setup will require a user interface to create these relationships at the time an experiment is started. These relationships are currently in the environment.py dictionary of the MVP code.