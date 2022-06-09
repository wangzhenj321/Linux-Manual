## Description

`dpkg` is a tool to install, build, remove and manage Debian packages. The primary and more user-friendly front-end for `dpkg` is `aptitude`. `dpkg` itself is controlled entirely via command line parameters, which consist of exactly one action and zero or more options. The action-parameter tells `dpkg` what to do and options control the behavior of the action in some way.

`dpkg` can also be used as a front-end to `dpkg-deb` and `dpkg-query`.

## Synopsis

`dpkg [option...] action`

## Options

- `-s, --status`

    Display package status details.
