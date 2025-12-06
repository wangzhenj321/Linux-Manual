## Description

`logger` makes entries in the system log (e.g., `/var/log/syslog` on Ubuntu/Debian or `/var/log/messages` on Red Hat/CentOS).

> The most reliable ways to determine if a Linux PC is Ubuntu/Debian-based or Red Hat/CentOS-based are by checking common system files or using a standard command-line utility.
> - The `/etc/os-release` file is available on most modern Linux distributions (including Debian, Ubuntu, Red Hat, and CentOS/Rocky/Alma Linux) and provides consistent information.
> - The `lsb_release -a` command provides distribution-specific information, but it may not be installed by default on all systems.

When the optional message argument is present, it is written to the log. If it is not present, and the `-f` option is not given either, then standard input is logged.

## Synopsis

`logger [options] message`

## Options

- `-f, --file file`
  
    Log the contents of the specified file. This option cannot be combined with a command-line message.

- `-t, --tag tag`

    Mark every line to be logged with the specified tag. The default tag is the name of the user logged in on the terminal (or a user name based on effective user ID).
