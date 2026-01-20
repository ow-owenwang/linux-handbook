# 内存泄漏

## 常用场景
- 内存持续增长
- OOM (Out of Memory)
- 系统变慢

## 排查步骤
1. 查看内存: `free -h`
2. 查看进程内存: `ps aux --sort=-%mem | head`
3. 查看系统内存: `vmstat 1`
4. 查看 OOM 日志: `dmesg | grep -i oom`

## 常用命令
```bash
free -h
ps aux --sort=-%mem | head -10
vmstat 1
dmesg | grep -i oom
```

## 解决方案
- 重启服务
- 调整应用配置
- 增加 swap
