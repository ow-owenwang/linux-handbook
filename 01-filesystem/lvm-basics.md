# LVM 基础

## 常用场景
- 动态调整磁盘空间
- 管理逻辑卷

## 核心概念
- PV (Physical Volume)
- VG (Volume Group)
- LV (Logical Volume)

## 常用命令
```bash
pvcreate /dev/sda1
vgcreate vg0 /dev/sda1
lvcreate -L 10G -n lv0 vg0
lvextend -L +5G /dev/vg0/lv0
```

以上命令仅为流程示意，`pvcreate` 会覆写设备上的元数据，执行前先用 `lsblk -f` 确认设备和备份。`lvextend` 只扩大逻辑卷；文件系统还需扩容，可在支持的环境下使用 `lvextend -r -L +5G /dev/vg0/lv0` 一并调整。XFS、ext4 等文件系统的缩容能力不同，不能把扩容步骤反向照搬。

## 延伸阅读
- [disk-management.md](./disk-management.md)
