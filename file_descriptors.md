A file descriptor (FD) in Unix/Linux operating systems is an indicator of connection maintained by the kernel to perform Input/Output (I/O) operations.

By default, the first three file descriptors in Linux are:

	Data Stream for Input
	STDIN – 0
	Data Stream for Output
	STDOUT – 1
	Data Stream for Output that relates to an error occurring.
	STDERR – 2


Redirecting stderr and stdout:

	find /etc/ -name shadow 2> /dev/null 1> stdout.txt

Redirecting stdin:

	cat < data.txt

Redirecting stdin as a stream and stdou to file

	cat << EOF > stream.txt
