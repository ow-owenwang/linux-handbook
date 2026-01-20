# 目录结构

## 常用场景
- 理解 Linux 目录层次
- 查找文件位置
- 了解各目录用途

## FHS 标准
FHS (Filesystem Hierarchy Standard) 是 Linux 文件系统层次结构标准，于 1994 年推出，统一了 Linux 界命名混乱的局面。

## 主要目录说明

### `/` - 根目录
- 根目录，一般根目录下只存放目录
- 在 Linux 下有且只有一个根目录
- 所有的东西都是从这里开始
- 当你在终端里输入 `/home`，你其实是在告诉电脑，先从 `/`（根目录）开始，再进入到 home 目录

### `/bin` 和 `/usr/bin` - 可执行二进制文件
- 可执行二进制文件的目录
- 如常用的命令 ls、tar、mv、cat 等
- `/bin` 存放系统基本命令
- `/usr/bin` 存放用户命令

### `/boot` - 启动文件
- 放置 Linux 系统启动时用到的一些文件
- Linux 的内核文件：`/boot/vmlinuz`
- 系统引导管理器：`/boot/grub`

### `/dev` - 设备文件
- 存放 Linux 系统下的设备文件
- 访问该目录下某个文件，相当于访问某个设备
- 常用的是挂载光驱：`mount /dev/cdrom /mnt`

### `/etc` - 系统配置
- 系统配置文件存放的目录
- 不建议在此目录下存放可执行文件
- 重要的配置文件有：
  - `/etc/inittab`
  - `/etc/fstab`
  - `/etc/init.d`
  - `/etc/X11`
  - `/etc/sysconfig`
  - `/etc/xinetd.d`

### `/home` - 用户主目录
- 系统默认的用户家目录
- 新增用户账号时，用户的家目录都存放在此目录下
- `~` 表示当前用户的家目录
- `~username` 表示用户 username 的家目录

### `/lib`、`/usr/lib`、`/usr/local/lib` - 函数库
- 系统使用的函数库的目录
- 程序在执行过程中，需要调用一些额外的参数时需要函数库的协助

### `/lost+found` - 丢失文件
- 系统异常产生错误时，会将一些遗失的片段放置于此目录下

### `/mnt` 和 `/media` - 挂载点
- 光盘默认挂载点
- 通常光盘挂载于 `/mnt/cdrom` 下
- 也可以选择任意位置进行挂载

### `/opt` - 可选软件
- 给主机额外安装软件所摆放的目录

### `/proc` - 虚拟文件系统
- 此目录的数据都在内存中
- 如系统核心，外部设备，网络状态
- 由于数据都存放于内存中，所以不占用磁盘空间
- 比较重要的目录有：
  - `/proc/cpuinfo`
  - `/proc/interrupts`
  - `/proc/dma`
  - `/proc/ioports`
  - `/proc/net/*`

### `/root` - root 用户主目录
- 系统管理员 root 的家目录

### `/sbin`、`/usr/sbin`、`/usr/local/sbin` - 系统管理命令
- 放置系统管理员使用的可执行命令
- 如 fdisk、shutdown、mount 等
- 与 `/bin` 不同的是，这几个目录是给系统管理员 root 使用的命令
- 一般用户只能"查看"而不能设置和使用

### `/tmp` - 临时文件
- 一般用户或正在执行的程序临时存放文件的目录
- 任何人都可以访问
- 重要数据不可放置在此目录下

### `/srv` - 服务数据
- 服务启动之后需要访问的数据目录
- 如 www 服务需要访问的网页数据存放在 `/srv/www` 内

### `/usr` - 用户程序
- 应用程序存放目录
- `/usr/bin`: 存放应用程序
- `/usr/share`: 存放共享数据
- `/usr/lib`: 存放不能直接运行的，却是许多程序运行所必需的一些函数库文件
- `/usr/local`: 存放软件升级包
- `/usr/share/doc`: 系统说明文件存放目录
- `/usr/share/man`: 程序说明文件存放目录

### `/var` - 可变数据
- 放置系统执行过程中经常变化的文件
- `/var/log`: 随时更改的日志文件
- `/var/log/message`: 所有的登录文件存放目录
- `/var/spool/mail`: 邮件存放的目录
- `/var/run`: 程序或服务启动后，其 PID 存放在该目录下

## 目录说明
- FHS (Filesystem Hierarchy Standard) 标准
- 各目录的用途和约定

## 延伸阅读
- [../00-intro/common-paths.md](../00-intro/common-paths.md) - 常用路径
- [../00-intro/filesystem-overview.md](../00-intro/filesystem-overview.md) - 文件系统概述
- [permissions.md](./permissions.md) - 文件权限
- [ln.md](./ln.md) - 链接文件
