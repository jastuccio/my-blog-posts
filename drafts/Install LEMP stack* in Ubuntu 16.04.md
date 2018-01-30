## Install LEMP stack* in Ubuntu 16.04

LEMP stack = Linux, Nginx, MySQL, PHP 


Prerequisites
you should have a regular, non-root user account on your server with sudo privileges. See "Initial DigitalOcean Server Setup with Ubuntu 16.04.md"


###1: Install the Nginx Web Server


$ sudo apt-get update
$ sudo apt-get install nginx

enable the HTTP & HTTPS.  You are using HTTPS for your site right?

You can enable this by typing:

$ sudo ufw allow 'Nginx Full'

>I need to explore if this should be changed to 'Nginx HTTPS' after installing SSL since we want all traffic to eventually be HTTPS

verify the change: $ sudo ufw status

-----

### 2: Check your Web Server

find your server's public IP address by typing one of the following into your terminal:

ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'
 
  * This will print out a few IP addresses. You can try each of them in turn in your web browser.

As an alternative, you can check which IP address is accessible as viewed from other locations on the internet:

curl -4 icanhazip.com
Type one of the addresses that you receive in your web browser. It should take you to Nginx's default landing page:

http://server_domain_or_IP
Nginx default page

If you see the above page, you have successfully installed Nginx.

### Step 2: Install ~~MySQL~~ to Manage Site Data

Lets [intstall MariaDB](https://downloads.mariadb.org/mariadb/repositories/#mirror=digitalocean-nyc&distro=Ubuntu&distro_release=xenial--ubuntu_xenial&version=10.1) instead.

* $ sudo apt-get install software-properties-common
* $ sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xF1656F24C74CD1D8
* $ sudo add-apt-repository 'deb [arch=amd64,i386,ppc64el] http://nyc2.mirrors.digitalocean.com/mariadb/repo/10.1/ubuntu xenial main'
* $ sudo apt update
* $ sudo apt install mariadb-server
* $ sudo mysql_secure_installation

Disallow root login remotely? [Y/n] y??????

read [securing-mariadb](https://mariadb.com/kb/en/mariadb/securing-mariadb/)


###Step 3: Install PHP for Processing

Nginx does not contain native PHP processing we will need to install php-fpm (fastCGI process manager)

$ sudo apt-get install php-fpm php-mysql

Configure the PHP Processor to make our setup more secure.

$ sudo nano /etc/php/7.0/fpm/php.ini

>What we are looking for in this file is the parameter that sets cgi.fix_pathinfo. This will be commented out with a semi-colon (;) and set to "1" by default.

>This is an extremely insecure setting because it tells PHP to attempt to execute the closest file it can find if the requested PHP file cannot be found. This basically would allow users to craft PHP requests in a way that would allow them to execute scripts that they shouldn't be allowed to execute.

uncomment the line and set it to "0":
cgi.fix_pathinfo=0

Save and close the file

restart PHP so the change takes effect:

$ sudo systemctl restart php7.0-fpm

###Step 4: Configure Nginx to Use the PHP Processor

tell Nginx to use our PHP processor for dynamic content.


$ sudo nano /etc/nginx/sites-available/default

Remove comments so the Nginx default server block file looks like this:

/etc/nginx/sites-available/default
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/html;
    index.php index index.html index.htm index.nginx-debian.html;

    server_name server's domain name or public IP address;

    location / {
        try_files $uri $uri/ =404;
    }
}


we added `index.php` as the first value of our index directive so that files named index.php are served, if available, when a directory is requested.

modify the server_name directive to point to our server's domain name or public IP address.

\uncomment a segment of the file that handles PHP requests. This will be the 

location ~\.php$ location block, the included fastcgi-php.conf snippet, and the socket associated with php-fpm.


also uncomment the location block dealing with .htaccess files. Nginx doesn't process these files. If any of these files happen to find their way into the document root, they should not be served to visitors.
The changes that you need to make are in red in the text below:

/etc/nginx/sites-available/default
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/html;
    index index.php index.html index.htm index.nginx-debian.html;

    server_name server_domain_or_IP;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.0-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }
}
When you've made the above changes, you can save and close the file.

Test your configuration file for syntax errors by typing:

sudo nginx -t
If any errors are reported, go back and recheck your file before continuing.

When you are ready, reload Nginx to make the necessary changes:

sudo systemctl reload nginx
Step 5: Create a PHP File to Test Configuration
Your LEMP stack should now be completely set up. We can test it to validate that Nginx can correctly hand .php files off to our PHP processor.

We can do this by creating a test PHP file in our document root. Open a new file called info.php within your document root in your text editor:

sudo nano /var/www/html/info.php
Type or paste the following lines into the new file. This is valid PHP code that will return information about our server:

/var/www/html/info.php
<?php
phpinfo();
When you are finished, save and close the file.

Now, you can visit this page in your web browser by visiting your server's domain name or public IP address followed by /info.php:

http://server_domain_or_IP/info.php
You should see a web page that has been generated by PHP with information about your server:

PHP page info

If you see a page that looks like this, you've set up PHP processing with Nginx successfully.

After verifying that Nginx renders the page correctly, it's best to remove the file you created as it can actually give unauthorized users some hints about your configuration that may help them try to break in. You can always regenerate this file if you need it later.

For now, remove the file by typing:

sudo rm /var/www/html/info.php
Conclusion
You should now have a LEMP stack configured on your Ubuntu 16.04 server. This gives you a very flexible foundation for serving web content to your visitors.