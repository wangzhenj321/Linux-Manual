#### Description

Determine file type. `file` tests each argument in an attempt to classify it. There are three sets of tests, performed in this order: **filesystem tests**, **magic tests**, and **language tests**. The first test that succeeds causes the file type to be printed.

#### Options

- `-b`

    Do not prepend filenames to output lines (brief mode).

- `-i`

    Causes the file command to output mime type strings rather than the more traditional human readable ones. Thus it may say ‘text/plain;charset=us-ascii’ rather than “ASCII text”.
