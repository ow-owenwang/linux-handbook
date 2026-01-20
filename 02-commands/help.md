# 查看帮助文档

## 常用场景
- 查看命令用法
- 学习命令参数
- 查找命令说明

## help 命令

### 功能
`help` 命令用于显示 shell 内部命令的帮助信息。`help` 命令只能显示 shell 内部的命令帮助信息。而对于外部命令的帮助信息只能使用 `man` 或者 `info` 命令查看。

### 命令格式
```bash
help [-dms] [PATTERN...]
```

### 选项说明
- `-d`: 输出每个命令的简短描述
- `-m`: 以类似于 man 手册的格式描述命令
- `-s`: 只显示命令使用格式

### 使用示例
```bash
# 查看 help 自身的帮助信息
help help

# 查看 help 命令的简短描述
help -d help
# 输出: help - Display information about builtin commands.

# 查看 help 和 cd 命令使用格式
help -s help cd
# 输出:
# help: help [-dms] [pattern ...]
# cd: cd [-L|[-P [-e]]] [dir]
```

## --help 选项

### 功能
绝大多数命令都可以使用 `--help` 选项来查看帮助，这也是一种获取帮助的方法。例如 `ls --help`，这种方法非常简单，输出的帮助信息基本上是 `man` 命令的信息简要版。

### 使用方法
```bash
command --help
```

### 示例
```bash
ls --help              # 查看 ls 命令的用法
grep --help            # 查看 grep 命令的用法
```

### 特点
- 快速查看命令的基本用法
- 不是所有命令都支持
- 通常显示简要的参数说明

## man 命令

### 功能
man 是 Linux 提供的一个手册，包含了绝大部分的命令、函数使用说明。

### 使用格式
```bash
man [选项] 命令名
```

### 手册章节
该手册分成很多章节（section），使用 man 时可以指定不同的章节来浏览不同的内容。

man 中各个 section 意义如下：

| 章节 | 说明 |
|------|------|
| 1 | Standard commands（标准命令） |
| 2 | System calls（系统调用，如 open, write） |
| 3 | Library functions（库函数，如 printf, fopen） |
| 4 | Special devices（设备文件的说明，/dev 下各种设备） |
| 5 | File formats（文件格式，如 passwd） |
| 6 | Games and toys（游戏和娱乐） |
| 7 | Miscellaneous（杂项、惯例与协定等，例如 Linux 档案系统、网络协定、ASCII 码；environ 全局变量） |
| 8 | Administrative Commands（管理员命令，如 ifconfig） |

### 使用方法
```bash
man ls                  # 查看 ls 命令的说明
man 1 ls                # 指定查看第 1 个 section（标准命令）
man printf              # 查看 printf（可能是命令）
man 3 printf            # 查看 printf 函数（库函数）
```

### 指定章节的重要性
实际上，我们不用指定第几个章节也可以查看，如 `man ls`。但是，有这样一种情况，假如命令的名字和函数的名字刚好重名（如：printf），它既是命令，也可以是库函数，如果我们不指定章节号，`man printf`，它只查看命令的用法，不会查询函数的用法，因为 man 是按照手册的章节号的顺序进行搜索的。

**所以，使用 man 手册时，最好指定章节号。**

### man 交互式操作
man 设置了如下的功能键：

| 功能键 | 功能 |
|--------|------|
| 上箭头 | 向上移动一行 |
| 下箭头 | 向下移动一行 |
| PgUP | 向上翻一页 |
| PgDn | 向下翻一页 |
| 空格键 | 显示手册页的下一屏 |
| Enter 键 | 一次滚动手册页的一行 |
| b | 回滚一屏 |
| f | 前滚一屏 |
| g | 移动到第一页 |
| G | 移动到最后一页 |
| q | 退出 man 命令 |
| h | 列出所有功能键 |
| /字符串 | 从当前向下搜索字符串 |
| ?字符串 | 从当前向上搜索字符串 |
| n | 当搜索字符串时，可以用 n 键找到下一个字符串 |
| N | 当搜索字符串时，使用 N 键反向查询字符串。也就是说，如果使用"/字符串"方式搜索，则 N 键表示向上搜索字符串；如果使用"?字符串"方式搜索，则 N 键表示向下搜索字符串 |

### man 手册的格式
man 手册通常包含以下部分：

- **NAME**: 命令名称及功能简要说明
- **SYNOPSIS**: 用法说明，包括可用的选项
  - `[ ]`: 可选内容
  - `< >`: 必选内容
  - `a | b`: 二选一
  - `{ }`: 分组
  - `...`: 同一内容可出现多次
- **DESCRIPTION**: 命令功能的详细说明，可能包括每一个选项的意义
- **OPTIONS**: 说明每一项的意义
- **EXAMPLES**: 使用示例
- **FILES**: 此命令相关的配置文件
- **AUTHOR**: 作者
- **COPYRIGHT**: 版本信息

### 示例
```bash
# 查看标准命令
man 1 ls

# 查看系统调用
man 2 open

# 查看库函数
man 3 printf

# 查看文件格式
man 5 passwd

# 查看管理员命令
man 8 ifconfig
```

## 其他帮助方式

### info 命令
```bash
info command            # 查看命令的详细信息（通常比 man 更详细）
```

### whatis 命令
```bash
whatis command          # 显示命令的简短描述
```

### apropos 命令
```bash
apropos keyword         # 搜索包含关键字的命令
```

## 易错点
- `--help` 不是所有命令都支持
- man 需要指定章节号才能准确查找（特别是命令和函数重名时）
- 使用 `q` 退出 man，不是 Ctrl+C

## 实战示例
```bash
# 使用 --help
ls --help
grep --help

# 使用 man
man ls
man 1 ls
man 3 printf

# 搜索帮助
apropos network
whatis ls
```
