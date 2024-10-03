### 管理员命令行操作

#### 启动$MySQL$服务：```net start mysql```

#### 关闭$MySQL$服务：```net stop mysql```

#### 登录：```mysql -uroot -p```

#### 退出：```exit```

#### 创建数据库： ```create database 数据库名 [default charset=utf8];```

#### 删除数据库： ```drop database 数据库;```

#### 查看全部数据库：```show databases;```

#### 看个别数据仓库：

```
use 库名; //进入该库
show tables; //查看当前库的所有表
```

#### 查看其它库的所有表：``` show tables from mysql;```

#### 查看在哪个库：``` select database();```

#### 在当前所在库创建表：

```
 create table 表名(
 列名1 列类型1 primary key auto_increment,
 列名2 列类型2 unique,
 ...
 )engine=innodb default charset=utf8;
```

#### 删除表： ```drop table 表名;```

#### 查看表的结构： ``` desc 表名;```

#### 查看表中的数据：```select * from 表名;```

#### 在表中插入数据：``` insert into 表名 （属性1，属性2，...） values(数据1，数据2，...);```

#### 修改表中数据：``` update 表名 set 属性1=新的数据 where 属性2=原来的数据```

#### 删除整行数据：```delete from 表名 where 属性1=数据;```

#### 在登录时查看版本号：```select version();``` 在dos界面查看版本号：```mysql -V```

#### 单行注释：#注释 或 -- 注释   多行注释：/* 注释文字 */ 

master  系统数据库，记录了所有其他数据库的存在

约束：

1、主键约束

2、外键约束

3、unique约束（唯一约束）

4、default约束

5、check 约束 check(列名 < 数值)



