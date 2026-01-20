# CPU 使用率过高

## 常用场景
- CPU 100%
- 系统卡顿
- 性能问题

## 排查步骤
1. 查看 CPU 使用: `top` 或 `htop`
2. 查看进程: `ps aux --sort=-%cpu | head`
3. 查看系统负载: `uptime`
4. 分析进程: `strace -p PID`

## 常用命令
```bash
top
htop
ps aux --sort=-%cpu | head -10
uptime
```

## 解决方案
- 终止异常进程
- 调整进程优先级
- 优化应用配置
