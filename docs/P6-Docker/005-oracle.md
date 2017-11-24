# docker安装mysql

## 安装
```bash
docker pull index.tenxcloud.com/guodong/docker-oracle-xe-11g
```

## docker run启动
```bash
docker run --detach --publish 38080:8080 --publish 31521:1521 --restart always -e processes=10000 -e sessions=11050 -e transactions=12150 --volume /Users/dd/Documents/work/docker_data/oracle/data:/u01/app/oracle dolphintwo/oracle:11.2.0.2
```

## docker compose启动<useless>


## 登录
```
hostname: localhost
port: 31521
sid: xe
username: system
password: oracle

http://localhost:8080/apex
workspace: INTERNAL
user: ADMIN
password: oracle
```

## DockeFile
```
FROM ubuntu:14.04

MAINTAINER Maksym Bilenko <sath891@gmail.com>

# get rid of the message: "debconf: unable to initialize frontend: Dialog"
ENV DEBIAN_FRONTEND noninteractive

ADD chkconfig /sbin/chkconfig
ADD oracle-install.sh /oracle-install.sh
ADD init.ora /
ADD initXETemp.ora /

# Prepare to install Oracle
RUN apt-get update && apt-get install -y -q libaio1 net-tools bc curl rlwrap && \
apt-get clean && \
rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/* &&\
ln -s /usr/bin/awk /bin/awk &&\
mkdir /var/lock/subsys &&\
chmod 755 /sbin/chkconfig &&\
/oracle-install.sh

# see issue #1
ENV ORACLE_HOME /u01/app/oracle/product/11.2.0/xe
ENV PATH $ORACLE_HOME/bin:$PATH
ENV ORACLE_SID=XE

EXPOSE 1521
EXPOSE 8080
VOLUME ["/u01/app/oracle"]

ENV processes 500
ENV sessions 555
ENV transactions 610

ADD entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]
CMD [""]
```