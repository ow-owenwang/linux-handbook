# scp / sftp / rz / sz

## 常用场景
- 文件上传下载
- 远程文件传输
- 安全文件传输

## scp 命令

### 功能
scp（secure copy）是基于 SSH 协议的安全文件传输命令。

### 下载文件
```bash
# 把远程主机 192.168.0.101 的 /var/www/test.txt 文件下载到本地主机用户家目录
scp root@192.168.0.101:/var/www/test.txt ~
```

### 上传文件
```bash
# 上传本地主机 /var/www/test.php 文件到远程主机 192.168.0.101 的 /var/www/ 目录
scp /var/www/test.php root@192.168.0.101:/var/www/
```

### 传输目录
下载和上传目录需要加 `-r` 参数。

```bash
# 下载目录
scp -r root@192.168.0.101:/var/www/dir ~

# 上传目录
scp -r /local/dir root@192.168.0.101:/var/www/
```

### 常用参数
- `-r`: 递归复制目录
- `-P`: 指定端口（注意是大写 P）
- `-i`: 指定密钥文件

## sftp 命令

### 功能
sftp（SSH File Transfer Protocol）是基于 SSH 的文件传输协议，提供交互式文件传输。

### 使用方法
```bash
# 连接到远程服务器
sftp user@host

# 在 sftp 会话中
put /local/file /remote/path    # 上传文件
get /remote/file /local/path     # 下载文件
ls                               # 列出远程目录
lls                              # 列出本地目录
cd /remote/path                  # 切换远程目录
lcd /local/path                  # 切换本地目录
quit                             # 退出
```

### 上传文件示例
```bash
sftp user@host
put /root/abc.txt
```

### 与 SSH 的关系
- SFTP 是 SSH 的子系统，共享同一个连接
- 默认使用 SSH 的 22 端口；可通过 `sftp -P` 指定其他端口
- 每次启动 `sftp` 通常会单独建立 SSH 连接并认证；配置 SSH 连接复用时才可能复用底层连接
- 所有数据传输都是加密的

## rz 和 sz 命令

### 功能
rz（Receive ZMODEM）和 sz（Send ZMODEM）使用 ZMODEM 协议进行文件传输，常用于虚拟终端软件（如 XShell、SecureCRT、Putty）。

### rz - 上传文件
```bash
# 上传文件，同名覆盖
rz -y
```

**说明**：
- 当我们使用虚拟终端软件，如 Xshell、SecureCRT 或 PuTTY 来连接远程服务器后，使用 rz 命令可以上传本地文件到远程服务器
- 输入 rz 回车后，会出现文件选择对话框，选择需要上传文件，一次可以指定多个文件
- 上传到服务器的路径为当前执行 rz 命令的目录
- **注意**：不能上传文件夹，如果上传文件夹，请先打包再上传
- 可以在虚拟终端软件设置上传时默认加载的本地路径和下载的路径

### sz - 下载文件
```bash
# 下载单个文件
sz file1

# 下载多个文件
sz file1 file2 file3

# 下载目录下所有文件
sz abc/*
```

**说明**：
- sz（Send ZMODEM）通过 ZMODEM 协议，可将多个文件从远程服务器下载到本地
- **注意**：不能下载文件夹，如果下载文件夹，请先打包再下载

### 安装
```bash
# CentOS/RHEL
yum install lrzsz -y

# Ubuntu/Debian
apt-get install lrzsz
```

## 传输方式对比

| 方式 | 协议 | 端口 | 加密 | 适用场景 |
|------|------|------|------|----------|
| scp | SSH | 22 | 是 | 命令行文件传输 |
| sftp | SSH | 22 | 是 | 交互式文件传输 |
| rz/sz | ZMODEM | 依赖终端会话 | 取决于外层连接 | 支持 ZMODEM 的终端软件 |
| ftp | FTP | 21 | 否 | 传统文件传输（不推荐） |

## 易错点
- scp 传输目录必须使用 `-r` 参数
- rz/sz 不能传输文件夹，需要先打包
- rz/sz 需要终端软件支持；通过 SSH 会话使用时，外层连接会加密
- scp 和 sftp 基于 SSH，更安全

## 实战示例
```bash
# scp 下载
scp root@192.168.0.101:/var/www/test.txt ~

# scp 上传
scp /var/www/test.php root@192.168.0.101:/var/www/

# scp 传输目录
scp -r /local/dir root@192.168.0.101:/var/www/

# sftp 交互式传输
sftp user@host
put /local/file
get /remote/file

# rz/sz 使用
rz -y              # 上传
sz file1 file2     # 下载
```

## 延伸阅读
- [ssh.md](./ssh.md) - SSH 远程登录
- [ping.md](./ping.md) - 网络连通性测试
