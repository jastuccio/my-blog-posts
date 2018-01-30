# Initial DigitalOcean Server Setup with Ubuntu 16.04

[initial-server-setup-with-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04)

- build a droplet using Ubuntu 16

1. ssh into the droplet as root
    - $ ssh root@_**SERVER IP ADDRESS**_

2. Create a user account

    - $ adduser _**username**_
        - any of the additional information is not required

3. Add your new user to the sudo group

    - $ usermod -aG sudo _**username**_

4. Public key authentication

## **ssh keygen information unedited**

Copy the Public Key

After generating an SSH key pair, you will want to copy your public key to your new server. We will cover two easy ways to do this.

Option 1: Use ssh-copy-id
If your local machine has the ssh-copy-id script installed, you can use it to install your public key to any user that you have login credentials for.

Run the ssh-copy-id script by specifying the user and IP address of the server that you want to install the key on, like this:

`ssh-copy-id sammy@SERVER_IP_ADDRESS`
After providing your password at the prompt, your public key will be added to the remote user's .ssh/authorized_keys file. The corresponding private key can now be used to log into the server.

Option 2: Manually Install the Key
Assuming you generated an SSH key pair using the previous step, use the following command at the terminal of your local machine to print your public key (id_rsa.pub):

`cat ~/.ssh/id_rsa.pub`
This should print your public SSH key, which should look something like the following:

id_rsa.pub contents
`ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDBGTO0tsVejssuaYR5R3Y/i73SppJAhme1dH7W2c47d4gOqB4izP0+fRLfvbz/tnXFz4iOP/H6eCV05hqUhF+KYRxt9Y8tVMrpDZR2l75o6+xSbUOMu6xN+uVF0T9XzKcxmzTmnV7Na5up3QM3DoSRYX/EP3utr2+zAqpJIfKPLdA74w7g56oYWI9blpnpzxkEd3edVJOivUkpZ4JoenWManvIaSdMTJXMy3MtlQhva+j9CgguyVbUkdzK9KKEuah+pFZvaugtebsU+bllPTB0nlXGIJk98Ie9ZtxuY3nCKneB+KjKiXrAvXUPCI9mWkYS/1rggpFmu3HbXBnWSUdf localuser@machine.local
`
Select the public key, and copy it to your clipboard.

To enable the use of SSH key to authenticate as the new remote user, you must add the public key to a special file in the user's home directory.

On the server, as the root user, enter the following command to temporarily switch to the new user (substitute your own user name):

`su - username`
Now you will be in your new user's home directory.

Create a new directory called .ssh and restrict its permissions with the following commands:

* `mkdir ~/.ssh`
* `chmod 700 ~/.ssh`

Now open a file in .ssh called authorized_keys with a text editor. We will use nano to edit the file:

`nano ~/.ssh/authorized_keys`
Now insert your public key (which should be in your clipboard) by pasting it into the editor.

Hit CTRL-x to exit the file, then y to save the changes that you made, then ENTER to confirm the file name.

Now restrict the permissions of the authorized_keys file with this command:

`chmod 600 ~/.ssh/authorized_keys`
Type this command once to return to the root user:

exit
Now your public key is installed, and you can use SSH keys to log in as your user.

To read more about how key authentication works, read this tutorial: How To Configure SSH Key-Based Authentication on a Linux Server.

Next, we'll show you how to increase your server's security by disabling password authentication.

--------

### Disable Password Authentication (Recommended)

>**Note: Only disable password authentication if you installed a public key to your user as recommended in the previous section, step four. Otherwise, you will lock yourself out of your server!**

As root or your new sudo user:

* $ `sudo nano /etc/ssh/sshd_config`
  * uncomment `PasswordAuthentication`
  * change its value to "no"

  >Here are two other settings that are important for key-only authentication and are set by default. If you haven't modified this file before, you do not need to change these settings:

>* sshd_config — Important defaults
  * `PubkeyAuthentication yes`
  * `ChallengeResponseAuthentication no`

Reload the SSH daemon:

* $ `sudo systemctl reload sshd`

Test Log In:

$ `ssh _**username**_ @ _**SERVER-IP-ADDRESS_**`

-----

###Set Up a Basic Firewall

lets use the use the UFW firewall

$ `sudo ufw app list`

allow SSH connections: $ `sudo ufw allow OpenSSH`

enable the firewall: $ `sudo ufw enable`

$ `sudo ufw status`

_____

set the timezone:
$ `sudo dpkg-reconfigure tzdata`

If you install and configure additional services, you will need to adjust the firewall settings to allow acceptable traffic in. You can learn some common UFW operations in [this guide](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands).
