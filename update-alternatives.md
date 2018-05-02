## DESCRIPTION

update-alternatives creates, removes, maintains and displays information about the symbolic links comprising the Debian alternatives system.

It is possible for several programs fulfilling the same or similar functions to be installed on a single system at the same time.  For example, many systems have several text editors installed at once.  This gives choice to the users of a system, allowing each to use a different editor, if desired, but makes  it difficult for a program to make a good choice for an editor to invoke if the user has not specified a particular preference.

Debian's  alternatives  system aims to solve this problem.  A generic name in the filesystem is shared by all files providing interchangeable functionality. The alternatives system and the system administrator together determine which actual file is referenced by this generic name.  For example, if the text editors  ed(1)  and  nvi(1)  are  both installed on the system, the alternatives system will cause the generic name /usr/bin/editor to refer to /usr/bin/nvi by default. The system administrator can override this and cause it to refer to /usr/bin/ed instead, and the alternatives system will not  alter  this  setting until explicitly requested to do so.

## COMMANDS

**`--install link name path priority [--slave link name path]...`**

Add a group of alternatives to the system. ***link*** is the generic name for the master link, ***name*** is the name of its symlink in the alternatives directory, and ***path*** is the alternative being introduced for the master link. The arguments after `--slave` are the generic name, symlink name in the alternatives directory and the alternative path for a slave link. Zero or more `--slave` options, each followed by three arguments, may be specified. Note that the master alternative must exist or the call will fail. However if a slave alternative doesn't exist, the corresponding slave alternative link will simply not be installed (a warning will still be displayed). If some real file is installed where an alternative link has to be installed, it is kept unless `--force` is used.

If  the alternative name specified exists already in the alternatives system's records, the information supplied will be added as a new set of alternatives for the group. Otherwise, a new group, set to automatic mode, will be added with this information. If the group is in automatic mode, and the  newly added alternatives' priority is higher than any other installed alternatives for this group, the symlinks will be updated to point to the newly added alternatives.

#### `--set name path`

Set the program ***path*** as alternative for ***name***. This is equivalent to `--config` but is non-interactive and thus scriptable.

```
--remove name path
```

Remove an alternative and all of its associated slave links. ***name*** is a name in the alternatives directory, and ***path*** is an absolute filename to which ***name*** could  be linked. If ***name*** is indeed linked to ***path***, ***name*** will be updated to point to another appropriate alternative (and the group is put back in automatic mode), or removed if there is no such alternative left.  Associated slave links will be updated or removed, correspondingly. If the link is not currently pointing to ***path***, no links are changed; only the information about the alternative is removed.

```
--remove-all name
```

Remove all alternatives and all of their associated slave links. ***name*** is a name in the alternatives directory.

```
--display name
```

Display information about the link group. Information displayed includes the group's mode (auto or manual), the master and slave links, which alternative the master link currently points to, what other alternatives are available (and their corresponding slave alternatives), and the highest priority alternative currently installed.

```
--config name
```

Show available alternatives for a link group and allow the user to interactively select which one to use. The link group is updated.
