**Table of contents**

**Part 1**

- [`/etc/passwd`文件结构](#etcpasswd文件结构)

- [`/etc/shadow`文件结构](#etcshadow文件结构)

- [`/etc/group`文件结构](#etcgroup文件结构)

- [初始群组(initial group)](#初始群组initial-group)

- [有效群组(effective group)](#有效群组effective-group)

**Part 2**

- [`id`](#id)

# Part 1

## `/etc/passwd`文件结构

这个文件的构造是这样的：每一行都代表一个账号，有几行就代表有几个账号在你的系统中！ 不过需要特别留意的是，里头很多账号本来就是系统正常运行所必须要的，我们可以简称他为系统账号， 例如 bin, daemon, adm, nobody 等等，这些账号请不要随意的杀掉他呢！ 

我们先来看一下每个 Linux 系统都会有的第一行，就是 root 这个系统管理员那一行好了， 你可以明显的看出来，每一行使用`:`分隔开，共有七个咚咚，分别是：

1. 账号名称

    就是账号啦！用来对应 UID 的。例如 root 的 UID 对应就是 0 (第三字段)；

2. 口令

    早期 Unix 系统的口令就是放在这字段上！但是因为这个文件的特性是所有的程序都能够读取，这样一来很容易造成口令数据被窃取， 因此后来就将这个字段的口令数据给他改放到`/etc/shadow`中了。所以这里你会看到一个`x`，呵呵！

3. UID

    这个就是使用者标识符啰！

4. GID

    这个与`/etc/group`有关！其实`/etc/group`的观念与`/etc/passwd`差不多，只是他是用来规范组名与 GID 的对应而已！

5. 用户信息说明栏

    这个字段基本上并没有什么重要用途，只是用来解释这个账号的意义而已！不过，如果您提供使用 finger 的功能时， 这个字段可以提供很多的信息呢！本章后面的 chfn 命令会来解释这里的说明。

6. 家目录

    这是用户的家目录，以上面为例， root 的家目录在 /root ，所以当 root 登陆之后，就会立刻跑到 /root 目录里头啦！呵呵！ 如果你有个账号的使用空间特别的大，你想要将该账号的家目录移动到其他的硬盘去该怎么作？ 没有错！可以在这个字段进行修改呦！默认的用户家目录在 /home/yourIDname

7. Shell

    当用户登陆系统后就会取得一个 Shell 来与系统的核心沟通以进行用户的操作任务。那为何默认 shell 会使用 bash 呢？就是在这个字段指定的啰！ 这里比较需要注意的是，有一个 shell 可以用来替代成让账号无法取得 shell 环境的登陆动作！那就是 /sbin/nologin 这个东西！这也可以用来制作纯 pop 邮件账号者的数据呢！

## `/etc/shadow`文件结构

我们知道很多程序的运行都与权限有关，而权限与 UID/GID 有关！因此各程序当然需要读取 /etc/passwd 来了解不同账号的权限。 因此 /etc/passwd 的权限需配置为 -rw-r--r-- 这样的情况， 虽然早期的口令也有加密过，但却放置到 /etc/passwd 的第二个字段上！这样一来很容易被有心人士所窃取的， 加密过的口令也能够透过暴力破解法去 try and error (试误) 找出来！

因为这样的关系，所以后来发展出将口令移动到 /etc/shadow 这个文件分隔开来的技术， 而且还加入很多的口令限制参数在 /etc/shadow 里头呢！在这里，我们先来了解一下这个文件的构造吧！

基本上， shadow 同样以`:`作为分隔符，如果数一数，会发现共有九个字段啊，这九个字段的用途是这样的：

1. 账号名称

    由于口令也需要与账号对应啊～因此，这个文件的第一栏就是账号，必须要与 /etc/passwd 相同才行！

2. 口令

3. ...

## `/etc/group`文件结构

这个文件就是在记录 GID 与组名的对应。

这个文件每一行代表一个群组，也是以冒号`:`作为字段的分隔符，共分为四栏，每一字段的意义是：

1. 组名

2. 群组口令

    通常不需要配置，这个配置通常是给群组管理员使用的，目前很少有这个机会配置群组管理员啦！ 同样的，口令已经移动到`/etc/gshadow`去，因此这个字段只会存在一个`x`而已；

3. GID

    就是群组的 ID 啊。我们`/etc/passwd`第四个字段使用的 GID 对应的群组名，就是由这里对应出来的！

4. 此群组支持的账号名称

    我们知道一个账号可以加入多个群组，那某个账号想要加入此群组时，将该账号填入这个字段即可。 举例来说，如果我想要让 dmtsai 也加入 root 这个群组，那么在第一行的最后面加上`,dmtsai`，注意不要有空格， 使成为`root:x:0:root,dmtsai`就可以啰～

#### 初始群组(initial group)

还记得每个使用者在他的`/etc/passwd`里面的第四栏有所谓的 GID 吧？那个 GID 就是所谓的『初始群组 (initial group) 』！也就是说，当用户一登陆系统，立刻就拥有这个群组的相关权限的意思。 举例来说，我们上面提到 dmtsai 这个使用者的`/etc/passwd`与`/etc/group`还有`/etc/gshadow`相关的内容如下：

![](../img/id/effective-group-initial-group.png?raw=true)

仔细看到上面这个表格，在`/etc/passwd`里面，dmtsai 这个使用者所属的群组为 GID=504 ，搜寻一下`/etc/group`得到 504 是那个名为 dmtsai 的群组啦！这就是 initial group。**因为是初始群组， 使用者一登陆就会主动取得，不需要在 /etc/group 的第四个字段写入该账号的！**

但是非 initial group 的其他群组可就不同了。举上面这个例子来说，我将 dmtsai 加入 users 这个群组当中，由于 users 这个群组并非是 dmtsai 的初始群组，因此， 我必须要在`/etc/group`这个文件中，找到 users 那一行，并且将 dmtsai 这个账号加入第四栏， 这样 dmtsai 才能够加入 users 这个群组啊。

那么在这个例子当中，因为我的 dmtsai 账号同时支持 dmtsai 与 users 这两个群组， 因此，在读取/写入/运行文件时，针对群组部分，只要是 users 与 dmtsai 这两个群组拥有的功能， 我 dmtsai 这个使用者都能够拥有喔！这样瞭呼？不过，这是针对已经存在的文件而言， 如果今天我要创建一个新的文件或者是新的目录，请问一下，新文件的群组是 dmtsai 还是 users ？呵呵！这就得要检查一下当时的有效群组了 (effective group)。

## 有效群组(effective group)

如果我以 dmtsai 这个使用者的身份登陆后，该如何知道我所有支持的群组呢？ 很简单啊，直接输入 groups 就可以了！注意喔，是 groups 有加 s 呢！结果像这样：

![](../img/id/groups.png?raw=true)

在这个输出的信息中，可知道 dmtsai 这个用户同时属于 dmtsai 及 users 这个两个群组，而且， 第一个输出的群组即为有效群组 (effective group) 了。 也就是说，我的有效群组为 dmtsai 啦～此时，如果我以 touch 去创建一个新档，例如： 『 touch test 』，那么这个文件的拥有者为 dmtsai ，而且群组也是 dmtsai 的啦。

# Part 2

## `id`

### Description

Print user and group information for the specified USER, or (when USER omitted) for the current user.

### Options

- `-u, --user` print only the effective user ID

- `-g, --group` print only the effective group ID

- `-G, --groups` print all group IDs

- `-n, --name` print a name instead of a number, for -ugG
