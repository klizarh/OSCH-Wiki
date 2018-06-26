# Web Server
How to set up a web server on your Raspberry Pi and make it accessible via the internet.
These instructions will use the Caddy web server and walk you through modifying your home router to forward a port to your Raspberry Pi Caddy server.
These instructions are for setting up the Caddy server.  Note that setting up the server is only part of making your MVP web accessible, you will also need to obtain a DNS name and modify your router and forward a port to the server.  Instructions for these steps are found [[here | MVP-Web-Access]]
You can get Caddy from [[Caddy Server | https://caddyserver.com/]].  Follow the download instructions, then copy to /usr/local/bin/caddy (note, you will need to be sudo to have permissions to make the move).
For a simple quick test, open a terminal and change to your web directory:
> cd /home/pi/MVP/web

then run:

> caddy

You need to leave the terminal window open since it is holding the process.
For more sophisticated running you will need a script that will start the server on boot.  A script for this, and a Caddy configuration file can be found in the repository.  With a little configuration, you can even add https security to the server.