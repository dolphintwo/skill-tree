# 性能调优
## 最大连接数
```sql
SQL> select value from v$parameter where name ='processes'; --查看当前最大连接

SQL> select USERNAME,status,count(*) from v$session group by USERNAME,status order by 3;  --查看当前连接数当前链接数

--修改最大连接数
SQL> alter system set processes = 5000 scope = spfile;

System altered.

SQL> shutdown immediate;
Database closed.
Database dismounted.
ORACLE instance shut down.
SQL> startup;
ORACLE instance started.

Total System Global Area 6680915968 bytes
Fixed Size            2213936 bytes
Variable Size        4026533840 bytes
Database Buffers    2617245696 bytes
Redo Buffers          34922496 bytes
Database mounted.
Database opened.
```