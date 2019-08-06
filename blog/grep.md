#### Description

`grep`命令是一种强大的文本搜索工具，它能使用正则表达式搜索文本，并把匹配的行打印出来。

`grep`的工作方式是这样的，它在一个或多个文件中搜索字符串模版。如果模版包括空格，则必须用引号，模版后的所有字符串都被看作文件名。搜索的结果被送到标准输出，不影响原文件内容。

**注意：**

1. 字符串模版全部加上单引号，防止出错。
2. 对于特殊字符，加\转义。

#### Options

- `-i, --ignore-case`
    Ignore case distinctions in both the PATTERN and the input files.

- `--v, --invert-match`
    Invert the sense of matching, to select non-matching lines.

- `-c, --count`
    uppress  normal output; instead print a count of matching lines for each input file. With the `-v, --invert-match` option (see below), count non-matching lines.

- `-n, --line-number`
    Prefix each line of output with the 1-based line number within its input file.
