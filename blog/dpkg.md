## Description

`dpkg` is a tool to install, build, remove and manage Debian packages. The primary and more user-friendly front-end for `dpkg` is `aptitude`. `dpkg` itself is controlled entirely via command line parameters, which consist of exactly one action and zero or more options. The action-parameter tells `dpkg` what to do and options control the behavior of the action in some way.

## Synopsis

`dpkg [option...] action`

## Actions

- `-i, --install package-file...`

    Install the package. If `--recursive` or `-R` option is specified, package-file must refer to a directory instead.

- `-r, --remove package...|-a|--pending`

    Remove an installed package. This removes everything except conffiles and other data cleaned up by the `postrm` script, which may avoid having to  reconfigure the package if it is reinstalled later (conffiles are configuration files that are listed in the DEBIAN/conffiles control file). If there is no DEBIAN/conffiles control file nor DEBIAN/postrm script, this command is equivalent to calling `--purge`. If `-a` or `--pending` is given instead of a  package name, then all packages unpacked, but marked to be removed in file /var/lib/dpkg/status, are removed.

- `-P, --purge package...|-a|--pending`

    Purge an installed or already removed package. This removes everything, including conffiles, and anything else cleaned up from `postrm`. If `-a` or `--pending` is given instead of a package name, then all packages unpacked or removed, but marked to be purged in file /var/lib/dpkg/status, are purged.

## Options

- `-s, --status`

    Display package status details.
