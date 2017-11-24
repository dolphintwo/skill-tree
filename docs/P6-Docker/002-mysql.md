# docker安装mysql

## 安装
```bash
docker pull mysql
```

## docker run启动
```bash
docker run --detach --volume /Users/dd/Documents/work/docker_data/mysql/data:/var/lib/mysql --volume /Users/dd/Documents/work/docker_data/mysql/config:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=888888 --restart always --publish 33306:3306 dolphintwo/mysql:latest
```

## docker compose启动<useless>
```
version: '3.1'
services:
    db:
        image: mysql
        restart: always
        environment:
            MYSQL_ROOT_PASSWORD: 888888
```

## 登录
用户名: `root`
密码: `888888`