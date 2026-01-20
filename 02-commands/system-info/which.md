# which

## 常用场景
- 查找命令位置
- 查看命令路径
- 确认命令是否存在

## 功能
查看命令位置。which 命令用于查找并显示给定命令的绝对路径。

## 常用命令
```bash
which command            # 查找命令位置
which ls                 # 查找 ls 命令位置
which python             # 查找 python 命令位置
which -a command         # 显示所有匹配的路径
```

## 常用参数
- `-a`: 显示所有匹配的路径（如果有多个同名命令）

## 输出说明
which 命令会显示命令的完整路径，例如：
- `/usr/bin/ls`
- `/usr/bin/python3`
- 如果命令不存在，不输出任何内容

## 易错点
- which 只查找 PATH 环境变量中的命令
- 某些内置命令（如 cd）可能找不到
- 如果命令不在 PATH 中，which 找不到

## 实战示例
```bash
# 查找命令
which ls
which python
which nginx

# 查找所有匹配
which -a python

# 检查命令是否存在
which command && echo "Found" || echo "Not found"
```

## 相关命令
- `whereis`: 查找命令、源文件和手册页
- `locate`: 通过数据库查找文件
- `find`: 实时查找文件
