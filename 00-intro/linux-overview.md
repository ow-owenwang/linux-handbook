# Linux 概述

## 常用场景
- 了解 Linux 基本概念
- 选择 Linux 发行版
- 理解操作系统的作用

## 操作系统的作用

### 操作系统的目标
- **方便**：使计算机系统易于使用
- **有效**：以更有效的方式使用计算机系统资源
- **扩展**：方便用户有效开发、测试和引进新功能

### 操作系统的地位
操作系统在计算机系统中承上启下的地位：向下封装硬件，向上提供操作接口。

## Unix 家族历史

### 发展历程
- **1960 年代**：贝尔实验室参与了 Multics 项目，后来退出；Multics 并非简单地“失败”，其设计对后来的系统有影响。
- **1969 年前后**：Ken Thompson、Dennis Ritchie 等人在贝尔实验室开始开发 Unix。
- **1972—1973 年**：Dennis Ritchie 主导设计 C 语言，Unix 随后主要用 C 重写。
- **1974**：UNIX 第一次出现在贝尔实验室以外。此后 UNIX 被政府机关，研究机构，企业和大学注意到，并逐渐流行开来。
- **1980**：有两个最主要的 Unix 的版本线，一个是 Berkeley 的 BSD UNIX，另一个是 AT&T 的 Unix，两者的竞争最终引发了 Unix 的战争，最终导致 Unix 出现各种各样的变种。
- **1982**：AT&T 基于版本 7 开发了 UNIX System Ⅲ 的第一个商业版本，并不再开源。
- **1992~2001**：由于版权问题，AT&T 公司与 BSD 开发组开始了一场将近 10 年的版权官司。UNIX 由于其昂贵的费用，仅局限于大型机的应用；BSD 因为版权问题，失去了宝贵的发展时期。

## Linux 家族历史

### 发展历程
- **Minix**：最初是由 Andrew Tanenbaum 教授，仿照 4.3BSD 的源代码，白手起家完成了 12000 行 C 语言的编写工作。这个系统只是一个教学工具，没有什么实际应用价值。
- **1991**：Linus Torvalds 公开了最初的 Linux 内核；Linux 是受 Minix 使用经历启发而独立开发的内核。

### Linux 的五大支柱
Linux 操作系统的诞生、发展、和成长过程依赖于五个重要支柱：
1. **Unix 操作系统**
2. **Minix 操作系统**
3. **GNU 计划**
4. **POSIX 标准**
5. **互联网**

### GNU 计划
- GNU 是 "GNU is Not Unix" 的递归缩写
- Richard M. Stallman 于 1983 年宣布 GNU 计划，1984 年开始开发
- 旨在开发一个免费、类 Unix 的操作系统 - GNU 系统及其开发工具
- Emacs 编辑系统、BASH shell 程序、GCC、GDB 等开发工具都是 GNU 组织的产品
- Linux 内核于 1992 年改用 GPL，随后与 GNU 工具等自由软件组合成可用的发行版；一些人称其为 "GNU/Linux"，日常也常简称 Linux

历史参考：[GNU 计划最初公告](https://www.gnu.org/gnu/initial-announcement.html)、[GNU 计划介绍](https://www.gnu.org/gnu/the-gnu-project.en.html)。

### POSIX 标准
- POSIX 标准定义了操作系统应该为应用程序提供的接口标准
- POSIX 标准用来统一 Unix、Linux 各分支编程接口，以提高其通用型和可移植性

## Linux 和 Unix 的联系

### Unix 系统特点
- UNIX 系统是工作站上最常用的操作系统
- 它通常支持多用户、多任务；“实时操作系统”是另一个有特定时限保证的概念，不能概括所有 Unix 系统
- UNIX 系统具有稳定、高效、安全、方便、功能强大等诸多优点
- 自 20 世纪 70 年代开始便运行在许多大型和小型计算机上

### Linux 的优势
- UNIX 虽然是一个安全、稳定且功能强大的操作系统，但它也一直是一种大型的而且对运行平台要求很高的操作系统，只能在工作站或小型机上才能发挥全部功能，并且价格昂贵，对普通用户来说是可望而不可及的，这为后来 Linux 的崛起提供了机会
- **Linux 是一个类 UNIX 操作系统**
- Linux 内核是受版权和 GPL 等许可约束的自由软件；发行版可能包含不同许可的软件，且兼容性依实现而异
- Linux 在 x86 架构上实现了 UNIX 系统的全部特性，具有多用户多任务的能力，同时保持了高效性和稳定性

### Linux 的优秀特点
1. **开放性**
2. **完全免费**
3. **多用户**
4. **多任务**
5. **良好的用户界面**
6. **设备独立性**
7. **提供了丰富的网络功能**
8. **可靠的系统安全性**
9. **良好的可移植性**

## Linux 内核及发行版

### Linux 内核版本
内核(kernel)是系统的心脏，是运行程序和管理像磁盘和打印机等硬件设备的核心程序，它提供了一个在裸设备与应用程序间的抽象层。

内核发布分主线与稳定维护等分支，具体支持期限取决于分支与维护者：
- **稳定版**：具有工业级强度，可以广泛地应用和部署。新的稳定版相对于较旧的只是修正一些 bug 或加入一些新的驱动程序
- **开发版**：由于要试验各种解决方案，所以变化很快

**内核源码及发布信息**：[kernel.org](https://www.kernel.org/)。补丁经过维护者分层审查，只有被接受的更改才进入相应分支。

### Linux 发行版本
Linux 发行版 (也被叫做 GNU/Linux 发行版) 通常包含了包括桌面环境、办公套件、媒体播放器、数据库等应用软件。

这些操作系统通常由 Linux 内核、以及来自 GNU 计划的大量的函式库，和基于 X Window 的图形界面，在 X Window 中用户同样可以通过使用鼠标对窗口、菜单等进行操作来完成相应的工作。

### X Window 系统
- X Window 系统是一个非常出色的图形窗口系统，是类 UNIX 系统的图形用户界面的工业标准
- X Window 系统最重要的特征之一就是它的结构与设备无关
- **主要特点**：
  - X Window 系统是客户机/服务器结构的。X Window 的实现是与操作系统内核分开的，其主要由 X Server 和 X Client 两部分组成
  - X Window 系统不是 Unix/Linux 操作系统的必须的构成部分，而只是一个可选的应用程序组件

### 主要发行版（2015 年排名）
1. Linux Mint
2. Debian
3. Ubuntu
4. openSUSE
5. Fedora
6. Mageia
7. Manjaro
8. CentOS
9. Arch
10. Elementary

## Unix/Linux 开发应用领域

### Unix/Linux 服务器
是目前 Unix/Linux 应用最多的一个领域，可以提供 Web、FTP、Gopher、SMTP/POP3、Proxy/Cache、DNS 等服务器，支持服务器集群，支持虚拟主机、虚拟服务、VPN 等。

### 嵌入式 Linux 系统
嵌入式 Linux 是将流行的 Linux 操作系统进行剪裁修改，能够在嵌入式计算机系统上运行的一种操作系统。Linux 嵌入式系统能够支持多种 CPU 和硬件平台，性能稳定，剪裁性好，开发和使用容易。其中包括 Embedix、uCLinux、muLinux 等。

### 桌面应用
近年来，Linux 系统特别强调在桌面应用方面的改进，并且已达到相当的水平，完全可以作为一种集办公应用、多媒体应用、网络应用等多方面功能于一体的图形界面操作系统，在办公应用方面，Unix/Linux 集成了 openOffice、SUN 公司的 StarOffice 以及 KOffice 等工具。

### 电子政务
随着 Linux 的快速发展，Linux 已逐渐成为 Windows 系统重要的竞争力量。尤其是 Linux 在安全性方面的独特优势，又使得 Linux 在政府应用领域得到很大的发展。目前一些国家正将其电子政务系统向 Linux 平台迁移。中国政府也对 Linux 给予极大的支持。

## 核心概念
- Linux 内核 vs 发行版
- 主要发行版：Ubuntu、CentOS、Debian、Fedora

## 延伸阅读
- [filesystem-overview.md](./filesystem-overview.md) - 文件系统概述
- [common-paths.md](./common-paths.md) - 常用路径
- [abbreviations.md](./abbreviations.md) - 常见缩写
