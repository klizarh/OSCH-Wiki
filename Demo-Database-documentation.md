The Couch database mvp_demo_data is a working set of data, indexes and views to help developers write code to access data for creating the UI, charts and analysis.

## Key data Values

> field_id : "8e89e414-0181-440a-9170-702434c8f400"

The GUID (universally unique identifier) that identifies a particular MVP

> trial_id : "d3ca243b-2740-4557-87f9-c07be9d929ad"

The GUID that identifies a trial.  Being a GUID, you do not need the field_id AND the trial_id to uniquely identify a trial.

> trial start date : "2018-07-22T12:34:55"

The data the trial started, this is the reference data for all activities.

## Environment Mango Queries

The Mango selector should start by selecting the field, to get the data for a particular box, then working your way down the data tree.  When building queries, make it a repetitive process as Couch doesn't give good debugging messages, if the code doesn't have any syntax errors, you will simply get no results.  Stepping your way through from something that works helps to spot the problems.

## Trial Queries

Environment data is trial independent.  Like NOAA weather data, the data is not specific to a particular farmer's needs, but just 'is'.  Since it is possible to run multiple trials (farm crops) in an MVP, the Environment data must exist independently of any particular trial.  However, for analysis it is necessary to associate this environment data with the trial by the data.  Since Couch does not have SQL joins, this has to be done through trial specific views.  In the demo database you will find a view named:

> "trial_d3ca243b-2740-4557-87f9-c07be9d929ad_view"

This view was generated via python code (at the time the trial was started) that selects data for this trial, and generates a trial specific key.  The key has the format of:

> [<subject.activity.name>, <week>, <day>]

Thus the key/value pair produced from this map/reduce view will be something like:

> ['Temperature', 2, 17], 25.6

Because the view is specific to this trial, by calling the view you do not have to search or sort by the trial_id.  This array key has some special abilities, I can now query for any environmental attribute, and get min/max/avg summaries for any day, week or range.  The following would be the parameters passed into the query function (assuming Python couchdb):

> view: '_design/trial_d3ca243b-2740-4557-87f9-c07be9d929ad_view/_view/trial_view'

> startkey=['Temperature', 1, 1]

> endkey = ['Temperature', {}, {}]

The '{}' are placeholders for anything, so the max values do not need to be specified.  By specifying the attribute as 'Temperature', only temperature records are returned; substitute 'Humidity' and you will get similar results for Humidity.  Thus, one view works for all Environment attributes.

So far this will return a single record, rather meaningless to get the min/max/avg for the whole trial; the trick is in the next two parameters:

> group=True

> group_level = 1 (or 2)

Here is the Couch magic, the built in grouping ability (specified by group=True), the power is in the array key and the group_level, by specifying 1 it groups on the second array value (ie index starts at 0) which is week, by specifying 2 it groups on day.  The trick is to pick the key structure so the values are ordered from general to specific (ie the attribute includes all the week data, and the week includes all the day records)

## Phenotype Data

Since phenotype records are specific to a trial, a single generic view will work for any trial.  The only query change is the need to specify the trial_id as the first key (and change the group_level values accordingly).

