iptables is a command-line firewall utility that uses policy chains to allow or block traffic. 

# Tables

The iptables firewall has the ability to do more than just low-level packet filtering. It defines what type of firewall functionality is taking place. There are four tables in the iptables utility. The tables offer the following functionalities:
	
	filter—The filter table is the packet filtering feature of the firewall. In this table, access control decisions are made for packets traveling to, from, and through your Linux system.

nat—The nat table is used for Network Address Translation (NAT). Firewalls can be set up for NAT, which is a different security feature than packet filtering.

mangle—As you suspect, packets are mangled (modified) according to the rules in the mangle table. Mangling packets is used in Network Address Translation.

raw—The raw table is used to exempt certain network packets from something called “connection tracking.” This feature is important when you are using Network Address Translation and Virtualization on your Linux server.

Of all the tables listed, three focus on Network Address Translation. Therefore, the filter table is the primary table to focus on for basic firewall packet filtering.


# Chains

The netfilter/iptables firewall categorizes network packets into categories, called chains. There are five chains (categories) that a network packet can be designated as, as follows:

	INPUT—Network packets coming into the Linux server
    FORWARD—Network packets coming into the Linux server that are to be routed elsewhere
    OUTPUT—Network packets coming out of the Linux server
    PREROUTING—Used by NAT, for modifying network packets when they come into the Linux server
    POSTROUTING—Used by NAT, for modifying network packets before they come out of the Linux server

Which netfilter/iptables table you choose to work with determine what chains are available for categorizing network packets.

After a network packet is categorized into a specific chain, iptables can determine what policies or rules apply to that particular packet.


# Rules, Policies and Targets

For each network packet, a rule can be set up defining what to do with that individual packet. Network packets can be identified many ways by the netfilter/iptables firewall. These are a few of the ways:

    Source IP address  
    Destination IP address 
    Network protocol 
    Inbound port 
    Outbound port 
    Network state

If no rule exists for a particular packet, then the overall policy is used. Each packet category or chain has a default policy. After a network packet matches a particular rule or falls to the default policy, action on the packet can occur. The action taken depends upon what iptable target is set. Here are a couple of actions (targets) that can be taken:

    ACCEPT—Network packet is accepted into the server. 
    REJECT—Network packet is dropped and not allowed into the server. A rejection message is sent. 
    DROP—Network packet is dropped and not allowed into the server. No rejection message is sent.

While REJECT gives a rejection message, DROP is quiet. You may consider using REJECT for internal employees, who should be told that you are rejecting their outbound network traffic and why. Consider using DROP for inbound traffic so that any malicious personnel are unaware that their traffic is being blocked.

Note: There are a couple of additional more sophisticated targets for iptables, such as QUEUE. You can find out more about these targets via the man iptables command.


# Iptables Options


-t table 

    The iptables command listed along with this switch is applied to the table. By default, the filter table is used. 

    iptables -t filter -P OUTPUT DROP 

-P chain target 

    Sets the overall policy for a particular chain. The rules in the chain are checked for matches. If no match occurs, then the chain’s listed target is used. 

    iptables -P INPUT ACCEPT

-A chain 

    Sets a rule, called an “appended rule,” which is an exception to the overall policy for the chain designated. 

    iptables -A OUTPUT -d 10.140.67.25 -j REJECT

-I rule# chain 

    Inserts an appended rule into a specific location, designated by the rule#, in the appended rule list for the chain designated.

    iptables -I 5 INPUT -s 10.140.67.23 -j DROP 

-D chain rule# 

    Deletes a particular rule, designated by the rule#, from the chain designated. 

    iptables -D INPUT 5 

-j target

    If the criteria in the rule are met, the firewall should jump to this designated target for processing.

    iptables -A INPUT -s 10.140.67.25 -j DROP 

-d IP address 

    Assigns the rule listed to apply to the designated destination IP address.

    iptables -A OUTPUT -d 10.140.67.25 -j REJECT 

-s IP address 

    Assigns the rule listed to apply to the designated source IP address. 

    iptables -A INPUT -s 10.140.67.24 -j ACCEPT

-p protocol 

    Assigns the rule listed to apply to the protocol designated.

    iptables -A INPUT -p icmp -j DROP 

--dport port# 

    Assigns the rule listed to apply to certain protocol packets coming into the designated port#. 

    iptables -A INPUT -p tcp --dport 22 -j DROP 

--sport port# 

    Assigns the rule listed to apply to certain protocol packets going out of the designated port#. 

    iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT

-m state --state network state 

    Assigns the rule listed to apply to the designated network state(s). 

    iptables -A INPUT -m state --state RELATED,ESTABLISH -j ACCEPT



Note: The --dport option must accompany a particular protocol, for example, -p tcp. 



Saving Iptables Configurations

All modifications must be saved to the iptables configuration file, /etc/sysconfig/iptables, because this is the file used at system boot to load the firewall.

 iptables-save > /etc/sysconfig/iptables

You can also remove all the modifications for the current netfilter/iptables firewall by using the flush option, iptables -F. After this is completed, all the rules (but not the policies) are removed.

A flush of the rules does not affect the iptables configuration file. To restore the firewall to its original condition, use the iptables-restore command.

	iptables-restore < /etc/sysconfig/iptables
