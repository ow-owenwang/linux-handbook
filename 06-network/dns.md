# DNS

## 常用场景
- 配置 DNS 服务器
- DNS 故障排查
- 域名解析测试

## 常用命令
```bash
nslookup domain
dig domain
host domain
```

## DNS 配置文件
- `/etc/resolv.conf`: DNS 服务器
- `/etc/hosts`: 本地域名解析

## 实战示例
```bash
dig @8.8.8.8 example.com
nslookup example.com
```
