# 服务管理

## 常用场景
- 启动/停止服务
- 设置开机自启
- 查看服务状态

## 常用命令
```bash
systemctl start nginx
systemctl stop nginx
systemctl restart nginx
systemctl reload nginx
systemctl enable nginx
systemctl status nginx
```

## 服务文件位置
- `/etc/systemd/system/`: 系统服务
- `~/.config/systemd/user/`: 用户服务

## 常用操作示例（以 nginx 为例）
```bash
# 停止服务
sudo systemctl stop nginx

# 启动服务
sudo systemctl start nginx

# 重启服务
sudo systemctl restart nginx

# 查看服务状态
sudo systemctl status nginx

# 开机自启动
sudo systemctl enable nginx

# 取消开机自启动
sudo systemctl disable nginx

# 检查配置文件是否有语法错误（nginx 示例）
sudo nginx -t

# 重新加载配置文件（不中断服务）
sudo systemctl reload nginx
```

## 实战示例
```bash
systemctl enable --now nginx
systemctl list-units --type=service
```
