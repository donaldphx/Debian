# Install and Setting up a Debian #

## sudo and root ###

The **whereis** function is used to find the path of a file or an app.

``` BASH
whereis sudo
```

### Enable sudo for user and disable root account ###

When you enable **sudo**, always disable the **root** account. You should never have both enabled, as it doubles the surface for malicious software or actors to compromise the system.

- First, you need to install **sudo**. Switch to the root account temporarily by typing

``` BASH
su  # Root account
apt update && apt install sudo # refresh the sources and install sudo
````
- Assign user to the **sudo** group

``` BASH
nano /etc/sudoers
```

Add username and leave the rest the same under ``` BASH root ALL=(ALL:ALL) ALL ```
  
```` BASH
your-user ALL=(ALL:ALL) ALL
````

CTRL + O to save the changes and CTRL +X to close it



```` BASH
usermod -a -G sudo your_user_name  # assign your user to the sudo group
````
  
  _full system reboot_.

- Check if **sudo** is indeed anable

````BASH
sudo apt update && apt upgrade
````

- Disable (lock) the root account by typing

````BASH
sudo passwd -l root
````



## Install a package ##

```` BASH
sudo apt install ./<file>.deb
````

### System update ###

```` BASH
sudo apt update && apt upgrade
````

## Completely erase a package ##

```` BASH
sudo apt-get remove --purge
````

The command **remove** only does not delete the setting files in **/etc**




Installing RPM In SUSE Linux (SLES)

Simply use the following syntax to install rpm file as root user:
zypper install file.rpm

OR
rpm -ivh file.rpm

OR yast method still works on an older version of SLES but it is now DEPRECATED on the latest version:
yast -i file.rpm

OR
yast2 -i file.rpm

So what happens when you use the yast2 method? For example, here is how I try to install atop*.rpm using the yast2 method:
yast2 -i atop-2.8.1-bp155.1.6.x86_64.rpm
