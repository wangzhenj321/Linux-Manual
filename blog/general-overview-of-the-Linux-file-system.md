**Table of Contents**

[1. Files](#1-files)

- [1.1 General](#11-general)

- [1.2 Sorts of files](#12-sorts-of-files)

[2. About partitioning](#2-about-partitioning)

- [2.1 Why partition?](#21-why-partition)

- [2.2 Partition layout and types](#22-partition-layout-and-types)

- [2.3 Mount points](#23-mount-points)

[3. More file system layout](#3-more-file-system-layout)

- [3.1 Visual](#31-visual)

- [3.2 The file system in reality](#32-the-file-system-in-reality)

[References](#references)


## 1. Files

### 1.1 General

### 1.2 Sorts of files

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

### 2.1 Why partition?

### 2.2 Partition layout and types

### 2.3 Mount points

## 3. More file system layout

### 3.1 Visual

| Directory | Content |
| --- | --- |
| /bin | Common programs, shared by the system, the system administrator and the users. |
| /boot | The startup files and the kernel, vmlinuz. In some recent distributions also grub data. Grub is the GRand Unified Boot loader and is an attempt to get rid of the many different boot-loaders we know today. |
| /dev | Contains references to all the CPU peripheral hardware, which are represented as files with special properties. |
| /etc | Most important system configuration files are in /etc, this directory contains data similar to those in the Control Panel in Windows |
| /home | Home directories of the common users. |
| /initrd | (on some distributions) Information for booting. Do not remove! |
| /lib | Library files, includes files for all kinds of programs needed by the system and the users. |
| /lost+found | Every partition has a lost+found in its upper directory. Files that were saved during failures are here. |
| /misc | For miscellaneous purposes. |
| /mnt | Standard mount point for external file systems, e.g. a CD-ROM or a digital camera. |
| /net | Standard mount point for entire remote file systems |
| /opt | Typically contains extra and third party software. |
| /proc | A virtual file system containing information about system resources. More information about the meaning of the files in proc is obtained by entering the command man proc in a terminal window. The file proc.txt discusses the virtual file system in detail. |
| /root | The administrative user's home directory. Mind the difference between /, the root directory and /root, the home directory of the root user. |
| /sbin | Programs for use by the system and the system administrator. |
| /tmp | Temporary space for use by the system, cleaned upon reboot, so don't use this for saving any work! |
| /usr | Programs, libraries, documentation etc. for all user-related programs. |
| /var | Storage for all variable files and temporary files created by users, such as log files, the mail queue, the print spooler area, space for temporary storage of files downloaded from the Internet, or to keep an image of a CD before burning it. |

### 3.2 The file system in reality

## References

1. [General overview of the Linux file system](https://www.tldp.org/LDP/intro-linux/html/sect_03_01.html)
