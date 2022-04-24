## Description

`ifconfig` is used to configure the kernel-resident network interfaces. It is used at boot time to set up interfaces as necessary. After that, it is usually only needed when debugging or when system tuning is needed.

1. If no arguments are given, `ifconfig` displays the status of the currently active interfaces.
2. If a single interface argument is given, it displays the status of the given interface only.
3. If a single `-a` argument is given, it displays the status of all interfaces, even those that are down.
4. Otherwise, it configures an interface.

## Synopsis

- `ifconfig [-a] [-s] [interface]`

## Options

- `-a`

    display all interfaces which are currently available, even if down

- `-s`

    display a short list (like `netstat -i`)

- `interface`

    The name of the interface. This is usually a driver name followed by a unit number, for example **eth0** for the first Ethernet interface. 
