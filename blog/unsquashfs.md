## Description

tool to uncompress squashfs filesystems

Squashfs is a highly compressed read-only filesystem for Linux. It uses zlib compression to compress both files, inodes and directories. Inodes in the system are very small and all blocks are packed to minimize data overhead. Block sizes greater than 4K are supported up to a maximum of 64K.

## Synopsis

`unsquashfs [OPTIONS] FILESYSTEM [directories or files to extract]`

## Options

- `-l, -ls`

    list filesystem, but don't unsquash.

- `-ll, -lls`

    list filesystem with file attributes (like `ls -l` output), but don't unsquash.

- `-nl, -nls`

    list filesystem with file attributes (like `ls -n` output), but don't unsquash.
