# 启动过程

## 常用场景
- 理解系统启动
- 故障排查

## 启动阶段
1. BIOS/UEFI
2. Bootloader (GRUB)
3. 内核加载
4. Init 进程 (systemd)
5. 运行级别/目标

## 相关文件
- `/etc/default/grub`: GRUB 配置
- `/etc/fstab`: 文件系统挂载
- `/etc/systemd/system/`: systemd 单元

## 延伸阅读
- [systemd.md](./systemd.md)
