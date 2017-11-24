# docker安装redis

## 安装
```bash
docker pull redis
```

## docker run启动
```bash
docker run --detach --publish 36379:6379 --restart always --volume /Users/dd/Documents/work/docker_data/redis/data:/data --volume /Users/dd/Documents/work/docker_data/redis/config/redis.conf:/usr/local/etc/redis/redis.conf dolphintwo/redis:latest redis-server --appendonly yes --requirepass 888888
```

## docker compose启动<useless>

## 登录