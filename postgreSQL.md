# 常用postgreSQL操作

----------


> 安装程序存放在共享目录中：\\192.168.1.5\share\postgreSQL
## DDL
### 创建数据库

> 语法为create database dbname;

>`create database ziker`;

> 语法为createdb [option...] [dbname [description]]

>`createdb -h localhost -p 5432 -U postgress ziker;`

### 默认使用模板库template1,可以手工指定template0

> `create database db2 template template0`
### 复制库

> `create database db3 template db2`

### 选择数据库

> 语法为:\c dbname; 

> `\c ziker;`
### 删除数据库
>语法为:drop database [if exists] dbname;

>`drop database db3;`

### 创建表

> 语法为：create table table_name(column1 datatype,column2 datatype,.....,columnN datatype,primary key (one or more columns));

>`create table wechat_agent (id int primary key not null,agent_name text not null);`
### 修改表
### 删除表
>语法为 drop table table_name;

>`drop table wechat_agent;`

## DML(同其他数据库)
### 新增
### 修改
### 查询
### 删除

### 常量
### 日期
>`select current_date;`
### 时间
>`select current_time;`
### 日期+时间
>`select current_timestamp;`

## 文件执行
### 脚本文件

> 语法为: \i filePath;

> `\i d:/my.sql;`

# 本地环境数据库创建(不做移交使用) #

----------

## 脚本 ##
### 共享库脚本 ###
> `请按顺序执行,并根据本地环境修改路径。`

> \i D:/work/ziker/ziker/db/pg/share/1.0/share_database.sql;'


> \i D:/work/ziker/ziker/db/pg/share/1.0/ddl_1000_ziker-common.sql;

> \i D:/work/ziker/ziker/db/pg/share/1.0/ddl_2000_ziker-user.sql;

> \i D:/work/ziker/ziker/db/pg/share/1.0/ddl_3000_ziker-datasource.sql;
### 企业模板脚本 ###
> `请按顺序执行，并根据本地环境配置`

> \i D:/work/ziker/ziker/db/pg/enterprise/template/ddl_1000_ziker-agent.sql;

> \i D:/work/ziker/ziker/db/pg/enterprise/template/ddl_2000_ziker-customer.sql；

> \i D:/work/ziker/ziker/db/pg/enterprise/template/ddl_3000_ziker-wechat.sql；

> \i D:/work/ziker/ziker/db/pg/enterprise/template/ddl_4000_ziker-session.sql；
