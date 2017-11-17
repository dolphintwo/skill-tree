## 安装
```bash
docker pull registry.cn-hangzhou.aliyuncs.com/lab99/gitlab-ce-zh
```

## docker run启动
```bash
docker run --detach \
    --hostname gitlab.example.com \
    --publish 443:443 --publish 80:80 --publish 22:22 \
    --name gitlab \
    --restart always \
    --volume /srv/gitlab/config:/etc/gitlab \
    --volume /srv/gitlab/logs:/var/log/gitlab \
    --volume /srv/gitlab/data:/var/opt/gitlab \
    twang2218/gitlab-ce-zh:latest
```

## docker compose启动
建立一个`docker-compose.yml`，内容如下：
```yaml
version: '2'
services:
    web:
      image: 'twang2218/gitlab-ce-zh:latest'
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