## The sensor is not the subject.
When I started modeling the MVP data, I initially was recording the 'SI7021 temperature', the name of the sensor and the attribute I was collecting. This seemed simple and easy until I explored Fairchild Garden's data, and started doing some report queries.  Fairchild was not using sensors, all measurements were manually done by students, from thermometer temperature readings to plant size and weight - there were no 'sensors' to which one could attach the measurement.  My test MVP also presented challenges when I installed five different temperature sensors, one SI7021 and four DS18B20, three were in different areas of the chamber, one was outside for 'ambient' temperature, and one was in the reservoir water.  For one report I wanted to show all the temperature readings, but at times I wanted only the canopy air temperature.  While knowing the name of the sensor is needed for maintenace and hardware analysis, normally I found I really wanted to now about the environment (canopy air temperature). 

## Main Subjects
* Environmental Subjects
** Air
** Water/Nutrient
* Plant (and sub-parts)
## Semantics and Ontology

I keep going back to Barry Smith’s definition that a measurement records an attribute of a substance. The substance is the ‘thing’ of interest: plant, air, water. It seems obvious, but can get complicated. There is a constellation of information here that gets jumbled together, all parts are needed, but they are easy to confuse. The constellation consists of the subject, where it is located (discriminator when there are multiple potential subjects) and the instrument used to capture the measurement.
I think I am making a mistake when I talk about a ‘camera image’. The image is really an image of a plant (or collection of plants), the camera is the instrument used to take the image. However, when there are multiple images from different instruments, the camera used becomes the easiest thing by which to call the image: the ‘NOIR Camera’ -vs- ‘Left side camera’ (and even here we are mixing type and location as discriminators). It is common to have the sensor be the ‘proxy’ for the subject.
There is a similar problem in taking temperature. The temperature is of air, water or possibly a leaf; the sensor (si7021) is the instrument. Confusion comes when talking about location, is location an attribute of the sensor, the subject, or both? I am recording ‘reservoir temperature’, when it is actually the ‘temperature of the water located in the reservoir’. Or similarly I have ‘si7021_top’ which is shorthand for ‘temperature for the air at the top of the chamber recorded with the si7021 sensor’. In common discussion, we abbreviate and use proxies, as it is easy for most of us to assume the context and fill in the missing pieces - something computers struggle with.
I am inclined to avoid this proxy confusion by having two fields: subject and instrument. I would then have location be a part of the subject (sensor location could be found in the context/environment document). I will reserve discussion of the details for a further post.
> {
> ‘subject’:{‘name’:, ‘location’:},
> ‘instrument’{‘name’:,‘type’:, ‘location’:, ‘protocol’:}
> }

> example:

> {
> ‘subject’:{‘name’:‘water’, ‘location’:‘reservoir’}.
> ‘insturment’:{‘name’:‘mcp9808’}.
> ‘attribute’:‘temperature’,
> ‘value’:22
> }

As a side note, fun comes when we have human observations. We have already captured the person information in the ‘user’, but are they also the instrument (technically ‘yes’, the person has two roles in this observation: recorder and instrument)? If I am manually recording EC, the instrument is both the EC meter and my eye; but if I am recording taste do I want/need to record my tongue as the instrument? My leanings is to not have an instrument in this situation. This is the crazy level to which I think we need to define our data issues.