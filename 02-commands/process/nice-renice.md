# nice / renice

## 常用场景
- 调整进程优先级
- 控制 CPU 使用

## 常用命令
```bash
nice -n 10 command
renice 10 PID
```

## 优先级说明
- nice 值范围：-20 到 19
- 值越小优先级越高
- 默认 nice 值为 0

## 易错点
- 普通用户只能提高 nice 值（降低优先级）
- root 可以设置任意 nice 值

## 实战示例
```bash
nice -n 19 backup.sh
renice -5 1234
```
