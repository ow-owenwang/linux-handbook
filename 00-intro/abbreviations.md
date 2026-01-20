# Linux 常见缩写

## 常用场景
- 理解命令含义
- 记忆命令名称
- 学习 Linux 术语

## 命令缩写

### 基础命令
- `ls`: list（列出目录内容）
- `cd`: Change Directory（改变目录）
- `pwd`: print work directory（打印当前目录，显示出当前工作目录的绝对路径）
- `su`: switch user（切换用户）
- `rm`: Remove（删除目录或文件）
- `rmdir`: Remove Directory（删除目录）
- `mkdir`: Make Directory（创建目录）
- `mv`: Move file（移动文件）
- `cp`: Copy file（复制文件）
- `cat`: concatenate（连锁，cat file1 file2>>file3 把文件1和文件2的内容联合起来放到file3中）
- `ln`: Link files（链接文件）
- `touch`: 创建空文件或更新时间戳

### 系统命令
- `ps`: process status（进程状态，类似于 windows 的任务管理器）
- `df`: disk free（显示磁盘可用空间数目信息及空间结点信息）
- `du`: Disk usage（显示目录或文件的大小）
- `uname`: Unix name（显示系统信息）
- `man`: Manual（手册、指南）
- `mkfs`: Make file system（创建文件系统）
- `fsck`: File system check（文件系统检查）
- `umount`: Unmount（卸载文件系统）

### 权限命令
- `chown`: Change owner（修改文件所有者）
- `chgrp`: Change group（修改文件所属组）
- `chmod`: Change mode（修改文件权限）
- `umask`: User's MASK（用户权限掩码）

### 进程命令
- `fg`: Foreground（前台）
- `bg`: Background（后台）
- `nohup`: No HangUP（不挂起）

### 包管理
- `rpm`: redhat package manager（红帽子打包管理器）
- `dpkg`: Debian package manager（Debian 包管理器）
- `apt`: Advanced package tool（高级包工具，Debian 或基于 Debian 的发行版中提供）

### 其他命令
- `tar`: Tape archive（磁带归档）
- `dd`: Disk Dump（本来应根据其功能描述"Convert an copy"命名为"cc"，但"cc"已经被用以代表"C Complier"，所以命名为"dd"）
- `ldd`: List dynamic dependencies（列出动态依赖）
- `insmod`: install module（载入模块）
- `lsmod`: List modules（列出模块）
- `rmmod`: Remove module（移除模块）

## 目录缩写

### 系统目录
- `/bin`: BINaries（二进制程序文件）
- `/dev`: DEVices（硬件驱动）
- `/etc`: ETCetera（目录存放着各种系统配置文件，类似于 windows 下的 system）
- `/lib`: LIBrary（库文件）
- `/proc`: PROCesses（进程信息）
- `/sbin`: Superuser BINaries（超级用户二进制文件）
- `/tmp`: TeMPorary（临时文件）
- `/usr`: Unix Shared Resources（Unix 共享资源）
- `/var`: VARiable（可变数据）
- `/boot`: boot（开机启动文件）

### 其他目录
- `/home`: Home（用户主目录）
- `/root`: Root（root 用户主目录）
- `/opt`: Optional（可选软件包）
- `/mnt`: Mount（挂载点）
- `/media`: Media（可移动媒体挂载点）
- `/srv`: Service（服务数据）

## 文件扩展名

### 库文件
- `.a`: Archive，static library（静态库）
- `.so`: Shared object，dynamically linked library（动态链接库）
- `.o`: Object file，complied result of C/C++ source file（目标文件）

### 配置文件
- `rc`（如 .bashrc、.xinitrc 等）: Resource configuration（资源配置）
- `Knnxxx / Snnxxx`（位于 rcx.d 目录下）: K（Kill）；S(Service)；nn（执行顺序号）；xxx（服务标识）

## 系统术语

### 引导相关
- `GRUB`: GRand Unified Bootloader（GRUB 引导加载程序）
- `LILO`: LInux LOader（Linux 加载程序）

### 系统组件
- `FIFO`: First In, First Out（先进先出）
- `IFS`: Internal Field Seperators（内部字段分隔符）
- `VT`: Video Terminal（视频终端）
- `daemon`: Disk And Execution MONitor（守护进程）

### 开发工具
- `bash`: Bourne Again SHell
- `awk`: "Aho Weiberger and Kernighan" 三个作者的姓的第一个字母
- `sed`: Stream EDitor（流编辑器）
- `grep`: Global Regular Expression Print
- `egrep`: Extended GREP
- `fgrep`: Fixed GREP
- `vim`: Vi IMproved
- `vi`: VIsual = Very Inconvenient

### 网络协议
- `SSH`: Secure SHell（安全外壳）
- `SSL`: Secure Sockets Layer（安全套接层）
- `FTP`: File Transfer Protocol（文件传输协议）
- `SFTP`: SSH File Transfer Protocol（SSH 文件传输协议）

### 编程语言
- `PHP`: Personal Home Page Tools = PHP Hypertext Preprocessor
- `Perl`: "Pratical Extraction and Report Language" = "Pathologically Eclectic Rubbish Lister"
- `Python`: 得名于电视剧 Monty Python's Flying Circus
- `Tcl`: Tool Command Language
- `Tk`: ToolKit

### 数据库
- `MySQL`: My 是最初作者女儿的名字，SQL = Structured Query Language

### 其他
- `apache`: "a patchy" server
- `YaST`: Yet Another Setup Tool
- `Fish`: the Friendly Interactive SHell
- `MIME`: Multipurpose Internet Mail Extensions
- `ECMA`: European Computer Manufacturers Association

## 实用提示
- 了解命令缩写有助于记忆和理解命令功能
- 许多缩写来自英语单词的首字母或前几个字母
- 有些缩写有历史原因，了解背景有助于记忆
