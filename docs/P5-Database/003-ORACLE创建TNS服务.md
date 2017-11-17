# 添加tns服务
```bash
[oracle@oracle ~]$ cd /u01/app/oracle/product/11.2.0/dbhome/network/admin/
# 此时没有TNS服务 所以没有对应的配置文件
[oracle@oracle admin]$ ls
listener.ora  samples  shrept.lst
# 创建tnsnames.ora侦听配置文件
[oracle@oracle admin]$ cat > tnsnames.ora <<EOF
ORCL =
  (DESCRIPTION =
    (ADDRESS_LIST=
      (ADDRESS = (PROTOCOL = TCP)(HOST = 172.21.4.20)(PORT = 1521))
    )
    (CONNECT_DATA =
      (SERVICE_NAME = orcl)
    )
  )

EXTPROC_CONNECTION_DATA =
  (DESCRIPTION =
    (ADDRESS_LIST =
      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC))
    )
    (CONNECT_DATA =
      (SID = PLSExtProc1)
      (PRESENTATION = RO)
    )
)
EOF
```
重启侦听器
```bash

[oracle@oracle admin]$ lsnrctl stop
[oracle@oracle admin]$ lsnrctl start
[oracle@oracle admin]$ lsnrctl status

LSNRCTL for Linux: Version 11.2.0.1.0 - Production on 16-NOV-2017 16:52:56

Copyright (c) 1991, 2009, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC1521)))
STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 11.2.0.1.0 - Production
Start Date                15-NOV-2017 15:21:46
Uptime                    1 days 1 hr. 31 min. 10 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Listener Parameter File   /u01/app/oracle/product/11.2.0/dbhome/network/admin/listener.ora
Listener Log File         /u01/app/oracle/diag/tnslsnr/oracle/listener/alert/log.xml
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC1521)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=0.0.0.0)(PORT=1521)))
Services Summary...
Service "orcl11g" has 1 instance(s).
  Instance "orcl", status READY, has 1 handler(s) for this service...
Service "orclXDB" has 1 instance(s).
  Instance "orcl", status READY, has 1 handler(s) for this service...
The command completed successfully
```
**侦听器启动较慢 大约1～2分钟**