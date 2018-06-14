# Interface

There are basically three options for looking at charts MVP information:
* Static web page viewed
* Setting up the Raspberry Pi as a server
* Cloud UI

# Static Page
This is as simple as typing the following into a browser running on the Raspberry Pi:
/home/pi/MVP/web/index.html
The limitation is that this can only be viewed on the Raspberry Pi running the MVP code.
 
# Web Browser
This allows for more dynamic local viewing, looking at the web page over your local (home.) network, and possibly viewing your MVP on the web (with some adjustments to your router).  Our current recommendation for this is to download and install [Caddy](https://caddyserver.com/). This is a simple software package that provides full https security.  For the moment, you are on your own, though documentation will be coming.  Basically you download Caddy, unzip the file (easiest to save it to /usr/local/bin/caddy).  Then from a command prompt, simply cd to your web directory (/home/pi/MVP/web) and start caddy (simply type caddy).  With some modifications to the Caddyfile you can get fancier.

To open up the MVP to the web, you need to make the server access from the internet requires two things:
1. Getting a web address.  For most home systems you do not have an IP address, most services assign you one dynamically that changes over time.  You will need a service like [No-Ip](https://www.noip.com/) that will give you an address and manage the changing IP.
1. Setting you home router to allow access to the server (this assumes you know the local IP address of your Raspberry Pi). There are two parts here: Setting up a static IP address for your MVP Raspberry Pi, and forwarding web requests to this Raspberry.  Your home router dynamically assigns IP addresses to devices as they access and drop from you router (ie as you bring your cell phone or laptop home or away to work or school).  You need to make sure your Raspberry Pi gets the same IP address every time it is re-booted.  All routhers have basically the same capabilities, but where you find them in their software will vary.  On my LinkSys router, I "reserve" an IP address in the Conectivity/Settings menu by adding my device to the reservation list. The second part is called "Port Forwarding", this means that requests coming to your router from the web get forwarded to the correct device.  For example, a request to MyMVP.com:80 needs to get sent to your router (via the IP address), and you router needs to forward that request to 192.168.5.66:80 - which is the port Caddy may be using on your Raspberry Pi.  On my wrouter under "Security" there is a tab called "Apps and Gaming", and under that "Single Port Forwarding".  Here you will need to make two entries, one for port 80, and the other for port 443.  You give it a name ("My MVP") and enter your Raspberry Pi's local IP address; the internal and external port numbers should be the same.

# Cloud UI
While you may be able to modify your home router to open up the MVP to the web, most schools and businesses do not want to take the security risk of opening up ports to the internet.  That is why MarsFarm has created a "Cloud" UI, someplace you can replicate your data to, and view charts, without having to change your network settings.
