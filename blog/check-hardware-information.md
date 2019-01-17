## List of commands

### `lscpu`

`lscpu` gathers CPU architecture information from **sysfs** and `/proc/cpuinfo`. The command output can be optimized for parsing or for easy readability by humans. The information includes, for example, the number of CPUs, threads, cores, sockets, and Non-Uniform Memory Access (NUMA) nodes. There is also information about the CPU caches and cache sharing, family, model, bogoMIPS, byte order, and stepping.

> The **sysfs** filesystem is a pseudo-filesystem which provides an interface to kernel data structures. (More precisely, the files and directories in **sysfs** provide a view of the *kobject* structures defined internally within the kernel.) The files under **sysfs** provide information about devices, kernel modules, filesystems, and other kernel components. The **sysfs** filesystem is commonly mounted at `/sys`.

### `lshw`

`lshw` is a small tool to extract detailed information on the hardware configuration of the machine. It can report exact memory configuration, firmware version, mainboard configuration, CPU version and speed, cache configuration, bus speed, etc. on DMI-capable x86 or IA-64 systems and on some PowerPC machines (PowerMac G4 is known to work).

### `hwinfo`

`hwinfo` is used to probe for the hardware present in the system. It can be used to generate a system overview log which can be later used for support.

- `lspci`
- `lsscsi`
- `lsusb`
- `inxi`
- `lsblk`
- `df`
- `Pydf`
- `fdisk`
- `mount`
- `free`
- `dmidecode`
- `/proc` files
- `hdparm`

## References

1. [16 commands to check hardware information on Linux](https://www.binarytides.com/linux-commands-hardware-info/)
2. [Get hardware information on Linux with lshw command](https://www.binarytides.com/linux-lshw-command/)
3. [Check hardware information on Linux with hwinfo command](https://www.binarytides.com/linux-hwinfo-command/)
