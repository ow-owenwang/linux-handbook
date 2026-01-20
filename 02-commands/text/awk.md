# awk

## 常用场景
- 文本处理
- 数据提取
- 格式化输出

## 常用命令
```bash
awk '{print $1}' file
awk -F: '{print $1}' /etc/passwd
awk '/pattern/ {print $0}' file
```

## 常用参数
- -F: 指定分隔符
- -v: 定义变量

## 易错点
- 默认分隔符是空格
- $0 表示整行

## 实战示例
```bash
awk -F: '{print $1, $7}' /etc/passwd
ps aux | awk '{sum+=$3} END {print sum}'
```

## 延伸阅读
- [regex-basics.md](./regex-basics.md)
- [sed.md](./sed.md)
