# SSH 远程登录

SSH 提供加密的远程登录、命令执行和端口转发。客户端配置通常在 `~/.ssh/config`，服务端配置通常在 `/etc/ssh/sshd_config`；服务名称因发行版可能为 `ssh` 或 `sshd`。

## 登录与诊断

```bash
ssh user@host
ssh -p 2222 -i ~/.ssh/id_ed25519 user@host
ssh -v user@host                         # 查看连接诊断信息
ssh -b 192.168.1.10 user@host           # 指定本地源地址，必须是本机地址
ssh -J jump_user@jump_host user@target  # 通过跳板机登录
```

常用选项：`-l user` 指定登录用户，`-p` 指定端口，`-i` 指定私钥，`-F` 指定客户端配置文件，`-t` 强制分配伪终端，`-v` 输出调试信息。连接失败时依次检查 DNS、网络、目标端口、防火墙、服务状态、认证和服务端日志；不要直接关闭防火墙来排障。

```bash
sudo systemctl status ssh     # Debian/Ubuntu 常见服务名
sudo systemctl status sshd    # RHEL 系常见服务名
sudo ss -lntp | grep ':22'
```

## 安装与配置

Debian/Ubuntu 上可用 `sudo apt install openssh-server` 安装服务端。修改配置前备份文件，使用 `sudo sshd -t` 检查语法；确认现有会话仍可登录后再 `sudo systemctl reload ssh`（或 `sshd`）。远程维护时保留一个已登录会话，避免配置错误导致无法再次连接。

不建议通过追加 `PermitRootLogin yes` 来开启 root 密码登录。应使用普通用户及受控的 `sudo` 权限，并按环境需要配置密钥登录。服务端配置可能包含 `Include` 文件，检查最终有效配置可使用 `sshd -T`。

## 密钥认证

```bash
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub user@host
ssh -i ~/.ssh/id_ed25519 user@host
```

公钥安装到**远程目标用户**的 `~/.ssh/authorized_keys`；私钥留在本机，不要复制给服务器或他人。`ssh-copy-id` 仍需先通过目标主机允许的方式登录。密钥口令保护私钥；`ssh-agent` 可以在会话中保存已解锁的密钥，减少重复输入口令，使用 `ssh-add ~/.ssh/id_ed25519` 加载。口令不是远程账号密码，Agent 也不会把私钥自动上传到远程主机。

## 跳板与端口转发

```bash
ssh -J user@jump user@target              # 目标主机只允许跳板机访问
ssh -N -L 8080:127.0.0.1:80 user@host     # 本地 8080 转到远端可访问的 80
ssh -N -D 127.0.0.1:2020 user@host        # 本地 SOCKS 代理
```

`-D` 在本机监听 SOCKS 端口，浏览器需显式设置该代理；DNS 是否经代理解析取决于客户端设置。`-L` 的目标地址从 SSH 服务端一侧访问。转发权限还受服务端配置限制。

## 文件传输

`scp` 和 `sftp` 都通过 SSH 加密传输。每次运行 `sftp user@host` 通常会建立自己的 SSH 连接，不会自动复用之前的 `ssh` 登录或免除认证；若配置了连接复用则可能共享底层连接。默认端口是 22，但可由配置或命令选项修改。详见 [scp / sftp](./scp-sftp.md)。

参考：[OpenSSH ssh 手册](https://man.openbsd.org/ssh)、[ssh-keygen 手册](https://man.openbsd.org/ssh-keygen)、[sftp 手册](https://man.openbsd.org/sftp)。
