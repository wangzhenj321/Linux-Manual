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
![](img/apt-get/fig3.jpg?raw=true)
![](img/apt-get/fig4.jpg?raw=true)
![](img/apt-get/fig5.jpg?raw=true)
![](img/apt-get/fig6.jpg?raw=true)
![](img/apt-get/fig7.jpg?raw=true)

## References

1. [Debian & Ubuntu最实用的apt-get命令详解](https://www.linuxdashen.com/apt-get%E8%BD%AF%E4%BB%B6%E5%8C%85%E7%AE%A1%E7%90%86%E5%99%A8%E7%9A%84%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTUwNjA2NTAwXX0=
-->