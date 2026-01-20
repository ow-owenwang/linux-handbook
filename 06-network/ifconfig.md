# ifconfig

## 常用场景
- 查看网卡信息
- 配置网络参数
- 启用/禁用网卡
- 网络故障排查

## 功能
查看或配置网卡信息

## 查看网卡信息

### 基本用法
```bash
ifconfig                # 显示所有网卡的信息
ifconfig eth0           # 显示指定网卡的信息
ifconfig -a             # 显示所有网络接口状态（包括未启用的）
```

### 输出字段说明

| 字段 | 说明 |
|------|------|
| `eth0` | 网络接口名称 |
| `Link encap` | 链路封装协议（如 Ethernet） |
| `Hwaddr` | 网络接口的 MAC 地址 |
| `inet addr` | IP 地址 |
| `Bcast` | 广播地址 |
| `Mask` | 子网掩码 |
| `UP` | 网络接口状态标识，UP 已经启用，DOWN 已经停用 |
| `BROADCAST` | 广播标识，标识网络接口是否支持广播 |
| `RUNNING` | 传输标识，标识网络接口是否已经开始传输分组数据 |
| `MULTICAST` | 多播标识，标识网络接口是否支持多播 |
| `MTU` | 最大传输单位，单位：字节 |
| `Metric` | 度量值，用于 RIP 建立网络路由用 |
| `RX bytes` | 接收数据字节统计 |
| `TX bytes` | 发送数据字节统计 |

## 配置网络参数

### 使用格式
```bash
ifconfig 网络接口名称 [地址协议类型] [address] [参数]
```

### 地址协议类型
- `inet`: IPv4 地址
- `inet6`: IPv6 地址

### 常用配置命令
```bash
# 设置 IP 地址和子网掩码
sudo ifconfig eth0 inet 192.168.10.254 netmask 255.255.255.0

# 启用网络接口
sudo ifconfig eth0 up

# 关闭网络接口
sudo ifconfig eth0 down

# 设置 IP 地址（自动计算子网掩码）
sudo ifconfig eth0 192.168.21.165
```

### 常用参数
- `inet [IP地址]`: 设置 IP 地址
- `netmask [子网掩码]`: 设置子网掩码
- `up`: 启用网络接口
- `down`: 关闭网络接口
- `-a`: 显示所有网络接口状态

## 持久化配置

### 重要提示
ifconfig 配置的网络参数在内存中，计算机重新启动之后就失效了。如果需要持久有效，就需要修改网络接口的配置文件。

### Red Hat/CentOS
修改 `/etc/sysconfig/network-scripts/ifcfg-eth0` 文件：
```bash
IPADDR=192.168.1.100
GATEWAY=192.168.1.1
NETMASK=255.255.255.0
```

### Ubuntu/Debian
修改 `/etc/NetworkManager/system-connections/Wired connection 1` 文件：
```ini
[ipv4]
method=manual
addresses1=192.168.1.100;24;192.168.1.1
```

或者使用 netplan（Ubuntu 18.04+）：
```yaml
# /etc/netplan/01-netcfg.yaml
network:
  version: 2
  ethernets:
    eth0:
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
```

## 易错点
- 只有 root 才能用 ifconfig 配置参数，其他用户只能查看
- ifconfig 配置是临时的，重启后失效
- 配置错误可能导致网络中断
- 现代系统推荐使用 `ip` 命令（`ip addr`, `ip link`）

## 实战示例
```bash
# 查看所有网卡
ifconfig

# 查看指定网卡
ifconfig eth0

# 配置 IP 地址
sudo ifconfig eth0 192.168.21.165
sudo ifconfig eth0 inet 192.168.10.254 netmask 255.255.255.0 up

# 启用/禁用网卡
sudo ifconfig eth0 up
sudo ifconfig eth0 down
```

## 延伸阅读
- [network-basics.md](./network-basics.md) - 网络基础
- [route.md](./route.md) - 路由设置
