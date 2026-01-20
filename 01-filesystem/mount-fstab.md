# mount / fstab

## 常用场景
- 挂载磁盘分区
- 配置开机自动挂载

## 常用命令
```bash
mount /dev/sda1 /mnt
umount /mnt
mount -a
```

## fstab 格式
```
/dev/sda1  /mnt  ext4  defaults  0  2
```

## 易错点
- umount 时设备不能在使用中
- fstab 错误可能导致系统无法启动

## 实战示例
```bash
# 查看已挂载
mount | grep sda

# 编辑 fstab
vim /etc/fstab
```
