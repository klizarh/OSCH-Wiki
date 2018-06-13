# Code Organization

This is a guide to the MVP code organization.  This is something specific to the project.

Cron is currently used for scheduling - calling time dependent actions.

Cron usually calls a script (/home/pi/MVP/scripts).  The scripts bundle code into common activities.  This is where you should customize the MVP, ie. if you have custom sensors, don't change the LogSensors.py file (which contains the logging of standard MVP sensors), but copy LogSensors.py and modify it to create your own custom file, and include it in the script (LogData.sh).  This helps when doing a code upgrades, you can install the new Python code without worrying about your logic being overwritten, you just have to watch out for the scripts.

The core of the project are three components:
* Sensors - the devices that provide environmental information
* Actuators - the devices that manipulate the environment (Lights, Fans, Relays)
* Controllers - the business logic that reads sensors and uses this information to change actuators

The rest of the code is basically utilities and output (charting).  The utilities are often wrappers that customize libraries for the MVP:
* Wrappers around the database (CouchDB or MySQL)
* Wrappers around MQTT
* Wrappers around JSON 

You will also find files that are just Python dictionaries.  These files are generated to hold persistent variables about the running of an experiment or configuration of the environment.