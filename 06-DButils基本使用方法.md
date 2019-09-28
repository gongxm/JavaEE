#### 基本使用步骤

- 导入jar包:```commons-dbutils-1.7.jar```

- 创建对象:

  ```java
  QueryRunner qr = new QueryRunner();
  ```

- 定义SQL语句

  ```java
  String sql = "xxx";
  ```

- 调用方法:

  ```java
  qr.update(con,sql);//这个方法可以完成对数据库的增删改操作:insert delete update, 返回数据库记录更新条数
  
  qr.query(con,sql,handler,params...);//这个方法用于查询数据,根据传入不同的hander结果处理对象,返回对应的结果
  ```



#### 常用的结果处理handler对象

- ArrayHandler: 将结果集中的第一条记录封装到一个Object[]中, 数组中的每一个元素就是这条记录的每一个字段的值

  ```sql
  示例: [1,zhangsan,23]
  ```

  

- ArrayListHandler: 将结果集中的每一条记录封装到一个Object[]中, 然后把这些数组封装到List集合中

  ```sql
  示例: {[1,zhangsan,23],[2,lisi,24],[3,wangwu,25]}
  ```

  

- BeanHandler:将结果集中的第一条记录封装到一个指定的JavaBean对象中

- BeanListHandler: 将结果集中的每一条记录封装成一个JavaBean对象 , 将这些对象封装到List集合中

- ColumnListHandler:将结果集中指定的列的值封装到List集合中

  ```sql
  示例: name列==> [zhangsan,lisi,wangwu]
  ```

  

- ScalarHandler:适用于单记录结果集, 例如: ``` SELECT COUNT(*) FROM users;```

- MapHandler: 将结果集中的第一条记录封装到Map集合中, key是列名, value是对应的值

  ```sql
  示例:
  [id=1,username=zhangsan,age=23]
  ```

  

- MapListHandler:将结果集中的每一条记录封装到一个Map集合中, 把这些Map集合封装到一个List集合中

  ```sql
  示例:
  [[id=1,username=zhangsan,age=23],[id=2,username=lisi,age=24],[id=3,username=wangwu,age=25]]
  ```

  