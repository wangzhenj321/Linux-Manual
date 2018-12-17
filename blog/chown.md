#### Description

Linux/Unix是多⼈多工作业系统, 所有的档案皆有拥有者。利用`chown`可以将档案的拥有者加以改变。一般来说,这个指令只有是由系统管理者(root)所使⽤, 一般使用者没有权限可以改变别人的档案拥有者, 也没有权限可以自己的档案拥有者改设为别人。只有系统管理者(root)才有这样的权限。

#### Synopsis

`chown [OPTION]... [OWNER][:[GROUP]] FILE...`

#### Examples

1. 将档案file1.txt的拥有者设为users群体的使⽤者jack

    `chown jack:users file1.txt`
