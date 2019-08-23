#### Description

Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships

#### Synopsis

#### Output

- **Active Internet connections (TCP, UDP, raw)**

    | Output column | Description |
    | --- | --- |
    | Proto | The protocol (tcp, udp, raw) used by the socket. |
    | Recv-Q | The count of bytes not copied by the user program connected to this socket. |
    | Send-Q | The count of bytes not acknowledged by the remote host. |
    | Local Address | Address and port number of the local end of the socket. |
    | Foreign Address | Address and port number of the remote end of the socket. |
    | State | The state of the socket. |

- **Active UNIX domain Sockets**

    | Output column | Description |
    | --- | --- |
    | Proto | The protocol (usually unix) used by the socket. |
    | RefCnt | The reference count (i.e. attached processes via this socket). |
    | Flags | The flags displayed is SO_ACCEPTON (displayed as ACC), SO_WAITDATA (W) or SO_NOSPACE (N). SO_ACCECPTON is used on unconnected sockets if their corresponding processes are waiting for a connect request. The other flags are not of normal interest. |
    | Type | types of socket access |
    | State | The state of the socket. |
    | PID/Program name | Process ID (PID) and process name of the process that has the socket open. |
    | Path | This is the path name as which the corresponding processes attached to the socket. |

#### Options

- `-r`

    Display the kernel routing tables.

- `-s`

    Display summary statistics for each protocol.

- `-n`

    Show numerical addresses instead of trying to determine symbolic host, port or user names.

- `-c`

    This will cause netstat to print the selected information every second continuously.

- `-e`

    Display additional information.

- `-p`

    Show the PID and name of the program to which each socket belongs.

- `-l`

    Show only listening sockets.  (These are omitted by default.)

- `-a`

    Show both listening and non-listening sockets.

- `-t`

    Show only tcp related items.

- `-u`

    Show only udp related items.

- `-x`

    Show only unix related items.
