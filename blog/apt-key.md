## Description

`apt-key` is used to manage the list of keys used by apt to authenticate packages. Packages which have been authenticated using these keys will be considered trusted.

## Synopsis

`apt-key {add filename}`

## Options

- `add filename`

    Add a new key to the list of trusted keys. The key is read from the filename given with the parameter `filename` or if the filename is `-` from standard input.
