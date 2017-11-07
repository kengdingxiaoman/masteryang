# 常用SQL

## 删除列
alter table <font color="red">${表名}</font> drop column <font color="red">${列名}</font>

例子：删除表 order 的字段：pay_time

alter table order drop column pay_time;

## 修改列名

alter table <font color="red">${表名}</font> change column <font color="red">${列名}</font> <font color="red">${新列名}</font> 原列的各个属性

例子：将表 order 的 cust_id 字段 改名为 recv_cust_id

alter table order change cust_id recv_cust_id varchar(16) NOT NULL;
