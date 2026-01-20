# 防火墙 / iptables

## 常用场景
- 配置防火墙规则
- 端口开放/关闭
- 安全加固

## iptables 基础
```bash
iptables -L
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -j DROP
```

## firewalld (CentOS/RHEL)
```bash
firewall-cmd --list-all
firewall-cmd --add-port=80/tcp --permanent
firewall-cmd --reload
```

## ufw (Ubuntu)
```bash
ufw status
ufw allow 80/tcp
ufw enable
```

## 易错点
- 错误配置可能导致无法远程连接
- 测试前确保有本地访问
