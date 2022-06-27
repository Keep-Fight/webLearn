# 数据库安全性

------



## 一 、权限表

### （一） **固定数据库角色表**

| 名称              |                             权限                             |
| :---------------- | :----------------------------------------------------------: |
| db_owner          |            拥有数据库全部权限，包括删除数据库权限            |
| db_accessadmin    | 只给数据库用户创建其他数据库用户的权限，而没有创建登录用户的权限。 |
| db_securityadmin  |       可以管理全部权限、对象所有权、角色和角色成员资格       |
| db_ddladmin       | 可以发出所有DDL(Create,Alter和Drop)，但不能发出GRANT、REVOKE或DENY语句 |
| db_backupoperator | 允许对数据库进行备份和还原的权限【备份与还原是通过sql sever management studio也可以进行】 |
| db_datareader     |            可以查询数据库内任何用户表中的所有数据            |
| db_datawriter     |            可以更改数据库内任何用户表中的所有数据            |
| db_denydatareader |            不能查询数据库内任何用户表中的任何数据            |
| db_denydatawriter |            不能更改数据库内任何用户表中的任何数据            |
| public            | 数据库的每个合法用户都属于该角色.它为数据库中的用户提供了所有默认权限 |

### （二）**固定数据库角色权限详解**

#### 1. db_owner

- 向其他固定数据库角色中添加成员，或从其中删除成员
- 运行所有的DDL语句
- 运行BACKUP DATABASE和BACKUP LOG语句
- 使用CHECKPOINT语句显式地启动检查点进程
- 运行下列dbcc命令：dbcc checkalloc、dbcc checkcatalog、dbcc checkdb、dbcc updateusage
  授予、取消或剥夺每一个数据库对象上的下列权限：SELECT、INSERT、UPDATE、DELETE和REFERENCES
- 使用下列系统过程向数据库中添加用户或角色：sp_addapprole、sp_addrole、sp_addrolemember、 sp_approlepassword、sp_changeobjectowner、sp_dropapprole、sp_droprole、 sp_droprolemember、sp_dropuser、sp_grantdbaccess
  使用系统过程sp_rename为任何数据库对象重新命名

#### 2.  db_accessadmin

- 运行下列系统过程：sp_addalias、sp_dropalias、sp_dropuser、sp_grantdbacess、sp_revokedbaccess
  为Windows用户账户、Windows组和SQL Server登录添加或删除访问

#### 3. dbdatareader

- 固定数据库角色dbdatareader的成员对数据库中的数据库对象(表或视图)具有SELECT权限
- 这些成员不能把这个权限授予其他任何用户或角色。(这个限制对REVOKE语句来说同样成立。)

#### 4. dbdatawriter

- 固定数据库角色dbdatawriter的成员对数据库中的数据库对象(表或视图)具有INSERT、UPDATE和DELETE权限
- 这些成员不能把这个权限授予其他任何用户或角色。(这个限制对REVOKE语句来说也同样成立。)

#### 5. db_ddladmin

- 运行所有DDL语句
- 对任何表上授予REFERENCESE权限
- 使用系统过程sp_procoption和sp_recompile来修改任何存储过程的结构
- 使用系统过程sp_rename为任何数据库对象重命名
- 使用系统过程sp_tableoption和sp_changeobjectowner分别修改表的选项和任何数据库对象的拥有者

#### 6. db_securityadmin

- 运行与安全有关的所有Transact-SQL语句(GRANT、DENY和REVOKE)
- 运 行以下系统过程：sp_addapprole、sp_addrole、sp_addrolemember、sp_approlepassword、 sp_changeobjectowner、sp_dropapprole、sp_droprole、sp_droprolemember
- 固定数据库角色db_securityadmin的成员可以管理数据库中的安全

#### 7. db_backupoperator

- 固定数据库角色db_backupoperator的成员可以管理数据库备份的过程
- 运行BACKUP DATABASE和BACKUP LOG语句
- 用CHECKPOINT语句显式地启动检查点进程
- 运行如下dbcc命令：dbcc checkalloc、dbcc checkcatalog、dbcc checkdb、dbcc updateusage

#### 8.  db_denydatareader

- 固定数据库角色db_denydatareader的成员对数据库中的数据库对象(表或视图)没有SELECT权限=>如果数据库中含有敏感数据并且其他用户不能读取这些数据，那么就可以使用这个角色。

#### 9. db_denydatawriter

- 固定数据库角色db_denydatawriter的成员对数据库中的任何数据库对象(表或视图)没有INSERT、UPDATE和DELETE权限。

### （三）**固定服务器角色表**

| 名称                 |                    权限                     |
| -------------------- | :-----------------------------------------: |
| sysadmin             |         执行SQL Server中的任何动作          |
| serveradmin          |               配置服务器设置                |
| setupadmin           |           安装复制和管理扩展过程            |
| securityadmin        | 管理登录和CREATE DATABASE的权限以及阅读审计 |
| processadmin         |             管理SQL Server进程              |
| dbcreator            |              创建和修改数据库               |
| diskadmin            |                管理磁盘文件                 |
| sp_addsrvrolemember  |           添加固定服务器角色成员            |
| sp_dropsrvrolemember |           删除固定服务器角色成员            |

**注意**：添加或删除固定服务器角色成员。 只有固定服务器角色的成员才能执行上述两个系统过程来从角色中添加或删除登录账户。

### （四）固定服务器角色权限详解

#### 1.  sysadmin

- 固定服务器角色sysadmin的成员被赋予了SQL Server系统中所有可能的权限
- eg:只有这个角色中的成员(或一个被这个角色中的成员赋予了CREATE DATABASE权限的用户)才能够创建数据库
- 固定服务器角色和sa登录之间有着特殊的关系。sa登录一直都是固定服务器角色中的成员，并且不能从该角色中删除。

#### 2. serveradmin

- 向该服务器角色中添加其他登录
- 运行dbcc pintable命令(从而使表常驻于主内存中)
- 运行系统过程sp_configure(以显示或更改系统选项)
- 运行reconfigure选项(以更新系统过程sp_configure所做的所有改动)
- 使用shutdown命令关掉数据库服务器
- 运行系统过程sp_tableoption为用户自定义表设置选项的值

#### 3. setupadmin

- 向该服务器角色中添加其他登录
- 添加、删除或配置链接的服务器
- 执行一些系统过程，如sp_serveroption

#### 4. securityadmin

- 固定服务器角色securitypadmin中的成员可以执行关于服务器访问和安全的所有动作
- 向该服务器角色中添加其他登录
- 读取SQL Server的错误日志
- 运 行如下的系统过程：如sp_addlinkedsrvlogin、sp_addlogin、sp_defaultdb、 sp_defaultlanguage、sp_denylogin、sp_droplinkedsrvlogin、sp_droplogin、 sp_grantlogin、sp_helplogins、sp_remoteoption和sp_revokelogin(所有这些系统过程都与系统安 全相关。)

#### 5. processadmin

- 固定服务器角色processadmin中的成员用来管理SQL Server进程，如中止用户正在运行的查询
- 向该服务器角色中添加其他登录
- 执行KILL命令(以取消用户进程)

#### 6. dbcreator

- 固定服务器角色dbcreator中的成员用来管理与数据库创建和修改有关的所有动作
- 向该服务器角色中添加其他登录
- 运行CREATE DATABASE和ALTER DATABASE语句
- 使用系统过程sp_renamedb来修改数据库的名称

#### 7. diskadmin

- 向该服务器角色中添加其他登录
- 运行如下系统过程：sp_ddumpdevice和sp_dropdevice。
- 运行DISK INIT语句
- 固定数据库角色

## 二、权限的管理

### （一）操作类型表

| 对象类型   | 对象         | 操作类型                                                    |
| ---------- | ------------ | ----------------------------------------------------------- |
| 数据库模式 | 模式         | CREATE  SCHEMA                                              |
| 数据库模式 | 基本表       | CREATE  TABLE , ALTER TABLE                                 |
| 数据库模式 | 视图         | CREATE  VIER                                                |
| 数据库模式 | 索引         | CREATE  INDEX                                               |
| 数据       | 基本表和视图 | SELECT , INSERT , UPDATE, DELETE, REFERENCES,ALL PRIVILEGES |
| 数据       | 属性列       | SELECT , INSERT , UPDATE, REFERENCES,  ALL PRIVILEGES       |



### （二）授权

**授予权限 GRANT**

```sql
GRANT <权限1>，<权限2>，·····
ON <对象类型1><对象名1>，<对象类型2><对象名2>，····
TO <用户1>，<用户2>，····
[WITH GRANT OPTION]
-- WITH GRANT OPTION 获得该权限的用户可以将这种权限授予其他用户

-- 举例样式
GRANT INSERT 
ON TABLE SC
TO U5
WITH GRANT OPTION
```

**收回权限 REVOKE**

```sql
REVOKE <权限1>，<权限2>，·····
ON <对象类型1><对象名1>，<对象类型2><对象名2>，····
FROM <用户1>，<用户2>，····[CASCADE|RESTRICT]
```



