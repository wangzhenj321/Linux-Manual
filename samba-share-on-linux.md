Creating a share on Linux and then accessing it from Windows is actually a bit easier than the other way around. First, we’ll create the shared folder on the Linux system. Then, we’ll look at how to access it from a Windows PC.

1. Create the Share on Linux
	
	To set up a shared folder on a Linux that Windows to access, start with installing Samba (software 							that provides access to SMB/CIFS protocols used by Windows). At the terminal, use the following command:
	```
	sudo apt-get install samba
	```
	After Samba installs, configure a username and password that will be used to access the share:
	```
	smbpasswd -a geek
	```
	Note: In this example, we are using ‘geek’ since we already have a Linux user with that name, but you can choose any name you’d like.
	
	![](img/apt-get/fig1.png?raw=true)
	
	Create the directory that you’d like to share out to your Windows computer.  We’re just going to put a folder on our Desktop.
	```
	```
	
	
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4Mjk3MzUzNTBdfQ==
-->