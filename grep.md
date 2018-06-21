#### Description

`grep`命令是一种强大的文本搜索工具，它能使用正则表达式搜索文本，并把匹配的行打印出来。

`grep`的工作方式是这样的，它在一个或多个文件中搜索字符串模版。如果模版包括空格，则必须用引号，模版后的所有字符串都被看作文件名。搜索的结果被送到标准输出，不影响原文件内容。

**注意：**

1. 字符串模版全部加上单引号，防止出错。
2. 对于特殊字符，加\转义。

#### Options

- `-i` ignore case distinctions 忽略字符大小写的差别
- `-v` select non-matching lines 显示不包含匹配文本的所有行
- `-c` print only a count of matching lines per FILE 计算符合样式的行数
- `-n` print line number with output lines 在显示符合样式的那一行之前，标示出该行的行号
- `--color` Mark up the matching text with the expression stored in GREP_COLOR environment variable.
