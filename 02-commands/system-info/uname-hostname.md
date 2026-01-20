# uname / hostname

## 常用场景
- 查看系统信息
- 查看主机名

## 常用命令
```bash
uname -a
uname -r
hostname
hostnamectl
```

## 常用参数
- uname -a: 所有信息
- uname -r: 内核版本
- uname -m: 架构

## 查看操作系统信息

### uname 命令
```bash
uname                  # 显示系统名称
uname -m               # 显示机器硬件名称
uname -r               # 显示内核版本
uname -a               # 显示本机详细信息
```

**uname -a 输出说明**：
依次为：内核名称(类别)，主机名，内核版本号，内核版本，内核编译日期，硬件名，处理器类型，硬件平台类型，操作系统名称

### 其他查看系统信息的方法
```bash
# 查看系统版本（Linux）
cat /etc/os-release
lsb_release -a

# 查看系统版本（Ubuntu）
cat /etc/issue          # 查看是否有版本更新
lsb_release -a          # 查看系统当前版本

# 查看系统版本（Mac）
uname
uname -r
```

### 系统更新（Ubuntu）
```bash
# 查看是否有版本更新
cat /etc/issue

# 如果有新版本，执行以下命令
sudo apt-get upgrade
```

## hostname 命令
```bash
hostname                # 查看当前主机名
cat /etc/hostname       # 查看主机名配置文件

# 修改主机名
hostnamectl set-hostname newname
# 或
vim /etc/hostname       # 编辑配置文件（需要重启生效）
# 或（CentOS/RHEL）
vim /etc/sysconfig/network
```

## 实战示例
```bash
# 查看系统信息
uname -a
uname -m
cat /etc/os-release
lsb_release -a

# 查看和修改主机名
hostname
hostnamectl set-hostname newname
```
