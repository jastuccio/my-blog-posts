###updating ubuntu

from [install-discourse-in-under-30-minutes](http://blog.discourse.org/2014/04/install-discourse-in-under-30-minutes/)

May 15, 2014
What is recommended to keep Ubuntu up to date? I assume it doesn't do any sort of automatic updates, or does it? A way to schedule automatic updates at 3am or something would be good, or maybe weekly?

-----

Kane York says:
May 15, 2014
The way that you're "supposed" to have unattended critical updates in Ubuntu is

sudo dpkg-reconfigure -plow unattended-upgrades
It brings up a ncurses window and you choose Yes or No.

-----

Greg Swallow says:
May 22, 2014
I found an easy way too to have the server email you when there are updates available:

apt-get install sendmail 
apt-get install apticron
(and edit /etc/apticron/apticron.conf and just change the line: EMAIL = "root" to EMAIL = "youremail@address.com")