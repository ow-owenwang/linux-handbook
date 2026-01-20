# netstat / ss

## 常用场景
- 查看网络连接
- 查看端口监听
- 监控网络状态
- 网络故障排查

## netstat 命令

### 功能
netstat 命令监控网络状态，包括接口设置、IP 路由、各种网络协议的统计。

### 输出信息说明
- **Proto**: 协议，如：tcp, udp
- **Recv-Q**: 尚未读取的数据字节数
- **Send-Q**: 尚未发送的数据字节数
- **Local_address**: 本地主机地址与端口号
- **Foreign_address**: 远程主机与端口号
- **State**: 网络连接状态
- **RefCnt**: 引用计数，表示加接到相应套接字的进程数量
- **Flags**: 标志字段
- **Type**: 套接字类型，如：SOCK_DGRAM, SOCK_STREAM, SOCK_RAW
- **Path**: 套接字路径名

### 常用命令
```bash
netstat -a              # 列出所有端口
netstat -i              # 显示网络接口列表
netstat -at             # 所有 tcp 端口
netstat -au             # 所有 udp 端口
netstat -l              # 所有监听端口
netstat -lt             # tcp 监听端口
netstat -lu             # udp 监听端口
netstat -s              # 显示所有协议统计信息
netstat -r              # 当前路由状态
netstat -p              # 输出中显示 PID 和进程名称
netstat -tulpn          # 常用组合：显示所有 TCP/UDP 监听端口及进程
```

### 常用参数
- `-a`: 列出所有端口
- `-i`: 显示网络接口列表
- `-t`: TCP 协议
- `-u`: UDP 协议
- `-l`: 监听端口
- `-n`: 数字格式（不解析域名）
- `-p`: 显示 PID 和进程名称
- `-s`: 显示所有协议统计信息
- `-r`: 显示路由表

## ss 命令

### 功能
ss 是 netstat 的现代替代品，功能类似但更快。

### 常用命令
```bash
ss -tulpn               # 显示所有 TCP/UDP 监听端口及进程
ss -lntp                # 显示 TCP 监听端口及进程
ss -an                  # 显示所有连接（数字格式）
```

## 易错点
- ss 比 netstat 更快更现代，推荐使用
- 需要 root 权限查看所有进程信息
- netstat 在某些新系统上可能未安装

## 实战示例
```bash
# 查看监听端口
ss -lntp | grep :80
netstat -lntp | grep :80

# 查看所有连接
netstat -an | grep ESTABLISHED

# 查看路由
netstat -r

# 查看网络统计
netstat -s
```
