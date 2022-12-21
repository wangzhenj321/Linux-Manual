## Description

Filter **adjacent matching lines** from INPUT (or standard input), writing to OUTPUT (or standard output). **With no options, matching lines are merged to the first occurrence.**

> **Note:** `uniq` does not detect repeated lines unless they are adjacent. You may want to sort the input first, or use `sort -u` without `uniq`.

## Options

- `-c, --count`

    prefix lines by the number of occurrences

- `-d, --repeated`

    only print duplicate lines, one for each group

- `-f, --skip-fields=N`

    avoid comparing the first N fields

- `-i, --ignore-case`

    ignore differences in case when comparing

- `-s, --skip-chars=N`

    avoid comparing the first N characters

- `-u, --unique`

    only print unique lines
