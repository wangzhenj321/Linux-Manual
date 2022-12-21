## Description

`sed` is a stream editor. A stream editor is used to perform basic text transformations on an input stream (a file or input from a pipeline). While in some ways similar to an editor which permits scripted edits (such as `ed`), `sed` works by making only one pass over the input(s), and is consequently more efficient. But it is `sed`'s ability to filter text in a pipeline which particularly distinguishes it from other types of editors.

## Synopsis

- `sed [OPTION]... {script-only-if-no-other-script} [input-file]...`

## Options

- `-n, --quiet, --silent`

    suppress automatic printing of pattern space
    
    By default, `sed` prints out the pattern space at the end of each cycle through the script. These options disable this automatic printing, and `sed` only produces output when explicitly told to via the `p` command.

- `-e script, --expression=script`

    add the script to the commands to be executed

- `-f script-file, --file=script-file`

    add the contents of script-file to the commands to be executed

    > Without `-e` or `-f` options, `sed` uses the first non-option parameter as the SCRIPT, and the following non-option parameters as input files. If `-e` or `-f` options are used to specify a SCRIPT, all non-option parameters are taken as input files. Options `-e` and `-f` can be combined, and can appear multiple times (in which case the final effective SCRIPT will be concatenation of all the individual SCRIPTs).

- `-i[SUFFIX], --in-place[=SUFFIX]`

    edit files in place (makes backup if SUFFIX supplied)

## `sed` commands

`sed` commands follow this syntax: `[addr]X[options]`

- 'a TEXT'

    Append TEXT after a line (alternative syntax).

- 'c TEXT'

    Replace (change) lines with TEXT (alternative syntax).

- 'd'

    Delete the pattern space; immediately start next cycle.

- 'i TEXT'

    insert TEXT before a line (alternative syntax).

- 'p'

    Print the pattern space.

- 's/REGEXP/REPLACEMENT/[FLAGS]'

    (substitute) Match the regular-expression against the content of the pattern space. If found, replace matched string with REPLACEMENT.

- '{ CMD ; CMD ... }'

    Group several commands together.

## Examples

```
nl /etc/passwd | sed ‘2,5d’ （2到5行）
nl /etc/passwd | sed ‘2d’
nl /etc/passwd | sed ‘3,$d’ （3到最后一行）
nl /etc/passwd | sed ‘2~2d’ （2:2:$行）

sed ‘2a drink tea’ filename
sed ‘2i drink tea’ filename

sed ‘2,5c No 2-5 number’ filename

sed -n ‘5,7p’ filename

sed ‘/root/p’ filename （搜索filename中有root的行）
sed -n ‘/root/p’ filename

sed ‘/root/d’ filename

sed -n ‘/root/{s/bash/blueshell/;p}’ filename

sed ’s/要被取代的字串/新的字串/g’ filename （替代所有的匹配）

sed -e ‘3,$d’ -e ’s/bash/blueshell/‘ filename （先删除，再替代）

sed ’s/^/#/g’ filename 在每行前面加上#
^ 表示一行的开头，如：/^#/以#开头的匹配
$ 表示一行的结尾，如：/}$/以}结尾的匹配
\< 表示词首
\> 表示词尾
. 表示任何单个字符
*
[] 字符集合
```
