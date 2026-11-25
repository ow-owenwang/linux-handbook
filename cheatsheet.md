# Linux 速查表

## 文件
```bash
ls -lh                    # 列出文件（人类可读）
du -sh *                  # 查看目录大小
find . -name "*.log"      # 查找文件
```

## 进程
```bash
pgrep -af xxx             # 按名称查找进程（Linux）
kill PID                  # 先发送 TERM，允许进程清理
kill -KILL PID            # 确认无法正常退出时再强制终止
top                       # 实时查看进程
```

## 网络
```bash
ss -lntp                  # 查看监听端口
curl -I url               # 查看 HTTP 头
netstat -an | grep ESTABLISHED
```

## 包管理
```bash
apt update && apt upgrade  # Debian/Ubuntu
sudo dnf install package  # 较新的 RHEL 系；旧系统可能用 yum
```

## 系统信息
```bash
df -h                     # 磁盘使用
free -h                   # 内存使用
uname -a                  # 系统信息
```

## 文本处理
```bash
grep "pattern" file       # 搜索
sed 's/old/new/g' file    # 替换
awk '{print $1}' file     # 提取字段
```

## 权限
```bash
chmod 755 file            # 修改权限
chown user:group file     # 修改所有者
```

## 服务管理
```bash
systemctl start service   # 启动服务
systemctl status service  # 查看状态
systemctl enable service  # 开机自启
```

## Vim
```bash
i                         # 插入模式
Esc                       # 返回普通模式
:wq                       # 保存退出
dd                        # 删除行
yy                        # 复制行
p                         # 粘贴
```

## 压缩解压
```bash
tar -czf archive.tar.gz dir/    # 压缩
tar -xzf archive.tar.gz         # 解压
```
