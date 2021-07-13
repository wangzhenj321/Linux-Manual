## Description

Run a program in a modified environment.

Set each **NAME** to **VALUE** in the environment and run **COMMAND**. If no **COMMAND**, print the resulting environment.

## Synopsis

`env [OPTION]... [-] [NAME=VALUE]... [COMMAND [ARG]...]`

## Options

- `-i, --ignore-environment`

    start with an empty environment

- `-u, --unset=NAME`

    remove variable from the environment
