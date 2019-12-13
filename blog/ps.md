## Description

ps displays information about a selection of the active processes. If you want a repetitive update of the selection and the displayed information, use `top` instead.

## Options

- `-A` 显示所有进程

- `-u` 指定用户的所有进程

- `aux` 所有正在内存当中的进程

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
