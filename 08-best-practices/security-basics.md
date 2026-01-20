# 安全基础

## 常用场景
- 服务器安全加固
- 安全最佳实践

## 安全措施
- 定期更新系统
- 使用密钥认证
- 配置防火墙
- 最小权限原则
- 定期备份

## 常用工具
- fail2ban: 防止暴力破解
- ufw/firewalld: 防火墙
- ssh-keygen: SSH 密钥

## 安全检查
```bash
lastlog              # 查看最后登录
who                  # 当前登录用户
netstat -an | grep ESTABLISHED
```
