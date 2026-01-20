# Docker 基础

## 常用场景
- 容器化应用
- 环境隔离
- 快速部署

## 常用命令
```bash
docker ps
docker images
docker run image
docker build -t name .
docker exec -it container bash
```

## 核心概念
- Image: 镜像
- Container: 容器
- Dockerfile: 构建文件

## 实战示例
```bash
docker run -d -p 80:80 nginx
docker exec -it container_id bash
```

## 延伸阅读
- [docker-compose.md](./docker-compose.md)
