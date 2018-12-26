#### Description

Print selected parts of lines from each **FILE** to standard output.

#### Options

- `-b` select only these bytes

- `-c` select only these characters

- `-d` use DELIM instead of TAB for field delimiter

- `-f` select only these fields; also print any line that contains no delimiter character, unless the -s option is specified

#### Examples


1. `who | cut -c 3-5,8`

2. `who | cut -c 5-`

3. `cat /etc/passwd | tail -n 5 | cut -d : -f 1`（`-d`: 以`:`为分隔符; `-f 1`: 分隔之后的第一列）

4. `cat /etc/passwd | tail -n 5 | cut -d : -f 1,3-5,7`
