To see all the files the package installed onto your system, do this:

```
dpkg-query -L <package_name>
```

To see the files a .deb file will install

```
dpkg-deb -c <package_name.deb>
```

To see the files contained in a package NOT installed, do this once (if you haven't installed `apt-file` already):

```
sudo apt-get install apt-file
sudo apt-file update
```

then

```
apt-file list <package_name>
```
