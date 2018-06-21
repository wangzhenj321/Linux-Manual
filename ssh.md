## Part 1: ssh-keygen

#### 一台用户机器，一台服务器，一个key

1. 登陆用户机器，在用户根目录的.ssh文件夹下，执行`ssh-keygen -t [rsa|dsa]`（一般选择rsa）
2. 为了区分，设定输出文件的文件名，譬如：geosurf_own_server_rsa，将会生成geosurf_own_server_rsa和geosurf_own_server_rsa.pub
3. 将geosurf_own_server_rsa.pub文件复制到服务器的~/.ssh目录中，并执行`cat geosurf_own_server_rsa.pub >> ~/.ssh/authorized_keys`
4. 设置服务器中目录和文件权限，设置.ssh目录权限：`chmod 700 -R .ssh`，设置authorized_keys文件权限：`chmod 600 authorized_keys`

#### 多台用户机器，一台服务器，一个key

如果需要在新用户机器上登陆同一台服务器，只需要将旧用户机器上的密匙文件复制到新机器的~/.ssh/中（待测）。

#### 一台用户机器，多台服务器，多个key

在用户机器中新建config文件，配置如下：

```
# config own server in GEOSURF
Host geosurf
HostName 192.168.0.109
User wangzhen
IdentityFile ~/.ssh/geosurf_own_server_rsa
PreferredAuthentications publickey
```

- Host 别名（便于记忆，以后可以使用“ssh 别名”登录服务器）
- User 在远程主机上的用户名
- HostName 远程主机名
- Port 端口（远程主机的ssh监听的端口号，如果是22，可以省略）
- IdentityFile 密钥文件的路径（当不指定密钥文件的路径，ssh会默认使用id_rsa，接下来会介绍id_rsa如何生成）

## Part 2: ssh

通常利用ssh连接远程服务器，一般都要输入以下类似命令：`ssh username@hostname -p port`，但是如果有多个远程账号时，特别麻烦。
