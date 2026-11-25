# Docker Compose

## 常用场景
- 多容器应用
- 服务编排
- 开发环境

## 常用命令
```bash
docker compose up
docker compose up -d
docker compose down
docker compose ps
docker compose logs
```

## docker-compose.yml 示例
```yaml
services:
  web:
    image: nginx
    ports:
      - "80:80"
```

`docker compose` 是 Compose v2 命令；旧的 `docker-compose` v1 已停止维护。当前 Compose 文件无需顶层 `version` 字段。

## 延伸阅读
- [docker-basics.md](./docker-basics.md)
