# 1.SQL语句

- SQL分类

  - **DDL**(Data Definition Language) 数据定义语言,用来定义数据库对象: 数据库, 表, 列等. 关键字: create alter drop等
  - **DML**(Data Manipulation Language) 数据操作语言,用于操作数据库中表的数据, 关键字:insert delete update
  - **DCL**(Data Control Language) 数据控制语言,用于定义数据库的访问权限和安全级别及创建用户
  - **DQL**(Data Query Language) 数据查询语言,用于查询数据库表中的记录,关键字: select  from  where 等

  

- SQL语法

  - 不区分大小写, 建议关键字大写, 其他内容小写
  - 可以单行也可以多行写, 以分号结尾
  - 可以使用/**/进行注释

  

- 常用数据类型

  | 类型    | 说明                                             |
  | ------- | ------------------------------------------------ |
  | int     | 整型                                             |
  | double  | 浮点型                                           |
  | varchar | 字符串类型                                       |
  | date    | 日期类型,格式为yyyy-MM-dd(只有年月日,没有时分秒) |

  

# 2.数据库操作

- 创建数据库:

  ```sql
  CREATE DATABASE 数据库名;
  CREATE DATABASE 数据库名 CHARACTER SET utf-8;
  ```

- 显示所有数据库:

  ```sql
  SHOW DATABASES;
  ```

- 使用指定数据库:

  ```sql
  USE 数据库名;
  ```

  

- 删除数据库:

  ```sql
  DROP DATABASE 数据库名;
  ```



# 3.数据表结构操作

- 创建表:

  ```sql
  CREATE TABLE 表名(列名1 数据类型 [约束],列名2 数据类型 [约束],...);
  ```

  - **约束**一般有: 
    - 主键约束(PRIMARY KEY)
    -  ID自动增长(AUTO_INCREMENT)
    - 非空约束(NOT NULL)
    - 唯一约束
    - 外键约束等
  - **主键约束**: 标识当前字段必须是非空的并且是唯一的, 一般只用于标识, 不具有实际意义

  

- 常见表操作:

  - 显示数据库中的所有表:

    ```sql
    SHOW TABLES;
    ```

  - 显示指定表的详细结构信息:

    ```sql
    DESC 表名;
    ```

  - 删除表:

    ```sql
    DROP TABLE 表名;
    ```



- 修改表添加列:

  ```sql
  ALTER TABLE 表名 ADD 列名 数据类型 [约束];
  ```

- 修改表中的列:

  ```sql
  ALTER TABLE 表名 MODIFY 列名 新数据类型; #修改列的数据类型
  ALTER TABLE 表名 CHANGE 旧列名 新列名 数据类型; #修改列名,可以同时修改列的数据类型
  ```

- 删除列:

  ```sql
  ALTER TABLE 表名 DROP 列名;
  ```

- 修改表名:

  ```sql
  RENAME TABLE 表名 TO 新表名;
  ```

- 修改表的字符集:

  ```sql
  ALTER TABLE 表名 CHARACTER SET 字符集;
  ```





# 4.数据表增删改查操作

####添加数据

- 添加数据

  ```sql
  INSERT INTO 表名(列名1,列名2,列名3,...) VALUES (值1,值2,值3,...)
  ```

- 添加数据时所有列都赋值, 可以简写:

  ```sql
  INSERT INTO 表名 VALUES (值1,值2,值3,...);
  ```

- 批量添加数据:

  ```sql
  INSERT INTO 表名(列名1,列名2,列名3,...) VALUES (值1,值2,值3,...),(值1,值2,值3,...),(值1,值2,值3,...),...;
  ```



#### 修改数据

- 修改表中指定列的内容

  ```sql
  UPDATE 表名 SET 列1=值1,列2=值2,... WHERE 条件;
  ```

  - 修改列内容时要加上条件, 如果没有加条件, 表中的所有列都会被修改
  - 条件可以使用表达式, 例如: id=1  id>=1   id<>1 
  - 在SQL中表示**"与或非"**: **and  or   not**



#### 删除数据

- 删除部分数据:

  ```sql
  DELETE FROM 表名 WHERE 条件;
  DELETE FROM 表名;/*删除数据表中的所有数据*/
  ```

- 删除整个数据表:

  ```sql
  DROP TABLE 表名;
  ```

- 清空数据表:

  ```sql
  TRUNCATE TABLE 表名; /*删除表后重建,auto_increment记录重置为0*/
  ```

- 面试题:

  ```sql
  使用 "DELETE FROM 表名;" 和使用 "TRUNCATE TABLE 表名;" 有什么区别?
  ```

  - 使用delete的方式, 是一条一条地删除记录,不会清空auto_increment记录
  - 使用truncate的方式, 是直接删除表, 重新建表, auto_increment记录重置为0



#### 查询语句

- 查询指定的列的数据

  ```sql
  SELECT 列名1, 列名2, ... FROM 表名;
  ```

- 查询所有列的数据

  ```sql
  SELECT * FROM 表名;
  ```

- 查询时去除指定列的重复数据:

  ```sql
  SELECT DISTINCT 列名 FROM 表名;
  ```

- 查询时临时更改列名:

  ```sql
  SELECT 列名 AS 临时列名 FROM 表名;
  ```

- 查询时临时更改表名:

  ```sql
  SELECT * FROM 表名 AS 临时表名;
  ```

- 查询过程中直接进行运算:

  ```sql
  SELECT uname, uscore+10 AS 'sum' FROM userscore;
  ```

- 条件查询:

  - 比较运算符

    ```sql
    >  <  <=  >=  =  <>  比较大小或相等
    
    BETWEEN...AND... 在某一区间的结果,包含头和尾
    
    IN(set) 显示在in列表中的结果,例如: in(1,2,3)
    
    LIKE 通配符: 模糊查询,可以使用两种通配符,%匹配多个字符,如: 'user%', _匹配一个字符,如:'user_'
    
    IS NULL: 判断是否为空
    	is null 判断是否为空
    	is not null判断不为空
    ```

  - 逻辑运算符

    - AND多个条件同时成立
    - OR 多个条件任意一个成立
    - NOT 不成立, 例如: where not(money>100)

- 排序查询

  - 升序查询

    ```sql
    SELECT uname,money FROM users ORDER BY money ASC;
    ```

    

  - 降序查询

    ```sql
    SELECT uname,money FROM users ORDER BY money DESC;
    ```




####添加外键

~~~sql
alter table orders add foreign key (cid) references customer(cid);
~~~



# 5.聚合函数

- COUNT: 统计数量

  ```sql
  SELECT COUNT(列名) FROM 表名; /*统计表中指定列的记录数量*/
  ```

  

- SUM: 求和

  ```sql
  SELECT SUM(money) FROM 表名; /*统计表中的money列中所有数据的和*/
  ```

  

- MAX:求最大值

  ```sql
  SELECT MAX(money) FROM 表名; /*统计表中的money列中所有数据的最大值*/
  ```

  

- MIN:求最小值

  ```sql
  SELECT MIN(money) FROM 表名; /*统计表中的money列中所有数据的最小值*/
  ```

  

- AVG:求平均值

  ```sql
  SELECT AVG(money) FROM 表名; /*统计表中的money列中所有数据的平均值*/
  ```

  

# 6.分组查询

**格式:  **

```sql
 SELECT 字段1,字段2...FROM 表名 GROUP BY 字段 HAVING 条件;
```

- having 和 where 的区别:

  - having 是在分组后对数据进行过滤
  - where是在分组前对数据进行过滤
  - having后面可以使用分组函数(统计函数)
  - where 后面不可以使用分组函数

- 例如:

  ```sql
  SELECT uname,SUM(money) FROM users GROUP BY uname HAVING SUM(money)>5000;
  ```

  

# 7.多表设计

- 表与表之间的关系一般有三种

  - 一对一
  - 一对多
  - 多对多

- 多表设计原则

  - 一对多:  在**多的一方**创建一个字段, 这个字段作为外键指向**一的一方**的主键

  - 多对多: 创建一个中间表, 中间表中至少有两个字段, 分别作为外键指向双方的主键

  - 一对一

    - 使用一对多的方式, 在一方建立唯一外键

    - 主键对应: 将双方的主键建立映射关系(双方的主键使用相同的ID)

      

# 8.多表查询

#####交叉查询:

- 语法: select * from A,B;
- 查询到的是两个表的**笛卡尔积**
- 一般很少用

#####**内连接查询** 

- inner join [inner关键字可以省略]

- 查询的是**两个表的交集内容**
- 语法: 
  - 显式内连接: select * from A inner join B on 条件;
  - 隐式内连接: select * from A,B where 条件;
- 例子:
  - 显式: SELECT * FROM customer c INNER JOIN orders o ON c.cid=o.cid;
  - 隐式: SELECT * FROM customer c , orders o where c.cid=o.cid;

##### **外连接查询**: 

- outer join[关键字outer可以省略]

- 左外连接: 查询的是**左表的全部和两个表的交集**
  - 语法: select * from A left outer join B on 条件;
  - 例子: SELECT * FROM customer c LEFT OUTER JOIN orders o ON c.cid=o.cid;
- 右外连接: 查询的是**右表的全部和两个表的交集**
  - 语法: select * from A rigth outer join B on 条件;
  - 例子: SELECT * FROM customer c RIGHT OUTER JOIN  orders o ON c.cid=o.cid;



![](.\imgs\MYSQL-外连接查询图示.jpg)

#####**图示说明:**

	- 内连接查询到的是交集C
	- 左外连接查询到的是A+C
	- 右外连接查询到的是B+C



##### 子查询

- 一个SQL语句查询的过程依赖另一个查询语句
- 例子: select * from customer c, orders o where c.cid=o.cid and c.cid in **(select cid from orders where addr like "广东%");**