Author: Brett Swan
Project: Pi Hosting

The purpose of this project is to build my personal website and learn how to configure a Raspberry Pi
as a $35 webserver. As of 4/12/17, I have redone much of my personal site using HTML and CSS. I have also purchased my
own domain name at brettswan.info. My objective for 4/15/17 is to figure out the setup of the DNS servers so that entering
my domain name will route the request to my home network. After that I need to configure my router and Raspberry Pi to respond
to HTML requests.

SYSTEM COMPONENTS:

Raspberry Pi 3
16Gb San Disk MicroSD
ASUS RT-AC66U router
Motorola SURFboard SBG6782-AC modem & router (included with Time Warner Cable Internet Service)
Spectrum (Time Warner Cable) Residential Internet Service
Domain name from GoDaddy.com
Markup :  - - - -

RASPBERRY PI CONFIGURATION:

Fresh installation of Raspbian Jessie operating system stored on a 16gb MicroSD card

In terminal, enter command "sudo apt-get install apache2 php5 libapache2-mod-php5"

Then enter "sudo service apache2 restart" to restart the Apache service

To host a single site, move your index.html file and other supporting files to /var/www/ using "sudo mv [your file name] /var/www/"

Now enter command "ifconfig" and write down your Raspberry Pi's IP Address

ROUTER CONFIGURATION:

I purchased my router several months ago and use the TWC supplied modem/router only as a modem and use the ASUS
RT-AC66U as the main access point for my home network. First, login to the admin page for your router by entering
192.168.1.1 in your preferred web browser. Once on the router's start page, locate the WAN tab under the "Advanced Settings" section in the lower left part of the screen. Set "Enable WAN" to "Yes". From there click on the "Virtual Server / Port Forwarding" tab. First enable port forwarding. Then add an entry in the port forwarding list by entering the service name of your choosing, leave the "Source Target" field empty, enter 80 in the "Port Range" field, enter your Raspberry Pi's IP address in the "Local IP" field, enter 80 for the "Local Port" field, then choose "BOTH" for the Protocol field. Then press the plus icon at the end of the row, followed by "APPLY" to save your new settings.

Now return to the "Network Map" page and write down the listed WAN IP. Now enter "www.whatsmyip.org" . If the IP address listed at the top of the screen does not match the WAN IP shown in your router, enter 192.168.0.1 to access your modem's user interface. In the firewall settings, turn off "Block WAN connections". This was the default configuration from Spectrum.

To test your system, type your WAN IP address into your preferred web browser. It should display your website's "index.html" file.

DOMAIN CONFIGURATION (ASSUMING YOUR DOMAIN IS FROM GODADDY):
Sign in on GoDaddy and click on your name (top right) to drop down the menu. On the left side under "Quick Links", click on "Manage My Domains". For the domain you would like to use, press the gear icon and then "Manage DNS". In the "Records" section, click on the pencil icon for the row with type "A" and name "@" to edit the "Value" field. Replace the current value with your network's WAN IP address. Your site should be reachable from your domain name within the next 24 hours.
