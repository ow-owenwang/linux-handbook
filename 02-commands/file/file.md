# file

## 常用场景
- 确定文件类型
- 查看文件格式
- 文件类型识别

## 功能
获取文件类型。Linux 系统文件类型不是根据文件扩展名分类的，通过 file 命令可以确认文件具体类型。

## 常用命令
```bash
file filename            # 查看文件类型
file a.c                 # 查看 C 源文件类型
file index.html          # 查看 HTML 文件类型
file pass.cgi            # 查看 CGI 脚本类型
file *                   # 查看当前目录所有文件类型
```

## 输出说明
file 命令会显示文件的类型信息，例如：
- ASCII text
- C source
- HTML document
- executable
- directory
- 等等

## 易错点
- Linux 文件类型不依赖扩展名
- 即使文件没有扩展名，file 也能识别类型
- 某些文件可能显示为 "data" 或 "binary"

## 实战示例
```bash
# 查看单个文件
file script.sh
file image.jpg
file document.pdf

# 查看多个文件
file *.txt
file *

# 查看可执行文件
file /usr/bin/ls
file /bin/bash
```
