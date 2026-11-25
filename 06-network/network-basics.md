# 网络基础

## 常用场景
- 理解网络配置
- 网络故障排查

## 核心概念
- IP 地址
- 子网掩码
- 网关
- DNS

## 网络配置文件
- `/etc/network/interfaces`: 部分 Debian 系统使用；Ubuntu 常见 Netplan 或 NetworkManager
- `/etc/sysconfig/network-scripts/`: 较旧 RHEL 系系统使用；新系统常见 NetworkManager
- `/etc/resolv.conf`: 解析器配置，可能由 systemd-resolved、NetworkManager 等自动生成

## 常用命令
```bash
ip addr                 # 显示网络设备
ip route                # 显示路由
ifconfig                # 显示或设置网络设备
```

## ifconfig 基本用法
```bash
ifconfig                # 显示已启用接口（需安装 net-tools）
ifconfig eth0           # 显示指定网卡信息
ifconfig eth0 up        # 启用 eth0 网卡
ifconfig eth0 down      # 停用 eth0 网卡
```

## 网络测试
```bash
ping 192.168.0.1        # 探测网络是否通畅
netstat -an | grep 3306 # 查询 3306 端口占用情况
```

## 延伸阅读
- [ifconfig.md](./ifconfig.md) - 网卡配置
- [ping.md](./ping.md) - 网络连通性测试
- [route.md](./route.md) - 路由设置
- [telnet.md](./telnet.md) - Telnet 端口探测
- [scp-sftp.md](./scp-sftp.md) - 文件传输
- [dns.md](./dns.md) - DNS 配置
- [ssh.md](./ssh.md) - SSH 远程登录
