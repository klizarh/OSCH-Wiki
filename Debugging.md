## Debugging ##

The following are bits of advice and experience we have come across to help work through problems
### SI7021 ###
Getting the the sensor up and running has caused problems for a number of people.
1. Make sure the problem is the SI7021.  If the error says it is a problem 'logging' the sensor, it may be a problem with the database (the logging process) and not the sensor.  Since the SI7021 is the first sensor to be logged, it will be associated with the logging error.
2) In general, it is usually a hardware problem and not a software problem.  The software (SI7021.py) has a built in test function which can be run from a command prompt:

> python /home/pi/MVP/python/SI7021.py

You should see both sensor readings, as well as information about the sensor (version, etc).
At a lower level, you can install the i2cdetect package, which will list all of the I2C devices that are available.

> sudo apt-get install i2c-tools

Then from the command prompt run:

> sudo i2cdetect -y 1 (or possibly: sudo i2cdetect -y 0)

This will display a grid of all possible addresses, and show the number of working i2c sensors.  The SI7021 should show up as address 40.

If the sensor does not show up, you have a hardware problem (or have not enabled I2C on the Raspberry.
* Check the Raspberry Configuration and confirm that I2C is enabled.
* Check you wiring that you have the proper pins connected
* Check you header pin soldering
* If you know someone with a working system, try swapping sensors (will check if the sensor and sensor soldering is good)

### CouchDB ###
To check that the database is up and running, enter the following from a browser:

> localhost:5984

This should come back with the 'welcome' message from the database.  If you get an error, proceed by checking the following.

The easiest fix is to reboot the system.  The restart script (/home/pi/NerdFarm/scripts/Startup.py) clears several issues and should restart the database.

There are several levels at which there can be database problems:
1) A frequent problem is permission on the log files created by the scripts.  The easiest fix to this is to delete the log files (/home/pi/NerdFarm/logs/) and let the next run recreate them.  This step is also taken by the startup script when the system is rebooted.
2) Try bypassing the scripts and starting the database from a command prompt:

> /home/pi/NerdFarm/scripts/StartCouchDB.sh

3) Check the log file (/home/pi/NerdFarm/logs/couchdb.log) and look for errors.  If you find errors, you have some significant problems. 

4) Finally: Make sure the database was installed.  You should find a /home/couchdb directory