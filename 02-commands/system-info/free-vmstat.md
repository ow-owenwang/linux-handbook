# free / vmstat

## 常用场景
- 查看内存使用
- 监控系统性能

## 常用命令
```bash
free -h
vmstat 1
vmstat 1 5
```

## 常用参数
- free: -h 人类可读, -m MB 单位
- vmstat: 间隔 次数

## 实战示例
```bash
free -h
vmstat 1 10
```
