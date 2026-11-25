# chown / chmod / chgrp / umask

## 常用场景
- 修改文件所有者
- 修改文件权限
- 修改文件所属组
- 设置默认权限掩码

## chmod 命令

### 功能
修改文件权限。chmod 修改文件权限有两种使用格式：字母法与数字法。

### 字母法

#### 使用格式
```bash
chmod u/g/o/a +/-/= rwx 文件
```

#### 用户类别
- `u` (user): 表示该文件的所有者
- `g` (group): 表示与该文件的所有者属于同一组(group)者，即用户组
- `o` (other): 表示其他以外的人
- `a` (all): 表示这三者皆是

#### 操作符
- `+`: 增加权限
- `-`: 撤销权限
- `=`: 设定权限

#### 权限类型
- `r` (read): 表示可读取
  - 对于一个目录，如果没有 r 权限，那么就意味着不能通过 ls 查看这个目录的内容
- `w` (write): 表示可写入
  - 对于一个目录，如果没有 w 权限，那么就意味着不能在目录下创建新的文件
- `x` (execute): 表示可执行
  - 对于一个目录，如果没有 x 权限，那么就意味着不能通过 cd 进入这个目录

#### 字母法示例
```bash
chmod o+w file          # 给文件 file 的其它用户增加写权限
chmod u-r file          # 给文件 file 的拥有者减去读的权限
chmod g=x file          # 设置文件 file 的同组用户的权限为可执行，同时去除读、写权限
chmod u+x file          # 给文件所有者增加执行权限
```

### 数字法

#### 权限数字
"rwx" 这些权限也可以用数字来代替：

| 权限 | 数字代号 |
|------|----------|
| r (读取权限) | 4 |
| w (写入权限) | 2 |
| x (执行权限) | 1 |
| - (不具任何权限) | 0 |

#### 数字法示例
```bash
# chmod u=rwx,g=rx,o=r filename 等价于：
chmod 754 filename

chmod 751 file          # 文件所有者：读、写、执行权限(7)
                        # 同组用户：读、执行的权限(5)
                        # 其它用户：执行的权限(1)

chmod 777 file          # 所有用户拥有读、写、执行权限

chmod 755 file          # 所有者：rwx，同组和其他：rx
chmod 644 file          # 所有者：rw-，同组和其他：r--
```

#### 常用权限组合
- `777`: rwxrwxrwx (所有用户所有权限)
- `755`: rwxr-xr-x (所有者所有权限，其他用户读和执行)
- `644`: rw-r--r-- (所有者读写，其他用户只读)
- `600`: rw------- (只有所有者读写)

### 递归修改权限
`-R` 会递归修改目录及其中的文件。文件和目录通常不应一律设置相同权限；`777` 会向所有用户开放写入权限。

```bash
find directory -type d -exec chmod 755 {} +  # 目录可遍历
find directory -type f -exec chmod 644 {} +  # 普通文件不额外授予执行权限
```

## chown 命令

### 功能
修改文件所有者。

### 使用格式
```bash
chown 用户名 文件或目录名
chown 用户名:组名 文件或目录名
```

### 常用命令
```bash
chown username file      # 修改文件所有者
chown user:group file    # 同时修改所有者和所属组
chown -R user:group dir  # 递归修改目录
```

### 常用参数
- `-R`: 递归修改目录及其子文件

## chgrp 命令

### 功能
修改文件所属组。

### 使用格式
```bash
chgrp 用户组名 文件或目录名
```

### 常用命令
```bash
chgrp groupname file     # 修改文件所属组
chgrp -R groupname dir   # 递归修改目录
```

### 常用参数
- `-R`: 递归修改目录及其子文件

## umask 命令

### 功能
设置默认权限掩码。

### 常用命令
```bash
umask 022                # 设置默认掩码
umask                    # 查看当前掩码
```

新建普通文件通常以 `666` 为基础，新建目录通常以 `777` 为基础，再屏蔽 umask 中的位。例如 `umask 022` 通常得到文件 `644`、目录 `755`；创建程序不会仅因 umask 而自动获得执行位。

## 常用参数
- `chmod`: `-R` 递归
- `chown`: `-R` 递归
- `chgrp`: `-R` 递归

## 易错点
- 数字权限：755 = rwxr-xr-x
- umask 是掩码，不是权限值
- 目录需要 x 权限才能进入
- 递归修改权限要谨慎，可能影响大量文件

## 实战示例
```bash
# 修改权限（字母法）
chmod u+x script.sh
chmod o+w file.txt
chmod g=r file.txt

# 修改权限（数字法）
chmod 755 script.sh
chmod 644 config.conf
find test -type d -exec chmod 755 {} +
find test -type f -exec chmod 644 {} +

# 修改所有者
chown username file
chown user:group file
chown -R www-data:www-data /var/www

# 修改所属组
chgrp groupname file
chgrp -R groupname directory
```
