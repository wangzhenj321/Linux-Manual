## Description

`updatedb` creates or updates a database used by `locate`. If the database already exists, its data is reused to avoid rereading directories that have not changed. `updatedb` is usually run daily by `cron` to update the default database.

## Exit Status

`updatedb` returns with exit status 0 on success, 1 on error.

## Files

- `/etc/updatedb.conf`

    A configuration file.

- `/var/lib/mlocate/mlocate.db`

    The database updated by default.
