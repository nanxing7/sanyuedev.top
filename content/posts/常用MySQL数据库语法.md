---
title: 常用MySQL数据库语法
date: 2019-10-03 12:02:30
tags: 
categories:
- 数据库
- MySQL
---
记载这个的目的是为了方便复习自学考试中数据库常用的操作语句
<!-- more -->
## 数据定义
### 数据库模式定义
创建数据库
```sql
CREATE DATABASE db_name;
```
选择数据库
```sql
USE db_name;
```
修改数据库
```sql
ALTER DATABASE db_name;
```
删除数据库
```sql
DROP DATABASE;
```
查看数据库
```sql
SHOW DATABASES;
```

### 表定义
#### 创建表
```sql
CREATE TABLE tbl_name(
字段名 1 数据类型 [列级完整性约束条件][默认值]
[,字段名 2 数据类型 [列级完整性约束条件][默认值]][......]
[表级完整性约束条件]
)[ENGINE=引擎类型]
```
关键字 `AUTO_INCREMENT` 实现自动增长
#### 更新表
##### 增加列
ADD
```sql
ALTER TABLE ADD tbl_name 字段名 1 数据类型 [列级完整性约束条件][默认值] {AFTER/BEFORE} 字段;
```
CHANGE
```sql
ALTER TABLE tbl_name CHANGE 原字段 新字段 属性
```
ALTER
```sql
ALTER TABLE tbl_name ALTER [COLUMN] 字段名 SET 
```
MODIFY
```sql
ALTER TABLE tbl_name MODIFY 字段 ...
```
DROP
```sql
ALTER TABLE tbl_name DROP 字段名
```
RENAME[TO]
```sql
ALTER TABLE tbl_name RENAME TO new_tbl_name
```
#### 重命名表
```sql
RENAME TABLE tbl_name TO new_tbl_name [,tbl2_name TO new_tbl_name]
```
#### 删除表
```sql
DROP TABLE [IF EXISTS] tbl_name
```
#### 查看表
显示表的名称
```sql
SHOW TABLES;
```
显示表的结构
```sql
DESCRIBE tbl_name;
```
连接数据库
```sql
mysql -u root -p
```

显示所有数据库
```sql
SHOW DATABASES;
```

显示数据库中所有表
```sql
SHOW TABLES;
```

选择数据库
```sql
USE 数据库名；
```

获取表结构
```sql
desc <表名>
或者
SHOW COLUMNS FROM <表名>;
```

```slq
CREATE DATABASE <数据库名>
DROP DATABASE <数据库名>
```

```sql

```

约束条件
```sql
ALTER TABLE <表名> DROP FOREIGN KEY <外键约束名>
ALTER TABLE <表名> DROP PRIMARY KEY
ALTER TABLE <表名> DROP {约束名|候选键字段名}
```

外键的添加
```sql
FOREIGN KEY(添加的列) REFERENCES 关联的表(关联的列) ON DELETE RESTRICET ON UPDATE RESTRICT
FOREIGN KEY(pro_id) REFERENCES pro(id) ON DELETE RESTRICET ON UPDATE RESTRICT
```

触发器
删除触发器
```sql
DROP TRIGGER [IF EXIST] 
```
创建触发器
```sql
CREATE TRIGGER add_test AFTER INSTER ON test FOR EACH row set @x='OK'
```