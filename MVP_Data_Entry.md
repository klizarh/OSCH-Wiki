# Data Entry - Creating Manual Records

Not all data is automated.  In fact the most significant data (Phenotype Observation) is normally entered manually, as the process of making a phenotype observation is done by a person.  Some Environment Observations are also manually performed, particularly things like pH readings.
All manual entries start with getting the identifier of the 'Field' (MVP box).  This is currently in the env.py file, but may be located in an Environment data record.

> {'location':{'field':uuid}}

The next step is to identify the type of record being recorded:the activity_type, these can be:
* Environment_Observation (something recorded about the whole field)
* Agronomic_Activity (something done to a whole trial)
* Phenotype_Observation (something about an individual plot/plant)

From here each activity type has different attributes

## Environment_Observation

Add the activity_type, and add a timestamp:

> {'start_date':{'timestamp':ts}, 'activity_type':'Environment_Observation', 'location':{'field':uuid}}

Select the subject name (Air, Nutrient, Water)

## Agronomic_Activity

Add activity_type, timestamp, and expand out the location information:

> {'start_date':{'timestamp':ts}, 'activity_type':'Agronomic_Activity', 'location':{'field':uuid, 'trial':uuid}}

Select the subject name (Planting, Harvest, Treatment):

## Phenotype_Observation

Add activity_type, timestamp, and expand out the location information:

> {'start_date':{'timestamp':ts}, 'activity_type':'Phenotype_Observation', 'location':{'field':uuid, 'trial_id':uuid, 'plot_id':1}}

The subject is usually the whole plant:
