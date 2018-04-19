***add-apt-repository***  is  a  script  which adds an external APT repository to either /etc/apt/sources.list or a file in /etc/apt/sources.list.d/ or removes an already existing repository.

## How to find and remove obsolete PPA repositories on Ubuntu

> Err http://ppa.launchpad.net trusty/main amd64 Packages  404  Not Found  
> Err http://ppa.launchpad.net trusty/main i386 Packages  404  Not Found
> W: Failed to fetch http://ppa.launchpad.net/finalterm/daily/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found
> 
> W: Failed to fetch http://ppa.launchpad.net/finalterm/daily/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
> 
> E: Some index files failed to download. They have been ignored, or old ones used instead.

When you attempt to update APT package indexes, "404 Not Found" errors can often happen after distro upgrade. That is, after you upgraded your Ubuntu release, some third-party PPA repositories which you added on the old release are no longer supported on the upgraded release. In that case, you can ***identify and purge those broken PPA repositories as follows.***

#### Find out the PPAs which cause "404 Not Found" failures.

```
sudo apt-get update | grep "Failed"
```



In this example, the PPA repository which is no longer supported in Ubuntu Trusty is "ppa:finalterm/daily".

#### Go ahead and remove the PPA repository.

```
sudo add-apt-repository --remove ppa:finalterm/daily
```

You have to repeat this process for every obsolete PPA repository that you found from above.


After removing all obsolete PPA repositories, re-run "apt-get update" to check all of them have been successfully removed.
