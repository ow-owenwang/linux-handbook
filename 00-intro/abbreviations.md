# Linux 常见缩写

## 常用场景
- 理解命令含义
- 记忆命令名称
- 学习 Linux 术语

## 命令缩写

### 基础命令
- `ls`: list（列出目录内容）
- `cd`: Change Directory（改变目录）
- `pwd`: print working directory（显示当前工作目录）
- `su`: switch user（切换用户）
- `rm`: Remove（删除目录或文件）
- `rmdir`: Remove Directory（删除目录）
- `mkdir`: Make Directory（创建目录）
- `mv`: Move file（移动文件）
- `cp`: Copy file（复制文件）
- `cat`: concatenate（连接并输出文件内容；如 `cat file1 file2 >> file3` 会追加到 `file3`）
- `ln`: Link files（链接文件）
- `touch`: 创建空文件或更新时间戳

### 系统命令
- `ps`: process status（进程状态，类似于 windows 的任务管理器）
- `df`: disk free（显示文件系统空间使用情况；`-i` 查看 inode）
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
- `rpm`: RPM Package Manager（递归名称，管理 RPM 软件包）
- `dpkg`: Debian package manager（Debian 包管理器）
- `apt`: Advanced package tool（高级包工具，Debian 或基于 Debian 的发行版中提供）

### 其他命令
- `tar`: Tape archive（磁带归档）
- `dd`: 按块复制并可转换数据；名称来源有多种说法，不宜当作可靠缩写记忆
- `ldd`: List dynamic dependencies（列出动态依赖）
- `insmod`: install module（载入模块）
- `lsmod`: List modules（列出模块）
- `rmmod`: Remove module（移除模块）

## 目录缩写

### 系统目录
- `/bin`: BINaries（二进制程序文件）
- `/dev`: devices（设备节点）
- `/etc`: ETCetera（目录存放着各种系统配置文件，类似于 windows 下的 system）
- `/lib`: LIBrary（库文件）
- `/proc`: PROCesses（进程信息）
- `/sbin`: Superuser BINaries（超级用户二进制文件）
- `/tmp`: TeMPorary（临时文件）
- `/usr`: 历史上与 user 相关，现主要存放可共享、通常只读的系统程序与资源；“Unix Shared Resources”是后来的助记说法
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
- `IFS`: Internal Field Separator（内部字段分隔符）
- `VT`: Video Terminal（视频终端）
- `daemon`: 守护进程；此词源于英语 daemon，并非 “Disk And Execution MONitor” 的缩写

### 开发工具
- `bash`: Bourne Again SHell
- `awk`: Aho、Weinberger、Kernighan 三位作者姓氏的首字母
- `sed`: Stream EDitor（流编辑器）
- `grep`: Global Regular Expression Print
- `egrep`: Extended GREP
- `fgrep`: Fixed GREP
- `vim`: Vi IMproved
- `vi`: visual（可视化编辑器）；“Very Inconvenient”是戏称

### 网络协议
- `SSH`: Secure SHell（安全外壳）
- `SSL`: Secure Sockets Layer（安全套接层）
- `FTP`: File Transfer Protocol（文件传输协议）
- `SFTP`: SSH File Transfer Protocol（SSH 文件传输协议）

### 编程语言
- `PHP`: Personal Home Page Tools = PHP Hypertext Preprocessor
- `Perl`: 语言名称；“Practical Extraction and Report Language”等是后来的反向缩写
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
