# 关机重启

## 常用场景
- 系统关机
- 系统重启
- 计划关机
- 切换运行级别

## 关机重启命令

### reboot
```bash
reboot                  # 重新启动操作系统
```

### shutdown
```bash
shutdown -r now         # 立刻重新启动操作系统，shutdown 会给别的用户提示
shutdown -h now         # 立刻关机，其中 now 相当于时间为 0 的状态
shutdown -h 20:25       # 系统在今天的 20:25 会关机
shutdown -h +10         # 系统再过十分钟后自动关机
shutdown -c             # 取消已计划的关机
```

### init
```bash
init 0                  # 关机
init 6                  # 重启
```

### 命令对比

| 命令 | 含义 | 特点 |
|------|------|------|
| `reboot` | 重新启动操作系统 | 立即重启，不给提示 |
| `shutdown -r now` | 重新启动操作系统 | 会给其他用户提示 |
| `shutdown -h now` | 立刻关机 | 会给其他用户提示 |
| `shutdown -h 20:25` | 计划关机 | 指定时间关机 |
| `shutdown -h +10` | 延迟关机 | 10 分钟后关机 |
| `init 0` | 关机 | 切换到运行级别 0 |
| `init 6` | 重启 | 切换到运行级别 6 |

## 字符界面和图形界面切换

### 使用 init 命令（Red Hat 平台）
```bash
init 3                  # 切换到字符界面
init 5                  # 切换到图形界面
```

### 使用快捷键（适用大部分平台）
- `Ctrl + Alt + F2`: 切换到字符界面（tty2）
- `Ctrl + Alt + F3`: 切换到字符界面（tty3）
- 图形会话所在的 TTY 取决于发行版和显示管理器，可用 `loginctl` 查看，不能固定认为是 tty7

### 运行级别说明
- **0**: 关机
- **1**: 单用户模式（维护模式）
- **2**: 多用户模式，网络是否启用依发行版和 init 配置而定
- **3**: 多用户模式（字符界面，有网络）
- **4**: 未使用
- **5**: 图形界面模式
- **6**: 重启

## sync 命令
把内存数据同步到磁盘。

```bash
sync                    # 把内存中数据写到磁盘中
```

**注意事项**：
- 正常关机流程会同步并卸载文件系统；一般无需事先手动运行 `sync`
- 目前 `shutdown`/`reboot`/`halt` 等命令均已经在关机前进行了 `sync`

## logout 命令
注销当前登录。

```bash
logout                  # 注销。在图形运行级别无效，在运行级别有效
```

## 易错点
- shutdown 命令会给其他用户发送提示，适合多用户环境
- reboot 和 init 6 立即执行，不给提示
- 使用 shutdown 可以取消（`shutdown -c`）
- 切换运行级别需要 root 权限
- 关机前建议先执行 `sync` 同步数据（现代系统已自动处理）

## 实战示例
```bash
# 立即重启
sudo reboot
sudo shutdown -r now

# 立即关机
sudo shutdown -h now
sudo init 0

# 计划关机
sudo shutdown -h 20:25
sudo shutdown -h +10

# 取消计划关机
sudo shutdown -c

# 切换界面
sudo init 3              # 切换到字符界面
sudo init 5              # 切换到图形界面
```

## 延伸阅读
- [boot-process.md](./boot-process.md) - 启动过程
- [systemd.md](./systemd.md) - systemd 管理
