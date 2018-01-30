# Digital Ocean Servers

### 1. [Initial Server Setup with Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04)

  * `sudo ufw allow proto tcp from any to any port 80,443`
    * this will [allow All Incoming HTTP and HTTPS](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands#allow-all-incoming-http-and-https)
  * I will probably still need to allow SQL through uwf

  After completing the initial setup I took a snapshot of the staging server on DigitalOcean

### 2. [Add swap memory](https://docs.ghost.org/docs/hosting#section-adding-swap-memory#section-adding-swap-memory)

* `dd if=/dev/zero of=/var/swap bs=1k count=1024k`
* `mkswap /var/swap`
* `swapon /var/swap`
  * do I need to `chmod` because of the message the server returned?  "swapon: /var/swap: insecure permissions 0644, 0600 suggested."

* `echo '/var/swap swap swap default 0 0' >> /etc/fstab`
  * `sudo chown -R USERNAME:USERNAME /etc/fstab` if you get denied

  * you may need `sudo` in front of these commands since you are not `root`
  * To prevent possible errors on a server with only 512mb ram configure a larger amount of swap memory

  ### 3. SSL pre-requisites
If you plan to setup SSL, you will need to point your custom domain at your server & check that it is resolving before starting the install.

link to my post "Securing my website with HTTPS and Lets Encrypt"