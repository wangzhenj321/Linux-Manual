**Table of contents**

[1. Files](#1-files)

- [1.1. General](#11-general)

- [1.2. Sorts of files](#12-sorts-of-files)

[2. About partitioning](#2-about-partitioning)

- [2.1. Why partition?](#21-why-partition)

- [2.2. Partition layout and types](#22-partition-layout-and-types)

- [2.3. Mount points](#23-mount-points)

[3. More file system layout](#3-more-file-system-layout)

- [3.1. Visual](#31-visual)

- [3.2. The file system in reality](#32-the-file-system-in-reality)

[4. References](#4-references)


## 1. Files

### 1.1. General

A simple description of the UNIX system, also applicable to Linux, is this:

**"On a UNIX system, everything is a file; if something is not a file, it is a process."**

This statement is true because there are special files that are more than just files (named pipes and sockets, for instance), but to keep things simple, saying that everything is a file is an acceptable generalization. A Linux system, just like UNIX, makes no difference between a file and a directory, since a directory is just a file containing names of other files. Programs, services, texts, images, and so forth, are all files. Input and output devices, and generally all devices, are considered to be files, according to the system.

In order to manage all those files in an orderly fashion, man likes to think of them in an ordered tree-like structure on the hard disk, as we know from MS-DOS (Disk Operating System) for instance. The large branches contain more branches, and the branches at the end contain the tree's leaves or normal files. For now we will use this image of the tree, but we will find out later why this is not a fully accurate image.

### 1.2. Sorts of files

Most files are just files, called **regular** files; they contain normal data, for example text files, executable files or programs, input for or output from a program and so on.

While it is reasonably safe to suppose that everything you encounter on a Linux system is a file, there are some exceptions.

- **Directories**: files that are lists of other files.

- **Special files**: the mechanism used for input and output. Most special files are in /dev, we will discuss them later.

- **Links**: a system to make a file or directory visible in multiple parts of the system's file tree. We will talk about links in detail.

- **(Domain) sockets**: a special file type, similar to TCP/IP sockets, providing inter-process networking protected by the file system's access control.

- **Named pipes**: act more or less like sockets and form a way for processes to communicate with each other, without using network socket semantics.

This table gives an overview of the characters determining the file type:

| Symbol | Meaning |
| --- | --- |
| -	| Regular file |
| d	| Directory |
| l	| Link |
| c	| Special file |
| s	| Socket |
| p	| Named pipe |
| b	| Block device |

## 2. About partitioning

### 2.1. Why partition?

Most people have a vague knowledge of what partitions are, since every operating system has the ability to create or remove them. It may seem strange that Linux uses more than one partition on the same disk, even when using the standard installation procedure, so some explanation is called for.

One of the goals of having different partitions is to achieve higher data security in case of disaster. By dividing the hard disk in partitions, data can be grouped and separated. When an accident occurs, only the data in the partition that got the hit will be damaged, while the data on the other partitions will most likely survive.

This principle dates from the days when Linux didn't have journaled file systems and power failures might have lead to disaster. The use of partitions remains for security and robustness reasons, so a breach on one part of the system doesn't automatically mean that the whole computer is in danger. This is currently the most important reason for partitioning. A simple example: a user creates a script, a program or a web application that starts filling up the disk. If the disk contains only one big partition, the entire system will stop functioning if the disk is full. If the user stores the data on a separate partition, then only that (data) partition will be affected, while the system partitions and possible other data partitions keep functioning.

Mind that having a journaled file system only provides data security in case of power failure and sudden disconnection of storage devices. This does not protect your data against bad blocks and logical errors in the file system. In those cases, you should use a RAID (Redundant Array of Inexpensive Disks) solution.

### 2.2. Partition layout and types

### 2.3. Mount points

## 3. More file system layout

### 3.1. Visual

For convenience, the Linux file system is usually thought of in a tree structure. On a standard Linux system you will find the layout generally follows the scheme presented below.

<img src="../img/general-overview-of-the-Linux-file-system/linux_file_system_layout.png">

The tree of the file system starts at the trunk or slash, indicated by a forward slash (`/`). This directory, containing all underlying directories and files, is also called the root directory or "the root" of the file system.

| Directory | Content |
| --- | --- |
| /bin | `/bin` contains commands that may be used by both the system administrator and by users, but which are required when no other filesystems are mounted (e.g. in single user mode). There must be no subdirectories in `/bin`. |
| /sbin | Utilities used for system administration (and other root-only commands) are stored in `/sbin`, `/usr/sbin`, and `/usr/local/sbin`. <ul><li>`/sbin` contains binaries essential for booting, restoring, recovering, and/or repairing the system in addition to the binaries in `/bin`.</li><li>Programs executed after `/usr` is known to be mounted (when there are no problems) are generally placed into `/usr/sbin`.</li><li>Locally-installed system administration programs should be placed into `/usr/local/sbin`.</li></ul> There must be no subdirectories in `/sbin`. |
| /lib | The `/lib` directory contains those shared library images needed to boot the system and run the commands in the root filesystem, ie. by binaries in `/bin` and `/sbin`. |
| /lib&lt;qual&gt; | There may be one or more variants of the `/lib` directory on systems which support more than one binary format requiring separate libraries. |
| /boot | The startup files and the kernel, vmlinuz. In some recent distributions also grub data. Grub is the GRand Unified Boot loader and is an attempt to get rid of the many different boot-loaders we know today. |
| /dev | Contains references to all the CPU peripheral hardware, which are represented as files with special properties. |
| /etc | Most important system configuration files are in /etc, this directory contains data similar to those in the Control Panel in Windows |
| /home | Home directories of the common users. |
| /initrd | (on some distributions) Information for booting. Do not remove! |
| /lost+found | Every partition has a lost+found in its upper directory. Files that were saved during failures are here. |
| /misc | For miscellaneous purposes. |
| /media | Mount point for removable media. In other words, where system mounts removable media. This directory contains sub-directories used for mounting removable media such as CD-ROMs, floppy disks, etc. |
| /mnt | For temporary mounting. In other words, where user can mount things. This directory is generally used for mounting filessytems temporarily when needed. |
| /net | Standard mount point for entire remote file systems |
| /opt | Typically contains extra and third party software. |
| /proc | A virtual file system containing information about system resources. More information about the meaning of the files in proc is obtained by entering the command man proc in a terminal window. The file proc.txt discusses the virtual file system in detail. |
| /root | The administrative user's home directory. Mind the difference between /, the root directory and /root, the home directory of the root user. |
| /srv | Site-specific data served by this system, such as data and scripts for web servers, data offered by FTP servers, and repositories for version control systems. |
| /tmp | Temporary space for use by the system, cleaned upon reboot, so don't use this for saving any work! |
| /usr | Programs, libraries, documentation etc. for all user-related programs. |
| /var | Storage for all variable files and temporary files created by users, such as log files, the mail queue, the print spooler area, space for temporary storage of files downloaded from the Internet, or to keep an image of a CD before burning it. |
| /sys | The sys filesystem is the location where information about devices, drivers, and some kernel features is exposed. |

**/usr**

| Directory |	Content |
| --- | --- |
| /usr/bin | Contains binary files for user programs. If you can’t find a user binary under /bin, look under /usr/bin. For example: at, awk, cc, less, scp |
| /usr/sbin | Contains binary files for system administrators. If you can’t find a system binary under /sbin, look under /usr/sbin. For example: atd, cron, sshd, useradd, userdel |
| /usr/lib | Contains libraries for /usr/bin and /usr/sbin |
| /usr/local | Contains users programs that you install from source. For example, when you install apache from source, it goes under /usr/local/apache2 |
| /usr/src | Holds the Linux kernel sources, header-files and documentation. |

### 3.2. The file system in reality

## 4. References

1. [General overview of the Linux file system](https://www.tldp.org/LDP/intro-linux/html/sect_03_01.html)
2. [Filesystem Hierarchy Standard Wiki](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
3. [Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
4. [Linux File Hierarchy Structure](https://www.geeksforgeeks.org/linux-file-hierarchy-structure/)
