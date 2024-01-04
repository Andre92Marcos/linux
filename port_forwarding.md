# Port Forwarding

## From local port to remote port

We can use ssh to accomplish this

	ssh -L 5000:<remote_ip>:5001 root@<remote_ip>

This commands sends incoming traffic on localhost:5000 to <remote_ip>:5001

## From local port to another local port

We can use socat for this

	socat TCP4-LISTEN:5001,fork TCP4:localhost:5000

This sends all incoming traffic in port 5001 to 5000
Can be used with the previous ssh command