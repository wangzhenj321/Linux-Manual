Creating a share on Linux and then accessing it from Windows is actually a bit easier than the other way around. First, we’ll create the shared folder on the Linux system. Then, we’ll look at how to access it from a Windows PC.

1. Create the Share on Linux
	
	To set up a shared folder on a Linux that Windows to access, start with installing Samba (software 							that provides access to SMB/CIFS protocols used by Windows). At the terminal, use the following command:
	```
	sudo apt-get install samba
	```
	After Samba installs, configure a username and password that will be used to access the share:
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExODQ1MTYwNTRdfQ==
-->