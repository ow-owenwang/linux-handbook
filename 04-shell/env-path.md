# 环境变量和 PATH

## 常用场景
- 设置环境变量
- 配置 PATH
- 理解环境变量作用域

## 常用命令
```bash
echo $PATH
export VAR=value
export PATH=$PATH:/new/path
```

## 配置文件
- `~/.bashrc`: 用户 bash 配置
- `~/.bash_profile`: 登录配置
- `/etc/profile`: 系统配置

## 易错点
- export 只在当前 shell 有效
- 永久修改需要写入配置文件

## 实战示例
```bash
export JAVA_HOME=/usr/lib/jvm/java-8
export PATH=$PATH:$JAVA_HOME/bin
```
