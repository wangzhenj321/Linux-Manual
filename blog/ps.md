## Description

ps displays information about a selection of the active processes. If you want a repetitive update of the selection and the displayed information, use `top` instead.

## Options

- `-A`
    
    Select all processes. Identical to `-e`.

- `-e`

    Select all processes. Identical to `-A`.

- `-u userlist`

    Select by effective user ID (EUID) or name. This selects the processes whose effective user name or ID is in `userlist`.

- `-f`

    Do full-format listing. This option can be combined with many other UNIX-style options to add additional columns. It also causes the command arguments to be printed. When used with `-L`, the NLWP (number of threads) and LWP (thread ID) columns will be added.

- `-l`

    Long format. The `-y` option is often useful with this.

## Process state codes

Here are the different values that the `s`, `stat` and `state` output specifiers (header "STAT" or "S") will display to describe the state of a process:

- `D` uninterruptible sleep (usually IO)
- `R` running or runnable (on run queue)
- `S` interruptible sleep (waiting for an event to complete)
- `T` stopped by job control signal
- `t` stopped by debugger during the tracing
- `W` paging (not valid since the 2.6.xx kernel)
- `X` dead (should never be seen)
- `Z` defunct ("zombie") process, terminated but not reaped by its parent
