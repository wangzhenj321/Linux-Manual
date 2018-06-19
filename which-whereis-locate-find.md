- `which` 通过PATH环境变量到该路径内查找可执行文件和别名(alias)
- `whereis` 可以找到可执行命令和man page
- `locate` 数据库⾥查找,数据库⼤至每天更新⼀次
- `find` 实际搜寻硬盘查询文件名称

## `which`

#### Description

在PATH变量指定的路径中，搜索某个系统命令的位置，并且返回第一个搜索结果。也就是说，使用`which`命令，就可以看到某个系统命令是否存在，以及执行的到底是哪一个位置的命令。

## `whereis`

#### Description

whereis.c的源码，在缺省的情况下，会找当前和以下的路径

```
static char *bindirs[] = {
“/bin”,
“/usr/bin”,
“/sbin”,
“/usr/sbin”,
“/etc”,
“/usr/etc”,
“/lib”,
“/usr/lib”,
“/lib64”,
“/usr/lib64”,
“/usr/games”,
“/usr/games/bin”,
“/usr/games/lib”,
“/usr/emacs/etc”,
“/usr/lib/emacs/*/etc”,
“/usr/TeX/bin”,
“/usr/tex/bin”,
“/usr/interviews/bin/LINUX”,
“/usr/X11R6/bin”,
“/usr/X386/bin”,
“/usr/bin/X11”,
“/usr/X11/bin”,
“/usr/X11R5/bin”,
“/usr/local/bin”,
“/usr/local/sbin”,
“/usr/local/etc”,
“/usr/local/lib”,
“/usr/local/games”,
“/usr/local/games/bin”,
“/usr/local/emacs/etc”,
“/usr/local/TeX/bin”,
“/usr/local/tex/bin”,
“/usr/local/bin/X11”,
“/usr/contrib”,
“/usr/hosts”,
“/usr/include”,
“/usr/g++-include”,
“/usr/ucb”,
“/usr/old”,
“/usr/new”,
“/usr/local”,
“/usr/libexec”,
“/usr/share”,
“/opt/*/bin”,
0
};
static char *mandirs[] = {
“/usr/man/*”,
“/usr/share/man/*”,
“/usr/X386/man/*”,
“/usr/X11/man/*”,
“/usr/TeX/man/*”,
“/usr/interviews/man/mann”,
0
};
static char *srcdirs[]  = {
“/usr/src/*”,
“/usr/src/lib/libc/*”,
“/usr/src/lib/libc/net/*”,
“/usr/src/ucb/pascal”,
“/usr/src/ucb/pascal/utilities”,
“/usr/src/undoc”,
0
};
```

#### Options

- `-b` 只找⼆进制⽂件
- `-m` 只找在说明文件manual路径下的⽂件
- `-s` 只找source源⽂件
- `-u` 没有说明⽂档的文件

#### Examples

1. 将和passwd文件相关的文件都查找出来: `whereis passwd`

2. 只将⼆进制文件查找出来: `whereis -b passwd`

## `locate`

linux系统会将系统内的所有⽂件都记录在一个数据库文件中（/var/lib/locatedb）, 当使用`locate`时,会从数据库中查找数据,而不是像`find`命令那样,通过遍历硬盘来查找,效率自然会很高。但是该数据库文件并不是实时更新,默认情况下时一星期更新⼀次,因此,我们在用`locate`查找⽂文件时,有时会找到已经被删除的数据,或者刚建⽴文件,却⽆法查找到,原因就是因为数据库⽂件没有被更新。

## `find`

#### Description

当我们⽤`whereis`和`locate`无法查找到我们需要的文件时,可以使用`find`,但是`find`是在硬盘上遍历查找,因此⾮常消耗硬盘的资源,⽽且效率也⾮常低,因此建议大家优先使用`whereis`和`locate`。

#### Options

```
find 路径 参数
```

- 时间查找参数:
    - `-atime n` 将n*24小时内存取过的的文件列出来
    - `-ctime n` 将n*24小时内改变、新增的文件或者目录列出来
    - `-mtime n` 将n*24小时内修改过的文件或者目录列出来
    - `-newer file` 把比file还要新的文件列出来

- 名称查找参数:
    - `-gid n` 寻找群组ID为n的文件
    - `-group name` 寻找群组名称为name的文件
    - `-uid n` 寻找拥有者ID为n的文件
    - `-user name` 寻找⽤户者名称为name的文件
    - `-name file` 寻找文件名为file的⽂件(可以使用通配符)

- 文件大小查找参数: 

    `-size n[cwbkMG]` File uses n units of space. The following suffixes can be used:
    
        - `b` for 512-byte blocks (this is the default if no suffix is used)
        - `c` for bytes
        - `w` for two-byte words
        - `k` for Kilobytes (units of 1024 bytes)
        - `M` for Megabytes (units of 1048576 bytes)
        - `G` for Gigabytes (units of 1073741824 bytes)
    
    注意：默认单位是b，而它代表的是512字节，所以2表示1K，1M则是2048，如果不想自己转换，可以使用其他单位，如c、K、M等。
