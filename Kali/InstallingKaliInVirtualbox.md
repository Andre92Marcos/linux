1 - Choose graphical installation
2 - Choose language and keyboard layout
3 - Hostname: Kali
4 - Domain Name:  #leave empty#
5 - Choose root’s password
6 - For the partition disks choose: “Guided - use entire disk”
7 - All files in one partition
8 - Finish partition and write changes to disk
9 - Write Changes to disk : Yes
10 - Use a network mirror: No
11 - Install the GRUB loader to the master disk: Yes.
12 - Finish Installation and wait for reboot
13 - Open firefox and go to docs.kali.org
14 - Choose Kali sources.list Repositories
15 - Copy the deb line to /etc/apt/sources.list
16 - Run apt update
17 - Run apt install linux-headers-$(uname -r)
18 - Go to /media/cdrom and run ./VBoxLinuxAdditions.run

Note: If installation fail try installing giving more memory to the disk but usually 8gb or 16gb should be enough
