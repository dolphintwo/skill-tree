# docker安装gitlab
## 安装
```bash
docker pull registry.cn-hangzhou.aliyuncs.com/lab99/gitlab-ce-zh
```

## docker run启动
```bash
docker run --detach --publish 30443:443 --publish 30080:80 --publish 30022:22 --name gitlab --restart always --volume /Users/dd/Documents/work/docker_data/gitlab/config:/etc/gitlab --volume /Users/dd/Documents/work/docker_data/gitlab/logs:/var/log/gitlab --volume /Users/dd/Documents/work/docker_data/gitlab/data:/var/opt/gitlab dolphintwo/gitlab-ce-zh:latest
```

## docker compose启动<useless>
建立一个`docker-compose.yml`，内容如下：
```yaml
version: '2'
services:
    web:
      image: 'dolphintwo/gitlab-ce-zh:latest'
      restart: always
      hostname: 'gitlab.example.com'
      environment:
        GITLAB_OMNIBUS_CONFIG: |
          external_url 'http://gitlab.example.com'
          # Add any other gitlab.rb configuration here, each on its own line
      ports:
        - '80:80'
        - '443:443'
        - '22:22'
      volumes:
        - config:/etc/gitlab
        - data:/var/opt/gitlab
        - logs:/var/log/gitlab
volumes:
    config: {}
    data: {}
    logs: {}
```
## 登录
默认用户名密码
用户名: `root`
密码: `5iveL!fe`