# 磁盘空间不足

## 常用场景
- 磁盘满了
- 查找大文件
- 清理空间

## 排查步骤
1. 检查磁盘使用: `df -h`
2. 查找大文件: `du -sh * | sort -h`
3. 查找大文件: `find / -size +100M`
4. 清理日志: `journalctl --vacuum-time=7d`

## 常用命令
```bash
df -h
du -sh * | sort -h
find / -size +100M -ls
```

## 清理建议
- 清理日志文件
- 清理包缓存
- 清理临时文件
