## 从软件仓库中安装软件包

### apt-get update

在安装任何软件之前，我们最好是要更新本地软件包索引（package index）。本地软件包索引列出了软件仓库中所有可安装的软件包以及版本信息。
```
sudo apt-get update
```
![](img/apt-get/fig1.jpg?raw=true)

### apt-get install

apt-get install 是用来安装软件包的。你需要将软件包的名字添加到 apt-get install 之后．例如，你可以在Ubuntu系统上安装Chromium浏览器。
```
sudo apt-get install chromium-browser
```
有时候apt-get会询问你是否真的要安装软件包。如果你想自动回答yes，可以在安装命令中添加 `-y` 选项．
```
sudo apt-get install -y chromium-browser
```
![](img/apt-get/fig2.jpg?raw=true)
在上图中你可以看到，我的Ubuntu系统上已经安装好了Chromium浏览器．

在你用apt-get install命令安装软件包之前，你需要知道这个软件包在软件仓库中的名称．这看起来有点麻烦．当你熟悉之后，你会感到非常方便．尤其是当你SSH远程管理Linux服务器的时候．
> apt-get首先会从软件仓库中下载deb安装包，这些deb安装在/var/cache/apt/archives目录下．下载后，apt-get会自动安装软件包

## 一条命令安装多个软件包

apt-get install 可以一次性安装多个软件包，比如
```
sudo apt-get install wireshark nmap aircrack-ng
```
![](img/apt-get/fig3.jpg?raw=true)

### apt-get upgrade

apt-get upgrade命令用来升级系统上可以升级的软件包．
```
sudo apt-get upgrade
```
![](img/apt-get/fig4.jpg?raw=true)

### apt-get remove

这条命令用来删除系统上的软件包，比如，删除Firefox
```
sudo apt-get remove firefox
```
它不会删除软件包的配置文件．

### apt-get purge

这条命令可以用来删除软件包及其配置文件．
```
sudo apt-get purge firefox
```

### apt-get clean

当apt-get安装或升级软件包时，它会将deb安装包下载到文件系统的/var/cache/apt/archives目录下．软件包安装完成后，这些deb安装包基本上就没有什么用处了．apt-get clean命令可以帮你删除这些deb安装包．

你可以使用下面的命令查看/var/cache/apt/archives目录下deb安装包的大小．

![](img/apt-get/fig5.jpg?raw=true)

### apt-get autoclean

### apt-get autoremove

### 
![](img/apt-get/fig6.jpg?raw=true)
![](img/apt-get/fig7.jpg?raw=true)

## References

1. [Debian & Ubuntu最实用的apt-get命令详解](https://www.linuxdashen.com/apt-get%E8%BD%AF%E4%BB%B6%E5%8C%85%E7%AE%A1%E7%90%86%E5%99%A8%E7%9A%84%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MTI2OTQwNjBdfQ==
-->