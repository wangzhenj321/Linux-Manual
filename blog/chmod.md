#### Description

`chmod` changes the file mode bits of each given file according to mode, which can be either a symbolic representation of changes to make,  or an octal number representing the bit pattern for the new mode bits.

A combination of the letters `ugoa` controls which users' access to the file will be changed: the user who owns it (`u`), other users in the file's group (`g`), other users not in the file's group (`o`), or all users (`a`). If none of these are given, the effect is as if (`a`) were given, but bits that are set in the umask are not affected.

The operator `+` causes the selected file mode bits to be added to the existing file mode bits of each  file; `-` causes them to be removed; and `=` causes them to be added and causes unmentioned bits to be removed except that a directory's unmentioned set user and group ID bits are not affected.

#### Synopsis

`chmod [OPTION]... MODE[,MODE]... FILE...`

`chmod [OPTION]... OCTAL-MODE FILE...`

#### Options

- `-R, --recursive` change files and directories recursively

#### Examples

***包含字母和操作符表达式的文字设定法***

1. 将档案`file1.txt`设为所有⼈皆可读取

    `chmod ugo+r file1.txt`

2. 将档案`file1.txt`设为所有⼈皆可读取

    `chmod a+r file1.txt`

3. 将档案`file1.txt`与`file2.txt`设为该档案拥有者,与其所属同一个群体者可写入,但其他以外的⼈则不可写⼊

    `chmod ug+w,o-w file1.txt file2.txt`

4. 将`ex1.py`设定为只有该档案拥有者可以执⾏

    `chmod u+x ex1.py`

5. 将目前目录下的所有档案与⼦目录皆设为任何人可读取

    `chmod -R a+r *`

***包含数字的数字设定法***

`chmod abc file` 其中a,b,c各为一个数字,分别表示User、Group、及Other的权限。 r=4,w=2,x=1

6. `chmod a=rwx file`和`chmod 777 file`效果相同

7. `chmod ug=rwx,o=x file`和`chmod 771 file`效果相同
