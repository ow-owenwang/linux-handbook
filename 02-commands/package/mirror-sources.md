# 镜像源配置

## 常用场景
- 加速软件包下载
- 更换软件源
- 配置国内镜像

## Ubuntu 镜像源配置

### 备份原配置
```bash
# 如果需要备份的话可以先备份
cp /etc/apt/sources.list /etc/apt/sources.back
```

### 编辑配置文件
```bash
vim /etc/apt/sources.list
# 或者
gedit /etc/apt/sources.list
```

### 阿里云镜像源
```plain
# 阿里镜像
deb http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
```

### 清华大学镜像源
```plain
# 清华大学
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty-backports main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ trusty-proposed main restricted universe multiverse
```

**注意**：上面的 `trusty` 是 Ubuntu 版本代号，需要根据你的 Ubuntu 版本替换为对应的代号（如：focal、jammy 等）。

### 设置公钥
```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32
```

### 更新源
```bash
sudo apt-get update
```

## CentOS/RHEL 镜像源配置

### 备份原配置
```bash
cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

### 使用阿里云镜像
```bash
# 下载阿里云镜像源配置
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo

# 清理缓存
yum clean all

# 生成缓存
yum makecache
```

## 常用镜像源

### 国内镜像源
- **阿里云**：http://mirrors.aliyun.com
- **清华大学**：http://mirrors.tuna.tsinghua.edu.cn
- **中科大**：http://mirrors.ustc.edu.cn
- **网易**：http://mirrors.163.com

### 选择建议
- 根据地理位置选择最近的镜像源
- 企业环境建议使用稳定的镜像源
- 定期更新镜像源配置

## 易错点
- 修改镜像源后必须执行 `apt-get update` 或 `yum makecache`
- Ubuntu 版本代号需要匹配，否则可能无法使用
- 修改前建议备份原配置文件

## 实战示例
```bash
# Ubuntu 配置阿里云镜像
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo vim /etc/apt/sources.list
# 编辑内容...
sudo apt-get update

# CentOS 配置阿里云镜像
sudo cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
sudo wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
sudo yum clean all
sudo yum makecache
```

## 延伸阅读
- [apt-yum-dnf.md](./apt-yum-dnf.md) - 包管理命令
- [rpm-dpkg.md](./rpm-dpkg.md) - 底层包管理
