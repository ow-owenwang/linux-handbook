# grep

## 常用场景
- 查日志
- 搜索配置项
- 文本搜索

## 功能说明
Linux 系统中 grep 命令是一种强大的文本搜索工具，grep 允许对文本文件进行模式查找。如果找到匹配模式，grep 打印包含模式的所有行。

## 使用格式
```bash
grep [-选项] '搜索内容串' 文件名
```

## 常用命令
```bash
grep "error" app.log
grep -rn "TODO" .
grep -E "pattern1|pattern2" file
grep 'a' 1.txt
```

## 常用参数
- `-i`: 忽略大小写
- `-r`: 递归搜索目录
- `-n`: 显示匹配行及行号
- `-E`: 扩展正则表达式
- `-v`: 显示不包含匹配文本的所有行（相当于求反）

## 注意事项
在 grep 命令中输入字符串参数时，最好用引号或双引号括起来。例如：`grep 'a' 1.txt`。

## grep 正则表达式

### 功能
grep 搜索内容串可以是正则表达式。

正则表达式是对字符串操作的一种逻辑公式，就是用事先定义好的一些特定字符、及这些特定字符的组合，组成一个"规则字符串"，这个"规则字符串"用来表达对字符串的一种过滤逻辑。

### 常用正则表达式

| 参数 | 含义 | 示例 |
|------|------|------|
| `^a` | 行首，搜寻以 a 开头的行 | `grep -n '^a' 1.txt` |
| `ke$` | 行尾，搜寻以 ke 结束的行 | `grep -n 'ke$' 1.txt` |
| `[Ss]igna[Ll]` | 匹配 [] 里中一系列字符中的一个 | `grep -n '[Ss]igna[Ll]' 1.txt` 搜寻匹配单词 signal、signaL、Signal、SignaL 的行 |
| `.` (点) | 匹配一个非换行符的字符 | `grep -n 'e.e' 1.txt` 匹配 e 和 e 之间有任意一个字符，可以匹配 eee，eae，eve，但是不匹配 ee，eaae |

### 正则表达式示例
```bash
# 行首匹配
grep -n '^a' 1.txt

# 行尾匹配
grep -n 'ke$' 1.txt

# 字符组匹配
grep -n '[Ss]igna[Ll]' 1.txt

# 点匹配任意字符
grep -n 'e.e' 1.txt
```

## 易错点
- grep 默认支持基本正则表达式
- `-E` 才是扩展正则表达式
- 搜索字符串最好用引号括起来
- `-v` 参数是反向匹配，显示不包含匹配的行

## 高级用法

### 递归查找
```bash
# 在某个目录下递归查找包含"关键词"的文件
grep -R "关键词" /path/to/dir

# 只显示文件名（不显示具体内容）
grep -R -l "关键词" /path/to/dir

# 忽略二进制文件（更快、更干净）
grep -R -l --binary-files=without-match "关键词" /path/to/dir

# 限定文件类型（比如只查 .txt、.json）
grep -R -l "关键词" /path/to/dir --include="*.txt"
grep -R -l "关键词" /path/to/dir --include="*.json"

# 查找并显示行号（方便定位）
grep -R -n "关键词" /path/to/dir
```

### 替代工具：ripgrep (rg)
如果你安装了 `rg`（速度远超 grep）：

```bash
# 基本搜索
rg "关键词" /path/to/dir

# 只显示文件名
rg -l "关键词" /path/to/dir
```

**安装（macOS）**：
```bash
brew install ripgrep
```

## 实战示例
```bash
# 基本搜索
grep "error" app.log
grep 'a' 1.txt

# 递归搜索
grep -rn "Exception" /var/log
grep -R "关键词" /path/to/dir

# 只显示文件名
grep -R -l "关键词" /path/to/dir

# 忽略大小写
grep -i "error\|warning" app.log

# 反向匹配
grep -v "debug" app.log

# 显示行号
grep -n "error" app.log

# 限定文件类型
grep -R --include="*.txt" "关键词" /path/to/dir
```

## 延伸阅读
- [regex-basics.md](./regex-basics.md) - 正则表达式基础
- [sed.md](./sed.md) - 文本替换
- [wc.md](./wc.md) - 文本统计
