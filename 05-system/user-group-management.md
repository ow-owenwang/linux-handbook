# 用户和组管理

## 常用场景
- 创建用户
- 修改用户属性
- 管理用户组
- 系统用户管理

## 用户管理概述

### 用户的重要性
- 用户是 Unix/Linux 系统工作中重要的一环，用户管理包括用户与组账号的管理
- 在 Unix/Linux 系统中，不论是由本机或是远程登录系统，每个系统都必须拥有一个账号，并且对于不同的系统资源拥有不同的使用权限

### root 账号
- Unix/Linux 系统中的 root 账号通常用于系统的维护和管理
- 它对 Unix/Linux 操作系统的所有部分具有不受限制的访问权限
- 在大多数版本的 Unix/Linux 中，都不推荐直接使用 root 账号登录系统

### 标准用户
- 在 Unix/Linux 安装的过程中，系统会自动创建许多用户账号
- 这些默认的用户就称为"标准用户"

## 查看用户信息

### whoami
查看当前系统当前账号的用户名。

```bash
whoami                    # 查看当前用户名
cat /etc/passwd           # 查看系统用户信息
```

**使用场景**：系统管理员通常需要使用多种身份登录系统，例如通常使用普通用户登录系统，然后再以 su 命令切换到 root 身份对系统进行管理。这时候就可以使用 whoami 来查看当前用户的身份。

### who
查看当前所有登录系统的用户信息。

```bash
who                       # 查看所有登录用户
who -m                    # 只显示运行 who 命令的用户信息
who -q                    # 只显示用户的登录账号和登录用户的数量
who -u                    # 在登录时间后显示该用户最后一次操作到当前的时间间隔
```

**常用选项**：
- `-m` 或 `am I`: 只显示运行 who 命令的用户名、登录终端和登录时间
- `-q` 或 `--count`: 只显示用户的登录账号和登录用户的数量
- `-u`: 在登录时间后显示该用户最后一次操作到当前的时间间隔
- `-u` 或 `--heading`: 显示列标题

### w
查看登录当前系统的用户信息。与 who 命令相比，w 命令的功能更强大，它不但可以显示当前有哪些用户登录到系统，还可以显示这些用户正在进行的操作，并给出更加详细和科学的统计数据。

```bash
w                         # 显示所有登录用户信息
w username                # 只显示指定用户的信息
w -h                      # 不显示标题
w -s                      # 使用短列表，不显示用户登录时间、JCPU 和 PCPU 时间
```

**使用格式**：
```bash
w [选项] [用户名]
```

如果 w 命令携带用户名，则只显示指定用户的信息，否则显示当前所有登录用户的信息。

**常用选项**：
- `-h`: 不显示标题
- `-l`: 显示详细信息列表，此为预设值
- `-s`: 使用短列表，不显示用户登录时间、JCPU 和 PCPU 时间
- `-u`: 忽略执行程序的名称，以及该程序的 PCPU 时间

### last
查询用户登录情况。不管是哪位用户从哪里登录，管理员都可以通过 last 命令查出，以及是否有人非法登录。

```bash
last                      # 查看所有登录记录
last username             # 查看指定用户的登录记录
```

## 切换用户

### su
可以通过 su 命令切换用户。

```bash
su                       # 切换到 root 用户
su root                  # 切换到 root 用户
su -                     # 切换到 root 用户，同时切换目录到 /root
su - root                # 切换到 root 用户，同时切换目录到 /root
su username              # 切换到普通用户
su - username            # 切换到普通用户，同时切换普通用户所在的目录
```

**su 和 su - 的区别**：
- `su`: 切换到对应的用户，但保持当前工作目录
- `su -`: 切换到对应的用户时会将当前的工作目录自动转换到切换后的用户主目录

**Ubuntu 平台注意**：
- 如果是 ubuntu 平台，需要在命令前加 `sudo`
- 如果在某些操作需要管理员才能操作，ubuntu 无需切换到 root 用户即可操作，只需加 `sudo` 即可
- sudo 是 ubuntu 平台下允许系统管理员让普通用户执行一些或者全部的 root 命令的一个工具，减少了 root 用户的登陆和管理时间，提高了安全性

### exit
退出登录账户。

- 如果是图形界面，退出当前终端
- 如果是使用 ssh 远程登录，退出登陆账户
- 如果是切换后的登陆用户，退出则返回上一个登陆账号

```bash
exit                     # 退出当前登录
```

## 添加用户账号

### useradd
在 Unix/Linux 中添加用户账号可以使用 `adduser` 或 `useradd` 命令，因为 adduser 命令是指向 useradd 命令的一个链接，因此，这两个命令的使用格式完全一样。

**使用格式**：
```bash
useradd [参数] 新建用户账号
```

**常用参数**：
- `-d <dirname>`: 指定用户登录系统时的主目录，如果不使用该参数，系统自动在 /home 目录下建立与用户名同名目录为主目录
- `-m`: 自动建立目录
- `-g`: 指定组名称

**相关说明**：
- Linux 每个用户都要有一个主目录，主目录就是第一次登陆系统，用户的默认当前目录(/home/用户)
- 每一个用户必须有一个主目录，所以用 useradd 创建用户的时候，一定给用户指定一个主目录
- 用户的主目录一般要放到根目录的 home 目录下，用户的主目录和用户名是相同的
- 如果创建用户的时候，不指定组名，那么系统会自动创建一个和用户名一样的组名

**常用命令**：
```bash
useradd -d /home/abc abc -m        # 创建 abc 用户，如果 /home/abc 目录不存在，就自动创建这个目录，同时用户属于 abc 组
useradd -d /home/a a -g test -m    # 创建一个用户名字叫 a，主目录在 /home/a，如果主目录不存在，就自动创建主目录，同时用户属于 test 组
cat /etc/passwd                    # 查看系统当前用户名
```

## 设置用户密码

### passwd
在 Unix/Linux 中，超级用户可以使用 passwd 命令为普通用户设置或修改用户口令。用户也可以直接使用该命令来修改自己的口令，而无需在命令后面使用用户名。

```bash
passwd                  # 修改当前用户密码
passwd username         # 修改指定用户密码（需要 root 权限）
```

### 修改 root 账号密码
```bash
# 方法1：使用 sudo（Ubuntu）
sudo passwd

# 方法2：切换到 root 账号后修改
su
passwd
```

## 删除用户

### userdel
删除用户账号。

```bash
userdel username        # 删除用户，但不会自动删除用户的主目录
userdel -r username    # 删除用户，同时删除用户的主目录
```

**常用参数**：
- `-r`: 删除用户主目录

## 组管理

### groupadd
新建组账号。

```bash
groupadd groupname      # 创建新组
```

### groupdel
删除组账号。

```bash
groupdel groupname     # 删除组
```

### 查看组信息
```bash
cat /etc/group         # 查看用户组
```

## 修改用户组

### usermod
修改用户所在组。

```bash
usermod -g 用户组 用户名
usermod -aG 用户组 用户名    # 追加到组（不删除原有组）
```

**常用参数**：
- `-g`: 修改用户的主组
- `-aG`: 追加用户到附加组（不删除原有组）

## 相关文件
- `/etc/passwd`: 用户信息
- `/etc/group`: 组信息
- `/etc/shadow`: 密码信息

## 切换用户注意事项

### su 和 su - 的区别
```bash
su root              # 切换到 root 用户，但不会模拟登录该用户的环境
                     # 这意味着你会切换到 root 身份，但环境变量、工作目录等设置将保持与之前的用户相同

su - root            # 启动一个新的登录会话，加载 root 用户的环境变量、工作目录等设置
                     # 使用短横线可以确保你以 root 用户的完整环境开始工作
```

### 切换用户规则
- 从权限高的用户切换到权限低的用户，不需要输入密码
- 从权限低的用户切换到权限高的用户，需要输入密码
- 当需要返回到原来用户时，使用 `exit` 或 `logout` 指令

## sudo 命令

### 功能
`sudo` 是"以超级用户权限执行（superuser do）"的缩写。`sudo` 命令允许授权用户以超级用户（通常是 root）的权限执行特定命令。

### 与 su 的区别
- **权限需求**：`su` 需要知道目标用户的密码，而 `sudo` 需要知道当前用户的密码
- **权限范围**：`su` 切换到目标用户后，拥有的权限是完全的，相当于目标用户的权限；而 `sudo` 执行的命令可能只是特定命令以 root 权限执行，执行完该命令后会回到普通用户权限
- **安全性**：`sudo` 提供了更多控制权限的灵活性，而且在日常管理中更为安全

### 配置 sudo
可以通过编辑 `sudo` 的配置文件来限制特定用户可以执行的命令范围。`sudo` 的配置文件通常位于 `/etc/sudoers` 或者 `/etc/sudoers.d` 目录下。

**重要提示**：在编辑这些文件之前，请务必使用 `visudo` 命令来避免在编辑过程中造成配置文件损坏。

### 限制用户执行特定命令
例如，假设要限制用户 `example_user` 只能执行 `/bin/ls` 和 `/usr/bin/apt-get update` 这两个命令：

```bash
# 使用 visudo 编辑 sudoers 文件
sudo visudo

# 在文件中添加如下行
example_user ALL=(ALL) /bin/ls, /usr/bin/apt-get update
```

上面的配置指定了 `example_user` 在任何主机上，以任何用户身份（ALL）可以使用 `sudo` 执行 `/bin/ls` 和 `/usr/bin/apt-get update` 这两个命令。

### Ubuntu 平台
如果是 ubuntu 平台，需要在命令前加 `sudo`。如果在某些操作需要管理员才能操作，ubuntu 无需切换到 root 用户即可操作，只需加 `sudo` 即可。sudo 是 ubuntu 平台下允许系统管理员让普通用户执行一些或者全部的 root 命令的一个工具，减少了 root 用户的登陆和管理时间，提高了安全性。

## 查看用户 ID
```bash
id root               # 查看 root 用户的 ID 信息
id username           # 查看指定用户的 ID 信息
id                    # 查看当前用户的 ID 信息
```

## 实战示例
```bash
# 查看当前用户
whoami
id

# 查看登录用户
who
w

# 切换用户
su root              # 切换到 root，保持当前环境
su - root            # 切换到 root，加载完整环境
su - username         # 切换到普通用户

# 使用 sudo
sudo command          # 以 root 权限执行命令

# 创建用户
useradd -d /home/abc abc -m
useradd -d /home/a a -g test -m
useradd test -d /home/t1

# 设置密码
passwd username
passwd abc

# 删除用户
userdel abc           # 删除用户，保留家目录
userdel -r abc        # 删除用户以及用户主目录（一般建议保留家目录）

# 组管理
groupadd public       # 创建组
useradd u1 -g public  # 创建用户指定组
groupdel public       # 删除组（如果该组有用户成员，必须先删除用户才能删除组）

# 修改用户组
usermod -g testgroup username

# 查看用户信息
cat /etc/passwd       # 用户文件
cat /etc/shadow       # 密码文件
cat /etc/group        # 组信息文件
```
