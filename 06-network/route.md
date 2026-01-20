# route

## 常用场景
- 查看路由表
- 添加路由
- 删除路由
- 修改路由
- 网络路由配置

## 功能
route 可以增加、修改、显示路由信息

## 使用格式
```bash
route [-v] [-A family] add default [gw 默认网关地址] [[dev interface]]
route [-v] [-A family] del default [gw 默认网关地址] [[dev interface]]
route -n                    # 显示路由表（数字格式）
```

## 查看路由

### 常用命令
```bash
route                      # 显示路由表
route -n                   # 以数字格式显示（不解析主机名）
route -v                   # 显示详细信息
```

## 添加路由

### 添加默认网关
```bash
route add default gw 192.168.1.1 dev eth0
```

### 添加特定路由
```bash
route add -net 192.168.2.0/24 gw 192.168.1.1 dev eth0
route add -host 192.168.2.100 gw 192.168.1.1
```

## 删除路由

### 删除默认网关
```bash
route del default gw 192.168.1.1
```

### 删除特定路由
```bash
route del -net 192.168.2.0/24
route del -host 192.168.2.100
```

## 常用参数

| 参数 | 功能 |
|------|------|
| `add` | 增加路由信息 |
| `del` | 删除路由信息 |
| `-v` | 显示路由信息（详细模式） |
| `-A` | 指定网络协议 inet(IPv4), inet6(IPv6) |
| `gw` | 指定默认网关地址 |
| `dev` | 指定网络接口 |
| `-n` | 以数字格式显示（不解析主机名） |
| `-net` | 指定网络路由 |
| `-host` | 指定主机路由 |

## 路由表说明
路由表显示的信息包括：
- **Destination**: 目标网络或主机
- **Gateway**: 网关地址
- **Genmask**: 网络掩码
- **Flags**: 标志（U=up, G=gateway, H=host）
- **Iface**: 网络接口

## 易错点
- 添加/删除路由需要 root 权限
- 错误的网关配置可能导致网络中断
- 删除默认网关可能导致无法访问外网
- 现代系统推荐使用 `ip route` 命令

## 实战示例
```bash
# 查看路由表
route -n

# 添加默认网关
sudo route add default gw 192.168.1.1 dev eth0

# 添加网络路由
sudo route add -net 192.168.2.0/24 gw 192.168.1.1 dev eth0

# 删除默认网关
sudo route del default gw 192.168.1.1

# 删除网络路由
sudo route del -net 192.168.2.0/24
```

## 现代替代方案
推荐使用 `ip route` 命令（功能更强大）：
```bash
ip route show              # 显示路由表
ip route add default via 192.168.1.1 dev eth0
ip route del default
```

## 延伸阅读
- [network-basics.md](./network-basics.md) - 网络基础
- [ifconfig.md](./ifconfig.md) - 网卡配置
