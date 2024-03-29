## Description

`man` is the system's manual pager.

Each `page` argument given to `man` is normally the name of a program, utility or function. The manual page associated with each of these arguments is then found and displayed.

A `section`, if provided, will direct `man` to look only in that `section` of the manual. The default action is to search in all of the available sections following a pre-defined order, and to show only the first page found, even if page exists in several sections.

The table below shows the section numbers of the manual followed by the types of pages they contain.

| Section number | Type of page |
| --- | --- |
| 1 | Executable programs or shell commands |
| 2 | System calls (functions provided by the kernel) |
| 3 | Library calls (functions within program libraries) |
| 4 | Special files (usually found in /dev) |
| 5 | File formats and conventions eg /etc/passwd |
| 6 | Games |
| 7 | Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7) |
| 8 | System administration commands (usually only for root) |
| 9 | Kernel routines [Non standard] |

## Synopsis

- `man [[section] page ...]`

- `man -k regexp ...`

## Options

- `-k, --apropos`

    Equivalent to `apropos`. Search the short manual page descriptions for keywords and display any matches.
