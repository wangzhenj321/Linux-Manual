Ubuntu 16.04 发布时，一个引人注目的新特性便是 `apt` 命令的引入。其实早在 2014 年，`apt` 命令就已经发布了第一个稳定版，只是直到 2016 年的 Ubuntu 16.04 系统发布时才开始引人关注。

随着 `apt install package` 命令的使用频率和普遍性逐步超过 `apt-get install package`，越来越多的其它 Linux 发行版也开始遵循 Ubuntu 的脚步，开始鼓励用户使用 `apt` 而不是 `apt-get`。

那么，`apt-get` 与 `apt` 命令之间到底有什么区别呢？如果它们有类似的命令结构，为什么还需要新的 `apt` 命令呢？是否 `apt` 真的比 `apt-get` 更好？普通用户应该使用新的 apt 命令还是坚持旧有习惯继续使用 `apt-get` 呢？

系统极客将在本文中解释所有这些问题，我们希望本文结束时，你将会有一个更清晰的了解。

## apt与apt-get

在开始对比 `apt` 与 `apt-get` 命令的区别之前，我们先来看看这两个命令的背景，以及它们要试图达到的目的。

Debian 作为 Ubuntu、Linux Mint 和 elementary OS 等 Linux 操作系统的母板，其具有强健的「包管理」系统，它的每个组件和应用程序都内置在系统中安装的软件包中。Debian 使用一套名为 Advanced Packaging Tool（APT）的工具来管理这种包系统，不过请不要把它与 apt 命令混淆，它们之间是其实不是同一个东西。

在基于 Debian 的 Linux 发行版中，有各种工具可以与 APT 进行交互，以方便用户安装、删除和管理的软件包。apt-get 便是其中一款广受欢迎的命令行工具，另外一款较为流行的是 Aptitude 这一命令行与 GUI 兼顾的小工具。

如果你已阅读过我们的 apt-get 命令指南，可能已经遇到过许多类似的命令，如apt-cache、apt-config 等。如你所见，这些命令都比较低级又包含众多功能，普通的 Linux 用户也许永远都不会使用到。换种说法来说，就是最常用的 Linux 包管理命令都被分散在了 apt-get、apt-cache 和 apt-config 这三条命令当中。

apt 命令的引入就是为了解决命令过于分散的问题，它包括了 apt-get 命令出现以来使用最广泛的功能选项，以及 apt-cache 和 apt-config 命令中很少用到的功能。

在使用 apt 命令时，用户不必再由 apt-get 转到 apt-cache 或 apt-config，而且 apt 更加结构化，并为用户提供了管理软件包所需的必要选项。

### apt与apt-get之间的区别

### apt和apt-get命令之间的区别

### apt-get已弃用？

## 我应该使用apt还是apt-get？

## 小结
![](img/apt-and-apt-get/fig1.jpg?raw=true)
![](img/apt-and-apt-get/fig2.jpg?raw=true)

## References
1. [Linux中apt与apt-get命令的区别与解释](https://www.sysgeek.cn/apt-vs-apt-get/)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQyNjUwMzA4MF19
-->