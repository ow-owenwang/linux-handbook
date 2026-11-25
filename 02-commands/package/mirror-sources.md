# 软件包镜像源

## 使用场景

软件源下载缓慢或原镜像不可用时，可改用与**发行版、版本代号和架构**匹配的镜像。修改前确认镜像由可信机构运营并支持当前系统版本；不要把旧版本的仓库地址直接套到新系统。

## Debian / Ubuntu（APT）

1. 查看发行版与代号：`cat /etc/os-release`。
2. 检查实际启用的源：`grep -R -E '^(deb |URIs:)' /etc/apt/sources.list /etc/apt/sources.list.d/ 2>/dev/null`。较新的系统也可能使用 `.sources`（deb822）文件。
3. 备份**实际使用的配置文件**，再把其中仓库 URI 改为镜像站为该版本提供的 URI。保留原有的 `Suites`、`Components` 和 `Signed-By` 等字段，除非镜像站的官方说明要求修改。
4. 执行 `sudo apt update`，确认没有签名或索引错误，再安装或升级软件。

第三方仓库应使用独立密钥文件和 `Signed-By` 限定其信任范围。`apt-key` 已弃用；切勿通过随意导入公钥来掩盖签名错误。系统官方仓库仅更换镜像域名时，通常沿用发行版提供的签名密钥。

## RHEL 系（DNF / YUM）

先查看 `/etc/os-release` 和 `/etc/yum.repos.d/` 中实际启用的仓库。备份对应 `.repo` 文件，再按镜像站**针对该发行版及版本**的说明修改 `baseurl` 或 `metalink`，保留 GPG 校验配置。随后执行：

```bash
sudo dnf clean all
sudo dnf makecache
```

旧系统使用 `yum` 时将上面的 `dnf` 换为 `yum`。仓库生命周期结束后，普通镜像可能已不提供该版本；应先确认发行版支持状态和升级路径。

## 核对

- `apt update` 或 `dnf makecache` 失败时，先检查版本代号、URL、证书、签名和网络连接。
- 不要为完成更新而关闭仓库签名校验。
- 源配置格式与路径以当前发行版提供的文件和文档为准。

参考：[APT sources.list 手册](https://manpages.debian.org/unstable/apt/sources.list.5.en.html)、[APT apt-key 手册](https://manpages.debian.org/unstable/apt/apt-key.8.en.html)。

## 延伸阅读

- [apt-yum-dnf.md](./apt-yum-dnf.md)
- [rpm-dpkg.md](./rpm-dpkg.md)
