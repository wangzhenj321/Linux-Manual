## Description

`fuser` displays the PIDs of processes using the specified files or file systems.

`fuser` outputs only the PIDs to stdout, everything else is sent to stderr.

## Synopsis

- `fuser [-fuv] [-a|-s] [-4|-6] [-c|-m|-n space] [ -k [-i] [-M] [-w] [-SIGNAL] ] name ...`

## Options

- `-k, --kill`

    Kill processes accessing the file.
