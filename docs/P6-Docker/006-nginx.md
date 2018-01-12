# docker安装nginx

## 安装
```bash
docker pull nginx
```

## docker run启动
docker run -d --name dd_nginx -v /mnt/data/nginx:/etc/nginx dolphintwo/nginx

docker run -d --name dd_mysql -v /mnt/data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD='&UJM8ik,' --restart always -p 3306:3306 dolphintwo/mysql:latest