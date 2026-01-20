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

## 延伸阅读
- [disk-management.md](./disk-management.md)
