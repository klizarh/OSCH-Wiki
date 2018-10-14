## Debugging ##

The following are bits of advice and experience we have come across to help work through problems
### SI7021 ###
Getting the the sensor up and running has caused problems for a number of people.  In general, it is usually a hardware problem and not a software problem.  The software (SI7021.py) has a built in test function which can be run from a command prompt:

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