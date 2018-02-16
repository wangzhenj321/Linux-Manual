Creating a share on Linux and then accessing it from Windows is actually a bit easier than the other way around. First, we’ll create the shared folder on the Linux system. Then, we’ll look at how to access it from a Windows PC.

## Create the Share on Linux
	
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
mkdir ~/Desktop/Share
```
Now, use your favorite editor to configure the smb.conf file. We’re using Vi here.
```
sudo vi /etc/samba/smb.conf
```
Scroll down to the end of the file and add these lines:
```
[Share]
path = /path/to/share
writeable = yes
browseable = yes
public = yes
create mask = 0644
directory mask = 0755
force user = shareuser
```
Save the file and close your editor.  Now, you just need to restart the SMB service for the changes to take effect.
```
sudo service smbd restart
```
Your shared folder should now be accessible from a Windows PC.

## Access the Linux Share from Windows

Now, let’s add the Linux share to our Windows Desktop.  Right-click somewhere on your Desktop and select New > Shortcut.

![](img/samba-share-on-linux/fig1.png?raw=true)

Type in the network location of the shared folder, with this syntax:
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY5MjkyNDY1NV19
-->