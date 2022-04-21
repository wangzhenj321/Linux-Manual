# `usermod`

## Description

The `usermod` command modifies the system account files to reflect the changes that are specified on the command line.

## Synopsis

- `usermod [options] LOGIN`

## Options

- `-a, --append`

    Add the user to the supplementary group(s). Use only with the `-G` option.

- `-g, --gid GROUP`

    The group name or number of the user's new initial login group. The group must exist.

    Any file from the user's home directory owned by the previous primary group of the user will be owned by this new group.

    The group ownership of files outside of the user's home directory must be fixed manually.

- `-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]`

    A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same restrictions as the group given with the `-g` option.

    If the user is currently a member of a group which is not listed, the user will be removed from the group. This behaviour can be changed via the `-a` option, which appends the user to the current supplementary group list.

- `-u, --uid UID`

    The new numerical value of the user's ID.

    This value must be unique, unless the `-o` option is used. The value must be non-negative.

    The user's mailbox, and any files which the user owns and which are located in the user's home directory will have the file user ID changed automatically.

    The ownership of files outside of the user's home directory must be fixed manually.

    No checks will be performed with regard to the UID_MIN, UID_MAX, SYS_UID_MIN, or SYS_UID_MAX from `/etc/login.defs`.

# `groupmod`

## Description

The `groupmod` command modifies the definition of the specified `GROUP` by modifying the appropriate entry in the group database.

## Synopsis

- `groupmod [options] GROUP`

## Options

- `-g, --gid GID`

    The group ID of the given `GROUP` will be changed to GID.

    The value of GID must be a non-negative decimal integer. This value must be unique, unless the `-o` option is used.

    Users who use the group as primary group will be updated to keep the group as their primary group.

    Any files that have the old group ID and must continue to belong to GROUP, must have their group ID changed manually.

    No checks will be performed with regard to the GID_MIN, GID_MAX, SYS_GID_MIN, or SYS_GID_MAX from `/etc/login.defs`.
