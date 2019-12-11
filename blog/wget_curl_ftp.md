# Part 1: `wget`

# Part 2: `curl`

# Part 3: `ftp`

## Synopsis

`ftp -v -d -i -n -g [hostname]`

## Options

- `-v` 显示远程服务器的所有响应信息

- `-d` 使用调试方式

- `-i` Turns off interactive prompting during multiple file transfers

- `-n` 限制ftp的自动登录，即：不使用.netrc文件

- `-g` 取消全局文件名

## Sub-Options

- `ascii` 使用ascii类型传输方式

- `binary` 使用二进制文件传输方式

- `bye` 退出ftp会话过程

- `cd`
 
- `delete` 删除远程主机文件

- `get` 将远程主机的文件传到本地硬盘

- `mget` 传输多个远程文件

- `mkdir`

- `open host[port]` 建立指定ftp服务器连接，可以指定连接端口

- `close` 中断与远程服务器的ftp会话

- `user user-name[password][account]` 向远程主机表明自己的身份

## Examples

```
set r_server = 'terras.gsi.go.jp'
set r_user   = 'wangzhen WzLTX1989321'
set r_dir    = /data/G_2.11/${yyyy}/${doy}
ftp -inv <<EOF  >& ftp.log
open $r_server
user $r_user
binary
cd $r_dir
get 0089${doy}0.${yy}o.gz
bye
EOF
```
