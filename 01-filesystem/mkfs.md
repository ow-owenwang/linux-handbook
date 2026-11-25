# mkfs

## 常用场景
- 格式化磁盘分区
- 创建文件系统
- 磁盘初始化

## 功能
mkfs 命令相当于 DOS/Windows 系统中的格式化命令，用于创建指定的文件系统。

## 使用格式
```bash
mkfs [选项] 设备文件名 [blocks]
```

## 常用命令
```bash
mkfs.ext4 /dev/sda1           # 格式化为 ext4 文件系统
mkfs -t ext4 /dev/sda1         # 指定文件系统类型
mkfs.ext4 -c /dev/sda1         # 格式化并检查坏块
mkfs.ext3 /dev/sda1            # 格式化为 ext3 文件系统
mkfs.xfs /dev/sda1             # 格式化为 xfs 文件系统
```

## 常用参数
- `-V`: 详细显示模式
- `-t <fs>`: 指定文件系统类型，默认值为 ext2
  - 常用类型：ext2, ext3, ext4, xfs, btrfs
- `-c`: 在创建文件系统的同时，进行磁盘坏块检查
- 可选的 `blocks` 参数在支持它的 `mkfs` 前端中表示文件系统块的**数量**；块大小由具体文件系统工具的选项设置，不要混淆

## 常用文件系统类型
- `ext2`: 较老的 Linux 文件系统
- `ext3`: ext2 的改进版，支持日志
- `ext4`: 现代 Linux 默认文件系统
- `xfs`: 高性能文件系统
- `btrfs`: 支持快照和压缩的文件系统

## 易错点
- **格式化会删除所有数据**，操作前务必确认
- 需要 root 权限
- 格式化前确保设备未被挂载（使用 `umount`）
- 错误的文件系统类型可能导致无法使用

## 实战示例
```bash
# 查看设备
lsblk
fdisk -l

# 卸载设备（如果已挂载）
umount /dev/sda1

# 格式化为 ext4
sudo mkfs.ext4 /dev/sda1

# 格式化并检查坏块
sudo mkfs.ext4 -c /dev/sda1

# 格式化为 xfs
sudo mkfs.xfs /dev/sda1
```

## 延伸阅读
- [disk-management.md](./disk-management.md) - 磁盘管理
- [mount-fstab.md](./mount-fstab.md) - 挂载文件系统
