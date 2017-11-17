# 修改数据库字符集
cicd环境使用的字符集为`utf-8`，因此，要确保数据库字符集为utf8或其扩展集
以SYSTEM用户连接
```
su - oracle
sqlplus /nolog
conn SYSTEM/Accp1234 as sysdba
```
查询数据库字符集设置
```sql
select * from v$nls_parameters;
```
![char.png](P5-Database/_media/002/char.png)

```
﻿NLS_LANGUAGE=AMERICAN
NLS_TERRITORY=AMERICA
NLS_CHARACTERSET=AL32UTF8
```
操作数据库起停挂载状态，修改字符集重启
以下操作请一步一步操作，看到返回完成再进行下一行
```sql
shutdown immediate;
startup mount;
alter system enable restricted session;
alter system set job_queue_processes=0;
alter system set aq_tm_processes=0;
alter database open;
alter database character set AL32UTF8;
shutdown immediate;
startup;

SELECT * FROM v$nls_parameters WHERE parameter = 'NLS_CHARACTERSET'; --查看生效情况
```
![char2.jpeg](P5-Database/_media/002/char2.jpeg)