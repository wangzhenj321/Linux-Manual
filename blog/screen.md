## Description

`screen` is a full-screen window manager that multiplexes a physical terminal between several processes (typically interactive shells). Each virtual terminal provides the functions of a DEC VT100 terminal and, in addition, several control functions from the ISO 6429 (ECMA 48, ANSI X3.64) and ISO 2022 standards (e.g. insert/delete line and support for multiple character sets).

## Synopsis

- `screen -r [[pid.]tty[.host]]`

## Options

- `-r [pid.tty.host]`

    resumes a detached screen session. No other options (except combinations with `-d/-D`) may be specified, though an optional prefix of `[pid.]tty.host` may be needed to distinguish between multiple detached screen sessions.

## Default key bindings

- `C-a d, C-a C-d`

    Detach screen from this terminal.

## Examples

1. `screen /dev/ttyS1`
2. `screen -r 12961`
