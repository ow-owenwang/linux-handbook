# kill / pkill

## 常用场景
- 终止进程
- 发送信号
- 强制结束进程

## 使用格式
```bash
kill [-signal] pid
```

## 常用命令
```bash
kill PID              # 正常终止进程（默认发送信号 15）
kill -9 PID            # 强制终止进程
kill -signal PID       # 发送指定信号
killall process_name   # 根据进程名终止
pkill process_name     # 根据进程名终止（支持模式匹配）
```

## 常用信号
信号值从 0 到 15，常用信号：
- `15` (SIGTERM): 正常终止（默认），允许进程清理资源
- `9` (SIGKILL): 绝对终止，强制结束，无法被捕获或忽略
- `1` (SIGHUP): 挂起信号，常用于重新加载配置
- `2` (SIGINT): 中断信号（相当于 Ctrl+C）

## 易错点
- kill -9 是最后手段，可能导致数据丢失
- 先尝试正常终止（kill），再使用强制终止（kill -9）
- 有些进程不能直接杀死，需要加 `-9` 参数强制结束
- 需要配合 ps 命令查找进程号（PID）

## 实战示例
```bash
# 查找进程
ps aux | grep nginx

# 正常终止
kill 9133

# 强制终止
kill -9 9133

# 重新加载配置
kill -HUP $(cat /var/run/nginx.pid)

# 根据进程名终止
pkill -f "python script.py"
killall nginx
```
