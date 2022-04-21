# `useradd`

## Description

`useradd` is a low level utility for adding users. On Debian, administrators should usually use `adduser` instead.

When invoked without the `-D` option, the `useradd` command creates a new user account using the values specified on the command line plus the default values from the system. Depending on command line options, the `useradd` command will update system files and may also create the new user's home directory and copy initial files.

By default, a group will also be created for the new user (see `-g`, `-N`, `-U`, and `USERGROUPS_ENAB`).

## Synopsis

- `useradd [options] LOGIN`

## Options

- `-g, --gid GROUP`

    The group name or number of the user's initial login group. The group name must exist. A group number must refer to an already existing group.

    If not specified, the behavior of `useradd` will depend on the USERGROUPS_ENAB variable in `/etc/login.defs`. If this variable is set to yes (or `-U/--user-group` is specified on the command line), a group will be created for the user, with the same name as her loginname. If the variable is set to no (or `-N/--no-user-group` is specified on the command line), `useradd` will set the primary group of the new user to the value specified by the GROUP variable in `/etc/default/useradd`, or 100 by default.

- `-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]`

    A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same restrictions as the group given with the `-g` option. The default is for the user to belong only to the initial group.

# `groupadd`

## Description

The `groupadd` command creates a new group account using the values specified on the command line plus the default values from the system. The new group will be entered into the system files as needed.

## Synopsis

- `groupadd [options] group`

## Options

- `-g, --gid GID`

    The numerical value of the group's ID. This value must be unique, unless the `-o` option is used. The value must be non-negative. The default is to use the smallest ID value greater than or equal to GID_MIN and greater than every other group.

    See also the `-r` option and the GID_MAX description.
