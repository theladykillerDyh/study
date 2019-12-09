# 数据库学习

## DML(Data Manipulation Language)数据操纵语言

适用范围：对数据库中的数据进行一些简单操作，如insert,delete,update,select等.

```mysql
insert 将记录插入到数据库 
update 修改数据库的记录 
delete 删除数据库的记录
```



## DDL(Data Definition Language)数据定义语言

适用范围：对数据库中的某些对象(例如，database,table)进行管理.

```mysql
create table 创建表     
alter table  修改表   
drop table 删除表   
truncate table 删除表中所有行     
create index 创建索引   
drop index  删除索引
```

## DCL(Data Control Language )数据控制语句

适用范围：操作数据库对象的权限，这些操作的确定使数据更加的安全。

DCL的主要语句(操作)

Grant语句：允许对象的创建者给某用户或某组或所有用户(PUBLIC)某些特定的权限。

Revoke语句：可以废除某用户或某组或所有用户访问权限

DCL的操作对象(用户):此时的用户指的是数据库用户。

## 总结：

1.DML操作是可以手动控制事务的开启、提交和回滚的。

2.DDL操作是隐性提交的，不能rollback！