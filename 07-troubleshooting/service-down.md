# 服务无法启动

## 常用场景
- 服务启动失败
- 服务异常退出
- 端口被占用

## 排查步骤
1. 查看服务状态: `systemctl status service`
2. 查看日志: `journalctl -u service`
3. 检查端口: `ss -lntp | grep port`
4. 检查配置文件: 验证配置语法

## 常用命令
```bash
systemctl status nginx
journalctl -u nginx -n 50
ss -lntp | grep :80
nginx -t  # 测试配置
```

## 常见原因
- 配置文件错误
- 端口被占用
- 权限问题
- 依赖服务未启动
