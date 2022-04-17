MySQL操作



1.操作库（文件夹）

新增数据库：

```
create database 数据库名 charset 字符编码;

create database db1 charset utf8;
```

改数据库编码：

```
alter database 数据库名 charset 字符编码;

alter database db1 charset gbk;
```

查看数据库：

```
show databases;
或
show create database db1;
```

删除数据库：

```
drop database 数据库名;

drop database db1;
```

操作表（文件）

切换到某一个库（文件夹）：use db1;

```
mysql> use db1;
Database changed
mysql> select database();		# 查看当前所在的库
+------------+
| database() |
+------------+
| db1        |
+------------+
1 row in set (0.00 sec)
```

新增表：

```
create table 表名(表的标题);

create table t1(id int,name char(10),sex,age int);
```

查看表：

```
show tables;

show create table t1;

desc t1;		# 查看表结构
```

删除表：

```
drop table 表名;

drop table t1;
```

改表：

```
alter table t1 charset gbk;		# 改编码

alter table t1 add sex char;	# 加字段

alter table t1 drop sex;		# 删除标题

alter table t1 modify sex char(6);		# 改宽度

alter table t1 change sex SEX char(6);	# 改字段名
```



操作记录

增加记录：

```
insert into 数据库名.文件名 (信息) values #  对应信息传入
(),
...
();

insert into db1.t1(id,name,age,SEX) values
(1,'egon',18,'male'),
(2,'egon2',28,'male'),
(3,'egon3',38,'male'),
(4,'egon4',48,'male');

# 如果有字段允许传空，可以不传
```

查记录

```
mysql> select id,name from t1;
+------+-------+
| id   | name  |
+------+-------+
|    1 | egon  |
|    2 | egon2 |
|    3 | egon3 |
|    4 | egon4 |
+------+-------+
select * from db1.t1;		# 查看所有字段
```

改记录

```
update t1 set name='EGON4';		# 更改所有字段

update t1 set name='alex' where id=4;		# 指定字段修改
```

删除记录

```
delete from db1.t1;		# 没有把表重置到初始状态

truncate db1.t1;		# 清空+重置表里的记录
```

自增id

```
create table t1(id int not primary key,name char(4));

create table t1(di int not null unique auto-increment,name char(4));	
# 自增id必须满足：自增字段必须是
```





