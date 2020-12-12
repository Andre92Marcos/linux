# Package Management

Packages are archives that contain binaries of software, configuration files, information about dependencies and keep track of updates and upgrades. The features that most package management systems provide are:

	Package downloading
	Dependency resolution
	A standard binary package format
	Common installation and configuration locations
	Additional system-related configuration and functionality
	Quality control

## Advanced Package Manager (APT)

Debian-based Linux distributions use the APT package manager. A package is an archive file containing multiple ".deb" files. The dpkg utility is used to install programs from the associated ".deb" file. APT makes updating and installing programs easier because many programs have dependencies. When installing a program from a standalone ".deb" file, we may run into dependency issues and need to download and install one or multiple additional packages. APT, by packaging together all of the dependencies needed to install a program.

Each Linux distribution uses software repositories that are updated often. When we update a program or install a new one, the system queries these repositories for the desired package. Repositories can be labeled as stable, testing, or unstable. Most Linux distributions utilize the most stable or "main" repository. This can be checked by viewing the contents of the /etc/apt/sources.list file.


