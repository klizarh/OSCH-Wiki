# Participant
The participant is the person or thing that carries out the activity.  In a grocery store this is the clerk at the cash register, it is the farmer who planted the seeds.  There may often be more than one participant, as we want to know which cash register the clerk was using, and what tractor/planter the farmer was using.  Whether a person, or a device; these have the role of a 'participant' in the activity.

## Modeling technicalities
A 'participant is a role', roles are defined by steriotypical behavior, what is done in a particular context.  A clerk is someone who scans items over a bar-code reader and works the cash register of a store. A customer is the person who purchases items at the store. Roles are not a sub-type of something, and a person or thing can have multiple roles.  A clerk is not a unique type of a person, and a particular person can have multiple roles (clerk, driver, student, sibling).

## Conclusion

For the sake of this data model I would like to consider the person or device making the measurement recording the 'Participant'  At this time I think we can avoid multiple participants (person and instrument), for something like a person taking a temperature reading, the details of the thermometer may be captured in a 'protocol' document describing how a person should take air temperature.