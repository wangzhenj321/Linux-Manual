#### Description

concatenate files and print on the standard output

#### Options

- `-c` 以字符为单位进行分割

- `-d` 自定义分隔符，默认为制表符（Tab）

- `-f` 与`-d`一起使用，指定显示哪个区域

#### Examples


1. `who | cut -c 3-5,8`

2. `who | cut -c 5-`

3. `cat /etc/passwd | tail -n 5 | cut -d : -f 1`（`-d`: 以`:`为分隔符; `-f 1`: 分隔之后的第一列）

4. `cat /etc/passwd | tail -n 5 | cut -d : -f 1,3-5,7`
