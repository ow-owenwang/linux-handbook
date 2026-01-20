# systemd

## 常用场景
- 管理系统服务
- 理解现代 Linux 初始化

## 核心概念
- Unit: 服务单元
- Target: 运行目标（类似运行级别）
- Service: 服务单元

## 常用命令
```bash
systemctl status service
systemctl start service
systemctl stop service
systemctl enable service
systemctl disable service
```

## 延伸阅读
- [service-management.md](./service-management.md)
- [boot-process.md](./boot-process.md)
