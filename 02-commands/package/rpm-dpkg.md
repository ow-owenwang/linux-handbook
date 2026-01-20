# rpm / dpkg

## 常用场景
- 安装本地包
- 查询已安装包
- 底层包管理
- 管理 RPM/DEB 格式的软件包

## RPM 命令

### 简介
RPM 的全称为 Redhat Package Manager，是由 Redhat 公司提出的，用于管理 Linux 下软件包的软件。它是一种软件打包发行并且实现自动安装的程序，需要用 rpm 程序安装的软件包，其后缀是 `.rpm`。

### 使用格式
```bash
rpm [选项] [软件包名]
```

### 常用命令
```bash
rpm -ivh package.rpm           # 安装软件包
rpm -qa | grep package        # 查询系统是否已安装指定的软件包
rpm -qa                       # 查看系统已安装的所有软件包
rpm -ql package               # 列出软件包安装的文件
rpm -e package                # 卸载软件包
rpm -e package --nodeps       # 强制卸载，不检查依赖项
rpm -ivh package.rpm --force  # 强制安装
```

### 常用参数
- `-i`: 指定安装的软件包
- `-h`: 使用 "#" 显示详细的安装过程及进度
- `-v`: 显示安装的详细信息
- `-q`: 查询系统是否已安装指定的软件包
- `-a`: 查看系统已安装的所有软件包
- `-e`: 卸载软件包
- `-l`: 列出软件包的文件列表
- `--nodeps`: 配合 -e 参数使用，强制卸载不检查依赖项
- `--force`: 强制操作，如强制安装删除等

## dpkg 命令

### 常用命令
```bash
dpkg -i package.deb           # 安装 deb 包
dpkg -l | grep package        # 查询已安装的包
dpkg -L package               # 列出软件包安装的文件
dpkg -r package               # 卸载软件包
```

## 易错点
- 不自动解决依赖关系，可能需要手动安装依赖
- 通常用 apt/yum 更简单，会自动处理依赖
- 使用 `--nodeps` 可能导致系统问题，需谨慎

## 实战示例
```bash
# 安装 RPM 包
rpm -ivh nginx.rpm

# 查询已安装的包
rpm -qa | grep gcc

# 卸载包
rpm -e package
rpm -e package --nodeps        # 强制卸载

# 安装 DEB 包
dpkg -i nginx.deb
```
