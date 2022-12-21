## Description

`sed` is a stream editor. A stream editor is used to perform basic text transformations on an input stream (a file or input from a pipeline). While in some ways similar to an editor which permits scripted edits (such as `ed`), `sed` works by making only one pass over the input(s), and is consequently more efficient. But it is `sed`'s ability to filter text in a pipeline which particularly distinguishes it from other types of editors.

## Synopsis

- `sed [OPTION]... {script-only-if-no-other-script} [input-file]...`

## Options

- `-n, --quiet, --silent`

    suppress automatic printing of pattern space

- `-e script, --expression=script`

    add the script to the commands to be executed

- `-i[SUFFIX], --in-place[=SUFFIX]`

    edit files in place (makes backup if SUFFIX supplied)

- `-n` 使用安静模式。在一般sed的用法中，所有来自STDIN的数据一般都会被列出到终端上。但如果加上-n参数后，则只有经过sed特殊处理的那一行才会被列出来。
- `-e` 直接在命令行模式上进行sed的动作编辑
- `-i` 直接修改读取的文件内容，而不是输出到终端

- a 新增，a的后面可以接字串，而这些字串会在新的一行出现（目前的下一行）
- c 取代，c的后面可以接字串，这些字串可以取代n1，n2之间的行
- d 删除
- i 插入，i的后面可以接字串，而这些字串会在新的一行出现（目前的上一行）
- p 列印，将某个选择的数据列出（通常与-n一起使用）
- s 取代

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
