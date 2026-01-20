# cron / at

## 常用场景
- 定时任务
- 计划任务

## cron
```bash
crontab -e          # 编辑定时任务
crontab -l          # 查看定时任务
crontab -r          # 删除定时任务
```

## crontab 格式
```
* * * * * command
分 时 日 月 周
```

## at
```bash
at 14:30
at now + 1 hour
atq                 # 查看任务
atrm ID             # 删除任务
```

## 实战示例
```bash
# 每天凌晨 2 点备份
0 2 * * * /path/to/backup.sh

# 每小时执行
0 * * * * /path/to/script.sh
```
