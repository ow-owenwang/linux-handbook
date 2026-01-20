# 常用一行命令

## 常用场景
- 快速处理任务
- 临时操作

## 文件操作
```bash
find . -name "*.log" -delete
du -sh * | sort -h
```

## 文本处理
```bash
grep -r "pattern" . | wc -l
sed -i 's/old/new/g' *.txt
```

## 系统信息
```bash
ps aux | awk '{sum+=$3} END {print sum}'
df -h | grep -E '^/dev'
```

## 网络
```bash
netstat -an | grep ESTABLISHED | wc -l
```
