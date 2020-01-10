# Google Sheets
The Google Sheets API provides a way to save data (and create charts) on Google Drive.  This requires fewer libraries and software on the Raspberry and makes data easily available to anyone.  In addition, manual data entry is simply a spreadsheet entry.
There are a few downsides:
* It requires WiFi access for the Raspberry Pi
* Sheet management can be tricky, especially if you are trying to publish charts to a webpage.

### Notes
Most of the spreadsheet is fairly obvious.  Data is entered into the appropriate sheets (Environment, Agronomic, Phenotype), with a sheet for data aggregation (Work) and several sheets for display (TempAverage, Dashboard, Camera).s  The MVP software logs sensor readings via the Google API directly to the spreadsheet, and formulas (in Work) automatically update the results.

### Data Management
It is assumed that a new spreadsheet is created for each trial (growth run).  The easiest way to do this is to copy a template spreadsheet and rename it to the start date of the trial ("Trial 2020 01 01").  This also assumes that the trial start date is updated in /home/pi/MVP/python/env.py, as the date is needed for calculating the week of temperature averages.  The spreadsheet id is also stored in env.py so the code knows where to send the data.

### Chart and web pages
It is easiest to forgo setting up a website and just use the spreadsheet for web information.  Everything currently on the website is available via the spreadsheet. 

Publishing and linking graphs into a website is possible, but it is a problem if you create new spreadsheet for each trial, as the charts have to be manually re-linked.  An alternative is to copy off the spreadsheet at the end of a trial, then clear the existing spreadsheet for the next trial.  The Google API also lacks a function to 'print' the charts to a png file, so they cannot be published and statically displayed as with the current Python generated charts.

This management of spreadsheets (copying or clearing) will likely be made into a Python function if this route is adopted for a future MVP iteration.