The init.d directory contains a number of start/stop scripts for various services on your system.

In order to control any of the scripts in init.d manually you have to have root (or sudo) access. Each script will be run as a command and the structure of the command will look like:
/etc/init.d/command OPTION

You can disable a script by changing it’s permissions:

	$ chmod -x /etc/init.d/varnish

And reenable by updating it:

	$ chmod +x /etc/init.d/varnish
