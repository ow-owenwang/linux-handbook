# cat / less / more

## 常用场景
- 查看文件内容
- 查看日志
- 合并文件内容
- 分屏显示长文件

## cat 命令

### 功能
查看或者合并文件内容。`cat` 看完文件内容，一次显示所有的内容，适合查看内容较少的文本文件。

### 命令格式
```bash
cat [选项] fileName
```

### 常用参数
- `-n` 或 `--number`: 由 1 开始对所有输出的行数编号
- `-b` 或 `--number-nonblank`: 和 `-n` 相似，只不过对于空白行不编号

### 常用命令
```bash
cat file                    # 查看文件内容
cat file1 file2             # 查看多个文件
cat file1 file2 > file3     # 合并文件内容
cat -n file                 # 显示行号
cat -b file                 # 显示行号（空白行不编号）
```

## more 命令

### 功能
分屏显示文件内容。`more` 命令是常用的文本文件阅读工具，类似于 `cat`，不过以一页一页的形式显示，更方便使用者逐页阅读。一般文件过大时使用 `more` 浏览，文件较小时使用 `cat`。

### 命令格式
```bash
more [OPTIONS] FILE [...]
```

### 常用参数
- `-NUM`: 指定每屏显示的行数为 NUM
- `+/STRING`: 从匹配搜索字符串 STRING 所在行的前两行开始显示
- `+NUM`: 从文件第 NUM 行开始显示

### 常用命令
```bash
more file
more -10 file              # 每屏显示 10 行
more +20 file               # 从第 20 行开始显示
more +/search file          # 从包含 "search" 的行开始显示
ls -alh | more             # 通过管道分屏显示
```

### 交互操作
- **回车键**: 向下滚动一行
- **空格键 (Space)**: 显示下一页
- **b 键 (back)**: 回显上一页
- **q 或 Q 键**: 退出

## less 命令

### 功能
`less` 命令是常用的文本文件阅读工具，类似于 `more`，是加强版的 `more` 命令。`less` 主要用于浏览大文件，加载文件时不会读取整个文件，相比于 `vim` 或 `nano` 等文本编辑器，启动会更快。

### 命令格式
```bash
less [OPTIONS] [FILE]...
```

### 常用参数
- `-m`: 显示类似 more 命令的百分比
- `-N`: 显示每行的行号

**注意**：`less` 的命令行选项很少使用，浏览文件时常用的是交互式命令。

### 常用命令
```bash
less file
less -N file               # 显示行号
less -m file               # 显示百分比
```

### 交互操作
- **b**: 向后翻一页
- **空格键**: 滚动一页
- **回车键**: 滚动一行
- **Q**: 退出 less 命令
- **/字符串**: 向下搜索字符串
- **?字符串**: 向上搜索字符串
- **g**: 移动到第一页
- **G**: 移动到最后一页

## tail 命令

### 功能
`tail` 命令用于显示文件尾部内容，与命令 `head` 作用相反。默认情况下，显示文件的末尾 10 行内容。

### 命令格式
```bash
tail [OPTION]... [FILE]...
```

可以指定多个文件 FILE，这种情况下，输出的内容前会列出所属文件名。如果未给定 FILE 或者 FILE 是 `-`，则从标准输入读取。

### 常用参数
- `-f`: 按照指定时间间隔输出文件追加的内容（常用于监控日志）
- `-n N` 或 `-N`: 输出最后 N 行，而非默认的最后 10 行

### 常用命令
```bash
tail file                   # 显示文件最后 10 行
tail -f file               # 跟踪文件变化（常用于日志）
tail -n 20 file             # 显示最后 20 行
tail -20 file               # 显示最后 20 行（简写形式）
```

## head 命令

### 功能
`head` 命令用于显示文件开头的内容。在默认情况下，显示文件的头 10 行内容。

### 命令格式
```bash
head [OPTION]... [FILE]...
```

### 常用参数
- `-c, --bytes=[-]K`: 显示每个文件的前 K 字节内容；如果附加 `-` 参数，则显示每个文件最后 K 字节外的所有内容
- `-n, --lines=[-]K`: 显示每个文件的前 K 行内容；如果附加 `-` 参数，则显示每个文件最后 K 行外的所有内容

### 常用命令
```bash
head file                   # 显示文件前 10 行
head -n 20 file             # 显示文件前 20 行
head -20 file               # 显示文件前 20 行（简写形式）
head /etc/passwd            # 显示 /etc/passwd 的前 10 行
```

## 易错点
- cat 不适合大文件，会一次性显示全部内容
- more 只能向下滚动，不能向上
- less 比 more 功能更强，推荐使用
- tail -f 常用于监控日志文件

## 实战示例
```bash
# 查看文件
cat /etc/hosts
cat file1 file2

# 分屏显示
more /var/log/syslog
less /var/log/syslog
ls -alh | more

# 查看日志
tail -f /var/log/nginx/access.log
tail -n 100 /var/log/syslog
```
