# tar / gzip / bzip2 / zip

## 常用场景
- 打包压缩文件
- 解压文件
- 备份数据

## tar 命令

### 功能
计算机中的数据经常需要备份，tar 是 Unix/Linux 中最常用的备份工具，此命令可以把一系列文件归档到一个大文件中，也可以把档案文件解开以恢复数据。

**注意**：tar 这个命令并没有压缩的功能，它只是一个打包的命令，但是在 tar 命令中增加选项可以调用压缩工具实现压缩功能。

### 使用格式
```bash
tar [参数] 打包文件名 文件
```

### 常用参数
- `-c`: 生成档案文件，创建打包文件
- `-v`: 列出归档解档的详细过程，显示进度
- `-f`: 指定档案文件名称，f 后面一定是 .tar 文件，所以必须放选项最后
- `-t`: 列出档案中包含的文件
- `-x`: 解开档案文件
- `-z`: 指定压缩包的格式为 file.tar.gz（调用 gzip）
- `-j`: 指定压缩包的格式为 file.tar.bz2（调用 bzip2）
- `-C`: 解压到指定目录（大写字母 C）

### 注意事项
- 除了 f 需要放在参数的最后，其它参数的顺序任意
- tar 命令很特殊，其参数前面可以使用 `-`，也可以不使用

## gzip 命令

### 功能
tar 与 gzip 命令结合使用实现文件打包、压缩。tar 只负责打包文件，但不压缩，用 gzip 压缩 tar 打包后的文件，其扩展名一般用 `xxxx.tar.gz`。

### 使用格式
```bash
gzip [选项] 被压缩文件
```

### 常用选项
- `-d`: 解压
- `-r`: 压缩所有子目录

### tar + gzip 组合

#### 压缩用法
```bash
tar cvzf 压缩包包名 文件1 文件2 ...
tar zcvf test.tar.gz 1.c 2.c 3.c 4.c    # 把 1.c 2.c 3.c 4.c 压缩成 test.tar.gz
```

#### 解压用法
```bash
tar zxvf 压缩包包名
tar zxvf test.tar.gz
```

#### 解压到指定目录
```bash
tar -xvf new.tar.gz -C ./test/          # 将 new.tar.gz 解压到当前目录下的 test 目录下
```

## bzip2 命令

### 功能
tar 与 bzip2 命令结合使用实现文件打包、压缩（用法和 gzip 一样）。tar 只负责打包文件，但不压缩，用 bzip2 压缩 tar 打包后的文件，其扩展名一般用 `xxxx.tar.bz2`。

### tar + bzip2 组合

#### 压缩用法
```bash
tar cjvf 压缩包包名 文件...
tar jcvf bk.tar.bz2 *.c
```

#### 解压用法
```bash
tar xjvf 压缩包包名
tar jxvf bk.tar.bz2
```

## zip / unzip 命令

### 功能
通过 zip 压缩文件的目标文件不需要指定扩展名，默认扩展名为 zip。

### 压缩文件
```bash
zip [-r] 目标文件(没有扩展名) 源文件
zip -r archive.zip dir/              # 递归压缩目录
```

### 解压文件
```bash
unzip -d 解压后目录文件 压缩文件
unzip archive.zip                    # 解压到当前目录
unzip -d /tmp archive.zip            # 解压到指定目录
```

### 常用参数
- `-r`: 递归压缩目录

## 压缩格式对比

| 格式 | 命令 | 扩展名 | 特点 |
|------|------|--------|------|
| tar | `tar cvf` | .tar | 只打包，不压缩 |
| gzip | `tar zcvf` | .tar.gz 或 .tgz | 压缩比中等，速度快 |
| bzip2 | `tar jcvf` | .tar.bz2 | 压缩比高，速度较慢 |
| zip | `zip -r` | .zip | 跨平台，Windows 兼容 |

## 易错点
- tar 参数顺序：f 必须放在最后
- 压缩时注意排除不需要的文件
- 解压到指定目录使用 `-C`（大写）
- zip 目标文件不需要指定扩展名

## 实战示例
```bash
# tar 打包
tar cvf archive.tar dir/

# gzip 压缩
tar zcvf backup-$(date +%Y%m%d).tar.gz /var/www
tar zxvf backup.tar.gz
tar zxvf backup.tar.gz -C /tmp

# bzip2 压缩
tar jcvf backup.tar.bz2 *.c
tar jxvf backup.tar.bz2

# zip 压缩
zip -r archive.zip dir/
unzip archive.zip
unzip -d /tmp archive.zip
```
