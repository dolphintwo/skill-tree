# oracle静默安装

本文适合以下情况安装：
   - GUI 界面远程交互比较慢 .
   - 数据库服务器无法使用图形界面访问.
   - 批量部署oracle.

## 1.准备工作

### 1.1 安装依赖包
```
yum install -y binutils compat-libstdc++-33 compat-db \
control-center elfutils-libelf elfutils-libelf-devel gcc \
gcc-c++ glibc glibc-common glibc-devel glibc-headers libaio \
libaio-devel expat libgcc libstdc++ libstdc++-devel make \
sysstat unixODBC glibc-headers unixODBC-devel pdksh \
sysstat xscreensaver  
```

### 1.2 组用户创建
```
# groupadd oinstall
# groupadd -g 1002 dba
# groupadd -g 1005 oper
# useradd -u 1002 -g oinstall -G oper,dba oracle
# passwd oracle
Changing password for user oracle.
New password:
BAD PASSWORD: The password is shorter than 8 characters
Retype new password:
passwd: all authentication tokens updated successfully.
##查看用户oracle组情况
# id oracle
uid=1002(oracle) gid=1001(oinstall) groups=1001(oinstall),1002(dba),1005(oper)

```
### 1.3 os参数修改
#### 1.3.1 修改安装限制
```
# vim /etc/security/limits.conf
## 添加如下
oracle soft nproc 2047
oracle hard nproc 16384
oracle soft nofile 1024
oracle hard nofile 65536

# vim /etc/pam.d/login
## 添加如下
session required pam_limits.so
```

#### 1.3.2修改内核参数
```
# vim /etc/sysctl.conf
## 添加如下:
kernel.shmmax = 2077155328  
kernel.sem = 250 32000 100 128
net.core.rmem_default = 4194304
net.core.rmem_max = 4194304
net.core.wmem_default = 262144
fs.file-max = 6815744
net.ipv4.ip_local_port_range = 9000 65500
net.core.wmem_max = 1048576
fs.aio-max-nr = 1048576

## 执行 使内核参数生效
# sysctl -p
```

#### 1.3.3修改profile
```
# vim /etc/profile
## 添加如下：
if [ $USER = "oracle" ] ; then
if [ $SHELL = "/bin/ksh" ]; then
ulimit -p 16384
ulimit -n 65536
else
ulimit -u 16384 -n 65536
fi
umask 0
fi
```

#### 1.3.4 修改.bash_profile
```
# su - oracle
# vim .bash_profile
## 添加如下
export ORACLE_BASE=/u01/app/oracle
export ORACLE_HOME=$ORACLE_BASE/product/11.2.0/dbhome
export ORACLE_SID=orcl
export LD_LIBRARY_PATH=$ORACLE_HOME/lib:/lib:/usr/lib:/usr/local/lib 
export PATH=$PATH:$HOME/bin:$ORACLE_HOME/bin:$HOME/.local/bin:
export NLS_LANG=AMERICAN_AMERICA.ZHS16GBK    

## 执行使之生效
# source .bash_profile 
```
### 1.4 创建挂载点
目录/u01 格式ext4 见[03-磁盘格式化](P03-磁盘格式化/docs.md)  
修改目录权限：
```chown -R oracle:oinstall /u01 ```
![u01.png](P5-Database/_media/001/u01.png)


## 2.安装
### 2.1 下载安装包
[下载地址](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html)

![download.png](P5-Database/_media/001/download.png)
```
文件列表
linux.x64_11gR2_database_1of2.zip
linux.x64_11gR2_database_2of2.zip
```
变更文件权限
```
chown oracle:oinstall linux.x64_11gR2_database_*
```
### 2.2 修改inventory目录
```
vim /etc/oraInst.loc
inventory_loc=/u01/app/oraInventory
inst_group=oinstall
```

<font color=red size=5>!!!内容以下操作均为oracle用户操作</font>

### 2.3 开始静默安装
#### 解压安装包，注意查看文件权限
```
# mv linux.x64_11gR2_database_* /u01/
# cd /u01
# unzip linux.x64_11gR2_database_1of2.zip
# unzip linux.x64_11gR2_database_2of2.zip
# ll
drwxrwxr-x 8 oracle oinstall       4096 Aug 21  2009 database
-rwxrwxr-x 1 oracle oinstall 1239269270 Sep 20 16:09 linux.x64_11gR2_database_1of2.zip
-rwxrwxr-x 1 oracle oinstall 1111416131 Sep 20 16:10 linux.x64_11gR2_database_2of2.zip
```
#### 修改应答文件
```
# cd /u01/database/response
该目录下有三个应答文件
# ll 
total 152
-rwxrwxr-x 1 oracle oinstall 44948 Sep 22 10:09 dbca.rsp
-rwxrwxr-x 1 oracle oinstall 22789 Sep 20 16:47 db_install.rsp
-rwxrwxr-x 1 oracle oinstall  5740 Sep 22 10:25 netca.rsp
```
已修改好的应答文件下载：

[db_install.rsp](P5-Database/_media/001/db_install.rsp) 

[dbca.rsp](P5-Database/_media/001/dbca.rsp) 

[netca.rsp](P5-Database/_media/001/netca.rsp) 

应答文件内容根据具体情况修改

#### 安装oracle
```
# cd /u01/database/
# ./runInstaller -silent -responseFile /u01/database/response/db_install.rsp
```

<font color=red size=4>！安装过程时间比较长，请耐心等待</font>

安装完成后出现如下图所示：
![db_install.jpeg](P5-Database/_media/001/db_install.jpeg)

根据安装完成的提示
使用root连接一个新终端，运行提示的shell脚本，运行完成后回到该终端回车完成安装

#### 安装数据库实例
静默安装数据库实例
``` 
dbca -silent -responseFile /u01/database/response/dbca.rsp
```
![dbca.jpeg](P5-Database/_media/001/dbca.jpeg)
#### 安装oracle侦听器
静默安装侦听器
```
netca /silent /responseFile  /u01/database/response/netca.rsp
```

![netca.jpeg](P5-Database/_media/001/netca.jpeg)

至此 ORACLE静默安装完成
检查数据库状态：
![done.jpeg](P5-Database/_media/001/done.jpeg)
