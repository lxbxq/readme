#����postgreSQL����
>��װ�������ڹ���Ŀ¼�У�\\192.168.1.5\share\postgreSQL
##DDL
###�������ݿ�
>�﷨Ϊcreate database dbname;

>`create database ziker`;

>�﷨Ϊcreatedb [option...] [dbname [description]]

>`createdb -h localhost -p 5432 -U postgress ziker;`

###Ĭ��ʹ��ģ���template1,�����ֹ�ָ��template0
>`create database db2 template template0`
###���ƿ�
>`create database db3 template db2`

###ѡ�����ݿ�

> �﷨Ϊ:\c dbname; 
> 
>`\c ziker;`
###ɾ�����ݿ�
>�﷨Ϊ:drop database [if exists] dbname;

>`drop database db3;`

###������
>�﷨Ϊ��create table table_name(column1 datatype,column2 datatype,.....,columnN datatype,primary key (one or more columns));

>`create table wechat_agent (id int primary key not null,agent_name text not null);`
###�޸ı�
###ɾ����
>�﷨Ϊ drop table table_name;

>`drop table wechat_agent;`

## DML(ͬ�������ݿ�)
###����
###�޸�
###��ѯ
###ɾ��

##����
###����
>`select current_date;`
###ʱ��
>`select current_time;`
###����+ʱ��
>`select current_timestamp;`

##�ļ�ִ��
###�ű��ļ�
>�﷨Ϊ \i filePath;

>`\i d:/my.sql;`
