# curl / wget

## 常用场景
- 下载文件
- 测试 API
- 检查 HTTP 响应

## 常用命令
```bash
curl -O url
curl -I url
wget url
wget -r url
```

## 常用参数
- curl: -O 保存文件, -I 只显示头, -L 跟随重定向
- wget: -r 递归, -c 断点续传

## 易错点
- curl 默认输出到 stdout
- wget 默认保存文件

## 实战示例
```bash
curl -I https://example.com
wget -c https://example.com/file.tar.gz
```
