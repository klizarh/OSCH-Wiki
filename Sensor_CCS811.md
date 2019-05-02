# CCS811 - CO2 Sensor
## Description
This is not a true CO2 sensor, but it measures volitle organic compounds in the air and emulates the CO2 reading.  I have only worked with it a bit, so I don't guarantee that this is the best software configuration.
The software follows I2C practices.

## Setup
There seems to be an assumption that this sensor is left on for continuous monitoring, and not periodically read (as done by the NerdFarm). The CCS811 requires heat to get proper readings, therefore one instance of the software (Master) should be called from the Startup.sh script, and another instance should be called to get data values (Slave).
Look in Startup.sh for commented out code for the Master, and LogSensorsExtra.py for the Slave.

## Technical Reference
* [AdaFruit](https://learn.adafruit.com/adafruit-ccs811-air-quality-sensor/overview)