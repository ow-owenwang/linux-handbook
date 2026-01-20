# 磁盘管理

## 常用场景
- 分区管理
- 创建文件系统
- 检查文件系统

## 常用命令
```bash
fdisk -l
parted /dev/sda
mkfs.ext4 /dev/sda1
fsck /dev/sda1
```

## 常用参数
- fdisk: -l 列出所有分区
- mkfs: -t 指定文件系统类型

## 易错点
- 分区操作会丢失数据，务必谨慎
- 格式化前确认设备名称

## 延伸阅读
- [lvm-basics.md](./lvm-basics.md)
- [../02-commands/system-info/df-du.md](../02-commands/system-info/df-du.md)
