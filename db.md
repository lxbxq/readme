# DB设计规范 #

----------

## 目录结构规范 ##

## 脚本命名规范 ##

### ddl脚本命名规范 ###

> `ddl_四位排序数字_组件名.sql`

> `示例：ddl_1000_ziker-common.sql`

### dml脚本命名规范 ###
> `dml_四位排序数字_组件名.sql`

> `示例：dml_1000_ziker-common.sql`
### ddl脚本编写规范 ###
> `1、全部小写`

----------
## 表设计规范 ##
### 表名规范 ###
> `1、全小写`
> 
> `2、单词间通过'_'间隔`
### 字段规范 ###
> `1、主键命名为'id',数据类型为int,不需要添加not null`

> `2、code字段类型为varchar,长度为50`

> `3、name字段类型为varchar,如果字段值为全英文长度为50，如果字段值包含中文长度为100`

> `4、type字段类型为varchar,长度为50`

> `5、email字段类型为varchar,长度为50`

> `6、address字段类型为varchar,长度300`

> `7、description字段类型为varchar,长度为500`

> `8、必须包含4个审计字段且不能为空。created_time、updated_time、created_by、updated_by。`

> `9、created_time、updated_time类型为timestamp`

> `status字段类型为varchar，长度为5`

> `gender字段表示性别，类型为varchar,长度为1`

### 外键命名规范 ###
> `1、外键命名fk_表名_字段名。如：fk_resource_authority_resource_id`
## 索引规范 ##
### 索引命名规范 ###
> `1、唯一索引：ux_表名_索引字段。如：ux_resource_code`

> `2、普通索引：ix_表名_索引字段。如：ix_role_name`