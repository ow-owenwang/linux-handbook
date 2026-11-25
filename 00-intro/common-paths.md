# 常用路径

## 常用场景
- 快速查找配置文件位置
- 理解系统目录结构

## 重要目录

### /etc
- 配置文件
- 主要存放主机相关配置；个别配置目录也可能包含脚本
- systemd、nginx、OpenSSH 的系统配置通常在这里，具体路径依发行版和安装方式而异

### /var
- 经常变化的数据
- log / spool / cache

### /usr
- 用户空间程序
- /usr/bin / /usr/lib

### /home
- 用户主目录

### /tmp
- 临时文件

### /opt
- 可选软件包

### /root
- root 用户主目录

## 延伸阅读
- [../01-filesystem/directory-structure.md](../01-filesystem/directory-structure.md)
