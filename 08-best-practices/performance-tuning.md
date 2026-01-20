# 性能调优

## 常用场景
- 系统性能优化
- 应用性能调优

## 调优方向
- CPU: 进程优先级、CPU 亲和性
- 内存: swap 配置、内存限制
- I/O: 文件系统、磁盘调度
- 网络: 内核参数、连接数

## 常用工具
- `sysctl`: 内核参数
- `ulimit`: 资源限制
- `nice/renice`: 进程优先级

## 实战示例
```bash
sysctl -w vm.swappiness=10
ulimit -n 65535
```
