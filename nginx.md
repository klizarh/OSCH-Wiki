# NGINX
NGINX is a proxy server.  It provides security certificates (along with CertBot) and provides a secure door-way to your NerdFarm content.

## Installation
sudo apt-get install nginx -y
sudo apt-get install certbot python-certbot-nginx -t stretch-backports

It is likely that the certbot install will fail with a message that the release is not available.  See [here[(https://backports.debian.org/Instructions/) for instructions and the reason why.  The summary of what to do:
sudo leafpad /etc/apat/sources.list

Add the following line to the end of the file:
deb http://deb.debian.org/debian stretch-backports main

sudo apt-get update

Now re-run the install:
sudo apt-get install certbot python-certbot-nginx -t stretch-backport
Enter "y" at all prompts

Now let CertBot set up the certificate security.
NOTE: Make sure you have port forwarded in you router ports 80 and 443 to the internal  ip address of this Raspberry Pi.
sudo certbot --nginx

Finally, set up cron to refresh your certificates on a regular basis (once every two months)
crontab -e
and type in the following:
* * * */2 * sudo certbot renew


## Making changes
If you edit the configuration file, simply run the following from a command prompt to refresh the system
sudo systemctl restart nginx.service