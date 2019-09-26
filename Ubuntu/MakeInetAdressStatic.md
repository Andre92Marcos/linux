Edit /etc/network/interfaces, this file will be something like this

    auto eth0 iface eth0 inet dhcp

Change it to something like (depending on the interface you want):

    auto eth0 
    iface eth0 inet static 
    address 10.253.0.50 
    netmask 255.255.255.0 
    network 10.253.0.0 
    gateway 10.253.0.1 
    dns-nameservers 8.8.8.8
