## Description

All files accessible in a Unix system are arranged in one big tree, the file hierarchy, rooted at `/`. These files can be spread out over several devices.  The `mount` command serves to attach the filesystem found on some device to the big file tree. Conversely, the `umount` command will detach it again. The filesystem is used to control how data is stored on the device or provided in a virtual way by network or another services.

The standard form of the mount command is:

```
mount -t type device dir
```

This tells the kernel to attach the filesystem found on `device` (which is of type `type`) at the directory `dir`. The option `-t` type is optional. The `mount` command is usually able to detect a filesystem. The root permissions are necessary to mount a filesystem by default. See section "Non-superuser mounts" below for more details. The previous contents (if  any) and owner and mode of `dir` become invisible, and as long as this filesystem remains mounted, the pathname `dir` refers to the root of the filesystem on `device`.


## Synopsis

- `mount [-fnrsvw] [-t fstype] [-o options] device dir`

## Command-line options

- `-o, --options opts`

    Use the specified mount options. The `opts` argument is a comma-separated list. For example: `mount LABEL=mydisk -o noatime,nodev,nosuid`.

- `-t, --types fstype`

    The argument following the `-t` is used to indicate the filesystem type.

## Examples

1. `sudo mount -t ntfs -o rw,auto,user,fmask=0022,dmask=0000 /dev/whatever /mnt/whatever`
