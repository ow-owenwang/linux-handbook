# Docker Compose

## 常用场景
- 多容器应用
- 服务编排
- 开发环境

## 常用命令
```bash
docker-compose up
docker-compose up -d
docker-compose down
docker-compose ps
docker-compose logs
```

## docker-compose.yml 示例
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "80:80"
```

## 延伸阅读
- [docker-basics.md](./docker-basics.md)
