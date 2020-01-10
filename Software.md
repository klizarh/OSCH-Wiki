# Architecture
Software is in two parts:
* Code running locally on the MVP's Raspberry Pi
* User Interface (UI) code running on the cloud server

These pages are about the custom MVP code.  For generic information about packages, see the following:
## Sensors
### Standard Sensors
* [SI7021](Sensor_SI7021) Temperature/Humidity
* [TSL2561](Sensor_TSL2561) LUX sensor
### Optional Sensors
* [CCS811](Sensor_CCS811) CO2 Sensor
* [NDIR](Sensor_NDIR) CO2 Sensor
* [OneWire](Sensor_OneWire) OneWire Temperature sensors
* [SCD30](Sensor_SCD30) CO2 Sensor
### Other
* [ADS1115](Sensor_ADS1115) Analog to Digital Converter

## Database and data storage
* [CouchDB](couch_db) The database for storing data
* [Google Sheets](Google_Sheets) - Using Google Sheets as a database (and charting)
## [Web Server](Web_Server) - Access from the web 
* [DDNS](ddns) Getting a stable address on the web
* [NGINX](nginx) Securing your presence on the web

## Code Architecture
The MVP code currently consists of three main parts:
* Controller (currently the Linux CRON process): control the timing of events
* Scripts (/home/pi/MVP/scripts): these package the Python code for group operations, and provide separation between the controller and functions.
* Code (/home/pi/MVP/python): most actions are executed through Python code files.  This code represents sensors, controllers, utilities (data handling,logging, ...) and reporting.

## Releases
* V1
* V2.1
* V3

## [Coding Standards](https://github.com/futureag/blog/wiki/Software_Standards)

## [Data_Model](https://github.com/futureag/blog/wiki/Data_Model)