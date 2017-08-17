## oracle管理性SQL

### 如何查看自己用户有哪些系统权限

select * from session_privs;

### 查看所有的用户

select * from all_users;

### 查看用户的表

两种方法：<br/>
select * from user_all_tables;<br/>
select * from user_objects where OBJECT_TYPE='TABLE';

### 查看用户的存储过程
两种方法：<br/>
select * from user_source;<br/>
select * from user_objects where OBJECT_TYPE='PROCEDURE';

### 查看用户下的序列
两种方法：<br/>
select * from user_sequences;<br/>
select * fromuser_objects where OBJECT_TYPE='SEQUENCE';

### 查看oracle字符集
select * from nls_database_parameters;  

### 解锁数据库用户
alter user <font color="red">username</font> account unlock;

### 建立表空间和用户
create tablespace <font color="red">tablespaceName</font> datafile '<font color="red">/data/u01/app/oracle/file01.dbf</font>' size 256m autoextend on next 128m maxsize unlimited segment space management auto extent management local uniform size 1m;

create user <font color="red">userName</font> identified by "<font color="red">password</font>" default tablespace <font color="red">tablespaceName</font>;<br/>
grant connect,resource,create view,create sequence to <font color="red">userName</font>;

### 修改用户密码
alter user <font color="red">username</font> identified by <font color="red">password</font>;

例子：alter user cash identified by cashdb;
修改cash用户的密码，新密码为：cashdb

### 删除表
drop table <font color="red">tableName</font>;

例子：drop table test_table;<br/>
删除表 test_table

在删除表的时候如果出现以下错误信息：unique/primary keys in table referenced by foreign keys<br/>
说明表中有字段被作为另一张表的外键，所以无法删除。这时可以使用：

drop table tableName cascade constraints;

### 删除表空间
drop tablespace <font color="red">tablespaceName</font>;

例子：drop tablespace testdata;<br/>
删除表空间testdata

### 删除存储过程
drop procedure <font color="red">procedureName</font>;

例子：drop procedure p_name;<br/>
删除存储过程p_name

删除序列
drop sequence <font color="red">sequenceName</font>;

例子：drop sequence padNoSequence;<br/>
删除序列padNoSequence

### 对表进行重命名
rename <font color="red">oldTableName</font> to <font color="red">newTableName</font>;

例子：rename usr_info to user_information;<br/>
将表 usr_info 改名为 user_information
