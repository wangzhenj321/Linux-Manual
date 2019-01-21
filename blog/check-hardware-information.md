**Table of Contents**

[List of commands](#list-of-commands)

- [`lscpu`](#lscpu)

- [`lshw`](#lshw)

- [`hwinfo`](#hwinfo)

- [`lspci`](#lspci)

- [`lsscsi`](#lsscsi)

- [`lsusb`](#lsusb)

- [`inxi`](#inxi)

- [`lsblk`](#lsblk)

- [`df`](#df)

- [`Pydf`](#Pydf)

- [`fdisk`](#fdisk)

- [`mount`](#mount)

- [`free`](#free)

- [`dmidecode`](#dmidecode)

- [`/proc` files](#proc-files)

- [`hdparm`](#hdparm)

[References](#references)

## List of commands

### `lscpu`

`lscpu` gathers CPU architecture information from **sysfs** and `/proc/cpuinfo`. The command output can be optimized for parsing or for easy readability by humans. The information includes, for example, the number of CPUs, threads, cores, sockets, and Non-Uniform Memory Access (NUMA) nodes. There is also information about the CPU caches and cache sharing, family, model, bogoMIPS, byte order, and stepping.

---

The **sysfs** filesystem is a pseudo-filesystem which provides an interface to kernel data structures. (More precisely, the files and directories in **sysfs** provide a view of the *kobject* structures defined internally within the kernel.) The files under **sysfs** provide information about devices, kernel modules, filesystems, and other kernel components. The **sysfs** filesystem is commonly mounted at `/sys`.

---

### `lshw`

`lshw` is a small tool to extract detailed information on the hardware configuration of the machine. It can report exact memory configuration, firmware version, mainboard configuration, CPU version and speed, cache configuration, bus speed, etc. on DMI-capable x86 or IA-64 systems and on some PowerPC machines (PowerMac G4 is known to work).

### `hwinfo`

`hwinfo` is used to probe for the hardware present in the system. It can be used to generate a system overview log which can be later used for support.

### `lspci`

`lspci` is a utility for displaying information about PCI buses in the system and devices connected to them. By default, it shows a brief list of devices. Use the options described below to request either a more verbose output or output intended for parsing by other programs.

---

外部链接（Peripheral Component Interconnect）标准，或称个人计算机接口（Personal Computer Interface），实际应用中简称为**PCI**，是一种连接计算机主板和外部设备的总线标准。一般PCI设备可分为以下两种形式：

- 直接内置于主板上的集成电路，在PCI规范中称作“嵌入设备”（planar device）

- 安装在插槽上的扩展界面卡

PCI规范规定了该总线的物理尺寸（包括线宽）、电气特性、总线时序和协议。该规范可从美国PCI-SIG协会购得。常见的PCI卡包括网卡、声卡、调制解调器、电视卡和硬盘控制器等，另外还有USB和串列端口等端口。原本显卡通常也是PCI设备，但很快其频宽已不足以支持显卡的性能。

---

### `lsscsi`

Uses information in sysfs (Linux kernel series 2.6 and later) to list SCSI devices (or hosts) currently attached to the system. Options can be used to control the amount and form of  information provided for each device.

---

小型计算机系统接口（SCSI，Small Computer System Interface）是一种用于计算机及其周边设备之间（硬盘、软驱、光驱、打印机、扫描仪等）系统级接口的独立处理器标准。SCSI标准定义命令、通信协议以及实体的电气特性（换成OSI的说法，就是占据物理层、链接层、套接层、应用层），最大部分的应用是在存储设备上（例如硬盘、磁带机），除外，SCSI可以连接的设备包括有扫描仪、光学设备（像CD、DVD）、打印机等等，SCSI命令中有条列出支持的设备SCSI周边设备。理论上，SCSI不可能连接所有的设备，所以有“1Fh - unknown or no device type”这个参数存在。

---

### `lsusb`

`lsusb` is a utility for displaying information about USB buses in the system and the devices connected to them.

### `inxi`

### `lsblk`

`lsblk` lists information about all available or the specified block devices. The lsblk command reads the **sysfs** filesystem and **udev db** to gather information. The command prints all block devices (except RAM disks) in a tree-like format by default.

### `df`
`free`
`df` displays the amount of disk space available on the file system containing each file name argument. If no file name is given, the space available on all currently mounted file systems is shown. Disk space is shown in 1K blocks by default, unless the environment variable POSIXLY_CORRECT is set, in which case 512-byte blocks are used.

### `Pydf`


### `fdisk`

`fdisk` is a dialog-driven program for creation and manipulation of partition tables. It understands GPT, MBR, Sun, SGI and BSD partition tables.

### `mount`

All files accessible in a Unix system are arranged in one big tree, the file hierarchy, rooted at **/**.  These files can be spread out over several devices. The `mount` command serves to attach the filesystem found on some device to the big file tree.

### `free`

`free` displays the total amount of free and used physical and swap memory in the system, as well as the buffers and caches used by the kernel. The information is gathered by parsing **/proc/meminfo**.

### `dmidecode`

`dmidecode` is a tool for dumping a computer's DMI (some say SMBIOS) table contents in a human-readable format. This table contains a description of the system's hardware components, as well as other useful pieces of information such as serial numbers and BIOS revision.

### `/proc` files

The **proc** filesystem is a pseudo-filesystem which provides an interface to kernel data structures. It is commonly mounted at **/proc**. Most of it is read-only, but some files allow kernel variables to be changed.

### `hdparm`

`hdparm` provides a command line interface to various kernel interfaces supported by the Linux SATA/PATA/SAS "libata" subsystem and the older IDE driver subsystem.

## References

1. [16 commands to check hardware information on Linux](https://www.binarytides.com/linux-commands-hardware-info/)
2. [Get hardware information on Linux with lshw command](https://www.binarytides.com/linux-lshw-command/)
3. [Check hardware information on Linux with hwinfo command](https://www.binarytides.com/linux-hwinfo-command/)
