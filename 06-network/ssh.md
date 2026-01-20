# SSH

## 常用场景
- 远程登录
- 文件传输
- 密钥认证
- 构建跳板隧道
- Socket5 代理

## 常用命令
```bash
ssh user@host
ssh -p 2222 user@host
scp file user@host:/path
```

## SSH 安装和配置

### 安装
```bash
# Ubuntu/Debian
sudo apt-get install openssh-server
sudo apt-get install openssh-client

# 卸载
sudo apt remove openssh-server
sudo apt remove openssh-client
```

### 配置
```bash
vim /etc/ssh/sshd_config
```

### 启动服务
```bash
# 启动
service ssh start
# 或
sudo /etc/init.d/ssh start
# 或 (systemd)
sudo systemctl start ssh

# 查看状态
service ssh status
ps -aux | grep ssh
netstat -a | grep ssh

# 停止
service ssh stop
```

### Ubuntu 配置示例
```bash
# 安装
apt install openssh-server

# 配置
cp /etc/ssh/sshd_config /etc/ssh/sshd_config-bak
echo "PermitRootLogin yes" >> /etc/ssh/sshd_config

# 启动
sudo service ssh start
```

## SSH 配置
- `~/.ssh/config`: 客户端配置
- `/etc/ssh/sshd_config`: 服务器配置

## 密钥认证

### 生成密钥
```bash
ssh-keygen -t rsa
```

### 添加公钥到远程服务器
```bash
# 方法1：手动添加
cat id_rsa.pub >> ~/.ssh/authorized_keys

# 方法2：使用 ssh-copy-id（推荐）
ssh-copy-id -i ~/.ssh/id_rsa.pub user@host
```

### ssh-copy-id
`ssh-copy-id` 命令是一个方便的工具，用于在远程服务器上安装你的公钥，以实现 SSH 的无密码登录。

**使用方法**：
```bash
ssh-copy-id 用户名@远程服务器
ssh-copy-id -i ~/.ssh/mykey user@host
```

**执行过程**：
1. 通过 SSH 连接到远程服务器
2. 将你的公钥（`~/.ssh/id_rsa.pub`）安装到远程用户主目录下的 `~/.ssh/authorized_keys` 文件中

## SSH Agent

### 功能
SSH Agent（Secure Shell Agent）是一个用于管理 SSH 密钥的程序。它的主要作用是在用户登录到 SSH 密钥所在的系统后，将私钥加载到内存中，并在用户的会话期间保持活动状态，以便在需要时自动提供 SSH 私钥，而不需要用户手动输入密码。

### 主要功能
1. **私钥管理**：SSH Agent 负责管理用户的 SSH 私钥，通常是 `~/.ssh/id_rsa`（或其他命名的私钥文件）
2. **密码缓存**：当 SSH 私钥被加密时，用户需要提供密码才能解锁私钥。SSH Agent 会在用户第一次使用私钥时要求输入密码，并将密码缓存在内存中
3. **单一登录**：如果用户在一个系统上登录，并且 SSH Agent 正在运行，那么他们可以在同一会话中使用加载到 SSH Agent 的私钥连接到其他远程系统，而不需要再次提供密码
4. **避免多次输入密码**：当用户需要在一个会话中执行多次 SSH 操作时，SSH Agent 可以避免用户多次输入 SSH 私钥密码

### 优势
使用 SSH Agent 可以提高 SSH 密钥的安全性和便利性。用户可以在 SSH 会话期间只需要输入密码一次，之后所有的 SSH 操作都会使用 SSH Agent 提供的私钥，而无需再次输入密码。

## SSH 高级用法

### 指定密钥路径、端口、用户及配置文件
```bash
# 以 test 用户连接 192.168.1.10 主机，使用当前用户家目录下 mykey 文件作为密钥文件，
# 指定访问远程主机的 2020 端口，并使用 myconfig 作为本地 ssh 客户端配置
ssh -l test 192.168.1.10 -i ~/mykey -p 2020 -F ~/myconfig
```

**参数说明**：
- `-i`：指定密钥路径
- `-p`：指定 ssh 端口
- `-l`：指定用户
- `-F`：指定配置文件
- `-t`：以交互模式工作

### 调试模式与绑定 IP 地址

#### 调试模式
```bash
ssh -v hostname
```
- `-v`：以类似 log 的形式返回 debug 信息，可以帮助运维人员在 ssh 连接出现问题时快速查找问题

#### 绑定 IP
如果你的 ssh 客户端有多于两个以上的 ip 地址，你就不可能分得清楚到底是哪一个 ip 地址连接到了 ssh 服务。

```bash
ssh -b 192.168.1.10 root@10.0.0.10
```
以上命令表示为从 192.168.1.10 这个 ip 来与 10.0.0.10 建立 ssh 连接。

### SSH 构建跳板隧道
本地可直接访问 hostA，hostB 只允许 hostA 访问，用 SSH 构建本地到 B 的连接通道。

```bash
# 首先与 192.168.1.10 建立 ssh 连接，并通过此连接与 10.0.0.10 建立 ssh 连接
ssh -t 192.168.1.10 ssh 10.0.0.10
```

### 构建 Socket5 代理
案例：hostA 可访问 www.website.com，hostB 无法直接访问该站点。现要求 hostB 可访问该站点。

```bash
# 使用 plink（Windows）
plink username@hostA -D 2020

# 使用 ssh（Linux/Mac）
ssh -D 2020 username@hostA
```

成功建立 ssh 隧道后，在浏览器中设置 Socket5 代理，填写指定的 2020 端口即可通过 hostA 网络获取本地受限的网络资源。

## SFTP 和 SSH 的关系

### 关系说明
**SFTP 和 SSH 的关系非常紧密**，SFTP 实际上是基于 SSH 协议运行的。

### 1. SFTP 是 SSH 的子系统
- SFTP（SSH File Transfer Protocol）是 SSH 协议的一个子系统，专门用于文件传输
- 它并不是独立的协议，而是依赖于 SSH 协议来建立连接和进行数据传输
- 因此，**SFTP 和 SSH 共享同一个连接**

### 2. 连接机制
- 当你通过 SSH 连接到远程服务器时，SSH 协议会建立一个加密的通信通道
- 如果你需要使用 SFTP，SSH 服务器会在这个已有的 SSH 连接上启动 SFTP 子系统
- 这意味着：
  - **不需要单独建立 SFTP 连接**，SFTP 直接复用 SSH 的连接
  - **认证方式也是共享的**：如果你已经通过 SSH 认证（如密码或密钥），SFTP 会自动使用相同的认证信息，无需重新输入

### 3. 为什么 SFTP 不需要重新认证？
因为 SFTP 是 SSH 的一个功能，它完全依赖于 SSH 的连接和认证机制。一旦 SSH 连接建立并认证成功，SFTP 就可以直接使用这个连接进行文件传输，无需额外的认证步骤。

### 4. SFTP 和 SSH 的端口
- SSH 默认使用 **22 端口**
- SFTP 也使用相同的 **22 端口**，因为它是在 SSH 连接上运行的，不需要单独的端口

### 5. SFTP 与 FTP 的区别
- **FTP** 是一个独立的文件传输协议，使用 **21 端口**（控制端口）和 **20 端口**（数据端口），且传输是明文的，不安全
- **SFTP** 是基于 SSH 的，使用 **22 端口**，所有数据传输都是加密的，安全性更高

## 常用参数
- `-p`: 指定端口
- `-i`: 指定密钥文件
- `-l`: 指定用户
- `-F`: 指定配置文件
- `-t`: 以交互模式工作
- `-v`: 调试模式
- `-b`: 绑定 IP 地址
- `-D`: 构建 Socket5 代理
- `-L`: 本地端口转发

## 查看 SSH 服务信息
```bash
# 查看安装包
rpm -qa | grep ssh

# 查看服务是否运行
ps -ef | grep ssh

# 查看网络连接情况
netstat -ntlp | grep ssh

# 如果 ssh 已经正常工作了，但是利用 ssh 客户端连不上，尝试关闭防火墙
service iptables stop
```

## 查看外网 IP 地址
```bash
curl ifconfig.me
curl cip.cc
curl ip.sb
```

## 实战示例
```bash
# 基本连接
ssh -i ~/.ssh/id_rsa user@example.com

# 指定端口和用户
ssh -p 2222 -l test 192.168.1.10

# 文件传输
scp -r dir/ user@host:/remote/path

# 跳板连接
ssh -t 192.168.1.10 ssh 10.0.0.10

# Socket5 代理
ssh -D 2020 user@hostA
```
