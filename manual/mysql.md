# mysql命令

## 启动登录

### 启动服务
mysql.server start

### 关闭服务
mysql.server stop

### 登录
mysql -u root -p

然后输入密码，-u 表示user，-p 表示密码

### 退出命令行
输入 exit

## 管理类命令

### 查看数据库
show databases;

### 展示数据库表
show tables;

### 查看当前密码策略
show variables like 'validate_password%';

设置密码策略：<br/>
类似：set global validate_password_mixed_case_count=0;

### 查看用户
select host, user from mysql.user;

### 查看字符集
show variables like 'character_set%';

### 查看库表信息
show table status from <font color="red">database</font>

例如：<br/>
show table status from orca;

则会查看 schema : orca 下的库表信息

## 初始化类

### 创建数据库
create database <font color="red">database</font>;

例如：<br/>
create database orca;

创建数据库 orca

### 进入数据库
use <font color="red">database</font>;

例如：<br/>
use orca;

进入数据库 orca

### 创建用户
create user '<font color="red">username</font>'@'localhost' identified by '<font color="red">password</font>';

例如：<br/>
create user 'orcauser'@'localhost' identified by 'orcauser';

创建用户 orcauser, 密码 orcauser

### 修改密码
set password for '<font color="red">username</font>'@'localhost' = password("<font color="red">password</font>");

例如：<br/>
set password for 'orcauser'@'localhost' = password("12345678");

修改用户 orcauser 的密码为 12345678

### 删除用户
drop user '<font color="red">username</font>'@'localhost';

例如：<br/>
drop user 'orcauser'@'localhost';

### 赋予用户权限

grant <font color="red">privileges</font> on <font color="red">database</font>.<font color="red">table</font> to '<font color="red">username</font>'@'localhost';

例如：<br/>
grant all on orca.* to 'orcauser'@'localhost';

把数据库 orca 中所有表的所有权限赋予给 orcauser 用户

grant select,insert on orca.test_user to 'orcauser'@'localhost';

把数据库 orca 中表test_user的查询，新增权限赋予给 orcauser 用户

权限 privileges 有这么多：<br/>
SELECT, UPDATE, DELETE, CREATE, DROP, REFERENCES, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES, EXECUTE, CREATE VIEW, SHOW VIEW, CREATE ROUTINE, ALTER ROUTINE, EVENT, TRIGGER
