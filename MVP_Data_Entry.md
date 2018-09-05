# Data Entry - Creating Manual Records

Not all data is automated.  In fact the most significant data (Phenotype Observation) is normally entered manually, as the process of making a phenotype observation is done by a person.  Some Environment Observations are also manually performed, particularly things like pH readings.
All manual entries start with getting the identifier of the 'Field' (MVP box).  This is currently in the env.py file, but may be located in an Environment data record.

> 'location':{'field':uuid}

The person entering the data should be identified by a user id.  Since this is manual entry, the type is a person (instead of a 'Device'):

> 'participant':{'type':'Person', 'id':'hmw'}

The status information can be defaulted.  It is assumed this is a complete and successful recording; there is no need for a status qualifier reason, which explains why something fails.  Comments can optionally be collected as a part of the data entry:

> 'status': {'status':'Complete', 'status_qualifier':'Success'}

The next step is to identify the type of record being recorded:the activity_type, these can be:
* Environment_Observation (something recorded about the whole field)
* Agronomic_Activity (something done to a whole trial)
* Phenotype_Observation (something about an individual plot/plant)

From here each activity type has different attributes

## Environment_Observation

Add the activity_type, and add a timestamp:

> 'start_date':{'timestamp':ts}

> 'activity_type':'Environment_Observation'

Select the subject name (Air, Nutrient, Water)

> 'subject':{'name':'Air'}

Select one of the corresponding attributes (Temperature, Humidity) and its units.

> 'subject':{'name':'Air', 'attribute':{'name':'Temperature', 'units':'degree F'}

Finally, collect from the user the value:

> 'subject':{'name':'Air', 'attribute':{'name':'Temperature', 'units':'degree F', 'value':27}

## Agronomic_Activity

Add activity_type, timestamp, and expand out the location information.  The user needs to provide which trial to use, assuming there is more than one trial running at this time for the field:

> 'start_date':{'timestamp':ts}

> 'activity_type':'Agronomic_Activity'

> 'location':{'field':uuid, 'trial':uuid}

Select the sub-activity name (Planting, Harvest, Treatment):

> 'sub-activity':'Planting'

> 'sub-activity':'Treatment'

Collect the subject information appropriate to the sub-activity:

> 'subject':{'name':'Seed', 'attribute':'Count', 'units':'unit'}

> 'subject':{'name':'Nutrient', 'attribute':'Volume', 'units':'ml'}

Then have the user enter the appropriate value

> 'subject':{'name':'Seed', 'attribute':'Count', 'units':'unit', 'value':3}

> 'subject':{'name':'Nutrient', 'attribute':'Volume', 'units':'ml', 'value': 2500}

## Phenotype_Observation

Add activity_type, timestamp, and expand out the location information.  The user may need to identify the trial, and will need to identify the plot:

> 'start_date':{'timestamp':ts}

> 'activity_type':'Phenotype_Observation'

> 'location':{'field':uuid, 'trial_id':uuid, 'plot_id':1}

Select the subject name, this will usually be 'Plant':

> 'subject':{'name':'Plant'}

Select one of the corresponding attributes (height, width,  weight, etc) and its units.

> 'subject':{'name':'Plant', 'attribute':{'name':'Height', 'units':'mm'}

Finally, collect from the user the value:

> 'subject':{'name':'Plant', 'attribute':{'name':'Height', 'units':'mm', 'value':256}

The message parts are then assembled into the record and saved to the database.
