# Part 1: init scripts, runlevels, and upstart

Ubuntu has 2 different mechanisms for starting system services:

- The traditional mechanism based on **run levels**, and scripts in `/etc/init.d` and `/etc/rc?.d` directories.

- A new mechanism known as **upstart**.

Some services are started using one mechanism and others using the other. If you want to control the services, it’s necessary to understand these mechanisms.

## Run levels and init.d scripts – the traditional mechanism

Linux has the concept of **run levels**, in all distros as part of the **Linux Base Specification(LBS)**. They can be considered to be "modes" in which Linux runs.

## References

1. [Ubuntu startup – init scripts, runlevels, upstart jobs explained](http://www.pathbreak.com/blog/ubuntu-startup-init-scripts-runlevels-upstart-jobs-explained)

# Part 2: `/etc/init.d/`, `/etc/rc?.d/`, and `/etc/init/`

## References

1. [Linux系统下/etc/init/和/etc/init.d/的区别](https://liaolushen.github.io/2015/09/11/Linux%E7%B3%BB%E7%BB%9F%E4%B8%8B-etc-init-%E5%92%8C-etc-init-d-%E7%9A%84%E5%8C%BA%E5%88%AB/)
