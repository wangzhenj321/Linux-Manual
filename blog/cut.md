## Description

Print selected parts of lines from each **FILE** to standard output.

## Synopsis

- `cut OPTION... [FILE]...`

## Options

- `-b, --bytes=LIST`

    select only these bytes

- `-c, --characters=LIST`

    select only these characters

- `-d, --delimiter=DELIM`

    use DELIM instead of TAB for field delimiter

- `-f, --fields=LIST`

    select only these fields; **also print any line that contains no delimiter character, unless the `-s` option is specified**

- `--complement`

    complement the set of selected bytes, characters or fields

- `-s`

    do not print lines not containing delimiters

- `--output-delimiter=STRING`

    use **STRING** as the output delimiter the default is to use the input delimiter

---

Use one, and only one of `-b`, `-c` or `-f`.  Each **LIST** is made up of one range, or many ranges separated by commas.  **Selected input is written in the same order that it is read, and is written exactly once.** Each range is one of:

- `N` N'th byte, character or field, counted from 1

- `N-` from N'th byte, character or field, to end of line

- `N-M` from N'th to M'th (included) byte, character or field

- `-M` from first to M'th (included) byte, character or field

---

## Examples


1. `who | cut -c 3-5,8`

2. `who | cut -c 5-`

3. `cat /etc/passwd | tail -n 5 | cut -d : -f 1`（`-d`: 以`:`为分隔符; `-f 1`: 分隔之后的第一列）

4. `cat /etc/passwd | tail -n 5 | cut -d : -f 1,3-5,7`
