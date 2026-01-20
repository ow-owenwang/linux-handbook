# 日志管理

## 常用场景
- 查看系统日志
- 分析应用日志
- 日志轮转

## 常用命令
```bash
journalctl
journalctl -u service
journalctl -f
tail -f /var/log/syslog
```

## 日志位置
- `/var/log/`: 系统日志
- `journalctl`: systemd 日志
- 应用日志通常在 `/var/log/` 或应用目录

## 日志轮转
- `/etc/logrotate.conf`: 轮转配置
- `/etc/logrotate.d/`: 应用配置

## 实战示例
```bash
journalctl -u nginx -f
journalctl --since "1 hour ago"
```
