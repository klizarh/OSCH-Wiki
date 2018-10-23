## Debugging FAQ##
* SI7021
* CouchDB
* Chart Display

The following are bits of advice and experience we have come across to help work through problems
### SI7021 ###
Getting the the sensor up and running has caused problems for a number of people.
1. Make sure the problem is the SI7021.  If the error says it is a problem 'logging' the sensor, it may be a problem with the database (the logging process) and not the sensor.  Since the SI7021 is the first sensor to be logged, it will be associated with the logging error.
2) In general, SI7021 issues are usually a hardware problem and not a software problem.  The software (SI7021.py) has a built in test function which can be run from a command prompt:

> python /home/pi/MVP/python/SI7021.py

You should see both sensor readings, as well as information about the sensor (version, etc).
NOTE: Some people are getting a 121 error (Remote I/O I2C transmission).  This only pops up when running from the command line, and not if you run the file from the Python development environment.  If you see this in association with the "Revision" information, ignore this and continue.
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

This should come back with the 'welcome' message from the database.  The version number may vary, but it will look like this:

> {"couchdb":"Welcome","version":"2.2.0"}

  If you get an error, proceed by checking the following.

The easiest fix is to reboot the system.  The restart script (/home/pi/NerdFarm/scripts/Startup.py) clears several issues and should restart the database.

There are several levels at which there can be database problems:
1) A frequent problem is permission on the log files created by the scripts.  The easiest fix to this is to delete the log files (/home/pi/NerdFarm/logs/) and let the next run recreate them.  This step is also taken by the startup script when the system is rebooted.
2) Try bypassing the scripts and starting the database from a command prompt:

> /home/pi/NerdFarm/scripts/StartCouchDB.sh

3) Check the log file (/home/pi/NerdFarm/logs/couchdb.log) and look for errors.  If you find errors, you have some significant problems. 

4) Finally: Make sure the database was installed.  You should find a /home/couchdb directory

### Not Seeing Current Chart Data ###

This is usually a browser cache problem, and not a problem with the code; but lets step through things:
First lets make sure there is some data in the database from which to build the charts.  Try running the following from the command line:
> python /home/pi/MVP/python/LogSensors.py

If that runs, then you definitely have data in the database (temperature and humidity).  Then build the charts by running:
> /home/pi/MVP/scripts/Render.sh

In /home/pi/MVP/web you should see both:
* temp_chart.svg
* humidity_chart.svg
Check the properties (right mouse click on the file) to make sure you have a recent date from the last build.
Try right mouse clicking on the chart file, the open it with 'Chrome Web Browser', that should show that chart in a browser.
You can also try double-clicking on index.html to display it, and see if you are getting the same data.
Finally try: 
> localhost:8000
If you don't see the same data, clear the file cache in your browser.  Chrome often has old files 'sticking' in the cache and will not display the latest.  This is in part an issue with the MVP, because we use a static web page (index.html) and the browser doesn't realize that the embedded files have changed.

