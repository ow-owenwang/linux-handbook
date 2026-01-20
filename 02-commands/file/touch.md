# touch

## 常用场景
- 创建空文件
- 修改文件时间戳
- 批量创建文件

## 功能
`touch` 命令用于修改文件或者目录的时间属性，包括存取时间和更改时间。若文件不存在，系统会建立一个新的文件。

## 命令格式
```bash
touch [OPTION]… FILE…
```

## 常用参数
- `-a`: 只更改访问时间
- `-m`: 只更改修改时间
- `-c`: 不创建任何文件
- `-d`: 使用指定的时间字符串
- `-r`: 使用参考文件的时间

## 常用场景

### 创建不存在的文件
```bash
touch demo.log              # 创建空文件 demo.log
touch file1.txt file2.txt   # 创建多个空文件
```

### 修改文件的末次访问时间
```bash
touch existing_file         # 更新文件的时间戳为当前时间
touch -d "2022-05-20 20:52:18" file  # 设置指定时间
```

## 实战示例
```bash
# 创建新文件
touch demo.log
ls -l demo.log

# 创建多个文件
touch file1.txt file2.txt file3.txt

# 更新时间戳
touch existing_file

# 使用参考文件的时间
touch -r reference.txt target.txt
```

## 延伸阅读
- [cp-mv-rm.md](./cp-mv-rm.md) - 文件复制和移动
- [ls.md](./ls.md) - 查看文件信息
