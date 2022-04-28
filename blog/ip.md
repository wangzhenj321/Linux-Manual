## Description

show / manipulate routing, network devices, interfaces and tunnels

## Synopsis

- `ip [ OPTIONS ] OBJECT { COMMAND | help }`

    - `OBJECT`
    
        `OBJECT` := { link | address | addrlabel | route | rule | neigh | ntable | tunnel | tuntap | maddress | mroute | mrule | monitor | xfrm | netns | l2tp | tcp_metrics | token | macsec }
    
    - `COMMAND`
    
        Specifies the action to perform on the object. The set of possible actions depends on the object type. As a rule, it is possible to `add`, `delete` and `show` (or `list` ) objects, but some objects do not allow all of these operations or have some additional commands. The `help` command is available for all objects. It prints out a list of available commands and argument syntax conventions. If no command is given, some default command is assumed. Usually it is `list` or, if the objects of this class cannot be listed, `help`.

## Examples

1. `ip addr`

    Shows addresses assigned to all network interfaces.

2. `ip route`

    Show table routes.

3. `ip address add 192.168.1.200/255.255.255.0 dev eth0`

    Assign the IP address 192.168.1.200/255.255.255.0 to device eth0.
