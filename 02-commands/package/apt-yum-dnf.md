# apt / yum / dnf

## 常用场景
- 安装软件包
- 更新系统
- 搜索软件包
- 在线安装软件

## Debian/Ubuntu (apt-get / apt)

### 常用命令
```bash
sudo apt-get update              # 获得最新的软件包的列表
sudo apt-get upgrade             # 升级已安装的包
sudo apt-get install package     # 从源中安装 package 软件
sudo apt-get remove package      # 删除 package 软件
sudo apt search keyword          # 搜索软件包
```

### 命令说明
- `apt-get update`: 更新软件包列表（不安装）
- `apt-get upgrade`: 升级已安装的包
- `apt-get install`: 安装软件包
- `apt-get remove`: 卸载软件包（保留配置文件）
- `apt-get purge`: 卸载软件包（删除配置文件）

### 优势
- 通过互联网在线安装，更加方便快捷
- 自动解决依赖关系

## CentOS/RHEL (yum / dnf)

### 常用命令
```bash
yum update                       # 更新系统
yum install package              # 安装软件包
yum search keyword               # 搜索软件包
yum remove package               # 卸载软件包
dnf install package              # dnf 是 yum 的下一代版本
```

## 常用参数
- `update`: 更新软件包列表
- `upgrade`: 升级已安装的包
- `install`: 安装
- `remove`: 卸载
- `search`: 搜索软件包

## 易错点
- 在 APT 中，`update` 刷新软件包索引，`upgrade` 升级已安装软件；在 DNF/YUM 中，`update` 通常也执行软件包升级
- 需要 root 权限（使用 sudo）
- Ubuntu 平台推荐使用 apt-get，CentOS/RHEL 使用 yum/dnf

## 实战示例
```bash
# Ubuntu/Debian
sudo apt-get update
sudo apt-get install sl
which sl
sudo apt-get remove sl

# CentOS/RHEL
yum update
yum install nginx
```

## 延伸阅读
- [rpm-dpkg.md](./rpm-dpkg.md) - 底层包管理
- [mirror-sources.md](./mirror-sources.md) - 镜像源配置
