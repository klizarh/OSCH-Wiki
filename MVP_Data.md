# Data
For some people, data is a part of the boring details; but next to growing plants, data is the heart of the MVP - it is what has value in the long term and what can be shared with others.

There are several 'flavors' to the data:
## [[Data Model | Data_Model]]
The theoretical, semantic design of what things are and how they are related.  If you really want to understand why the data structures are the way they are, dig into the model, otherwise continue to the more practical stuff.

## [[Storage and Message Structures | Storage-and-Message-Structures]]
The packages of data for storing observations and events, and exchanging them between programs.  This is the 'operational' data created while things are running.  These structures fall into two formats, a comma separated value (csv) format for storing in spreadsheets and relational databases, and a JSON structure for messaging and No-SQL databases (ie CouchDB which is what the MVP uses to store data).

## Recipe
This is a description of what it takes to run a plant trial - the growing of one or more plants under the same conditions.  The recipe describes the plant (genus, species, variety, ...) and what needs to be done to it (light, nutrients, temperature).  The description of how to grow a plant that can be translated into machine instructions for controlling the MVP.  This is currently a work in progress.

## Data Summary
This is a package of data generated at the end of an experiment.  This is what should be exchanged between groups for analytics.  It consists of the recipe, description of the environment (the MVP) and a results summary.  The MVP collects temperature data every 20 minutes, but this level of detail is not needed for analytics - so it is summarized into a daily min, max and average.  There will likely be a core set of summary data, but each type of experiment will likely have a custom sub-set of data (ie research on CO2 concentration affecting growth rate will be different from research on light spectrum affecting flowering).  For a start, we are looking at what Fairchild Gardens is providing for NASA. 

