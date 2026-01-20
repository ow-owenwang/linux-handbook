# iostat / sar

## 常用场景
- 监控 I/O 性能
- 系统性能分析

## 常用命令
```bash
iostat -x 1
sar -u 1 10
sar -d 1 10
```

## 常用参数
- iostat: -x 详细信息, 间隔
- sar: -u CPU, -d 磁盘, -r 内存

## 易错点
- sar 需要 sysstat 包
- 需要 root 权限

## 实战示例
```bash
iostat -x 1
sar -u 1 60
```
