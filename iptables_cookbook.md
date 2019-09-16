### Show chains and rules:

	iptables -L

### Show Chains and rules of a Specific Table:

	iptables -t filter -L

### Show Chains and rules Verbose:

	iptables -L -v

### Show Rules Line Numbers:

	iptables -L --line-number

### Show Commands Used to Create the Rules:

	iptables -S

### Save Changes and Restart iptables:

    iptables-save
    service iptables save 
    service iptables restart


### Enable port through firewall:
	
    iptables -A INPUT -p tcp --dport 8080 -j ACCEPT


### Remove a rule:

	iptables -D INPUT -p tcp -m tcp --sport 9000 -j ACCEPT

### Remove all rules of the current session:

	iptables  -F

### Remove Rule by Number

	iptables -D INPUT 5

### Remove Any Non Default Chain

	iptables -X

### Change the Policy of a Chain:

	iptables -P INPUT ACCEPT
	iptables -P OUTPUT DROP

### Allow Dynamic Packet Filtering

    This allows that even if the INPUT policy is set to DROP other servers can still respond to your outbound connections.

    iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
