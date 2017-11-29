# docker安装mongodb
## 安装
```bash
docker pull mongo
```

## docker run启动
```bash
docker run --detach --publish 27017:27017 --name mongodb --volume  /Users/dd/Documents/work/docker_data/mongo/data:/data/db dolphintwo/mongo:latest
```

## docker compose启动<useless>


## 登录
```
$ docker exec -it mongodb mongo admin
connecting to: admin
> db.createUser({ user: 'dolphintwo', pwd: 'abc123456', roles: [ { role: "userAdminAnyDatabase", db: "admin" } ] });
Successfully added user: {
	"user" : "dolphintwo",
	"roles" : [
		{
			"role" : "userAdminAnyDatabase",
			"db" : "admin"
		}
	]
}
```
