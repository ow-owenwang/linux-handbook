# sed

## 常用场景
- 文本替换
- 删除行
- 批量编辑

## 常用命令
```bash
sed 's/old/new/g' file
sed -i 's/old/new/g' file
sed '/pattern/d' file
```

## 常用参数
- -i: 直接修改文件
- -n: 静默模式
- -e: 多个表达式

## 易错点
- 默认只替换每行第一个匹配
- 需要 g 标志替换全部

## 实战示例
```bash
sed 's/127\.0\.0\.1/localhost/g' /etc/hosts
sed -i '/^#/d' config.conf
```

## 延伸阅读
- [regex-basics.md](./regex-basics.md)
- [awk.md](./awk.md)
