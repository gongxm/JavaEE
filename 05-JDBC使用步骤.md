# JDBC的使用

##基本使用步骤:

1. 导入数据库驱动包, 例如:mysql-connector-java-5.1.28.jar

2. 加载数据库驱动

   ```java
   Class.forName("com.mysql.jdbc.Driver");
   ```

3. 获取数据库连接

   ```java
   String url = "jdbc:mysql://localhost:3306/mydatabase";
   String username = "root";
   String password="123456";
   Connection con = DriverManager.getConnection(url,username,password);
   ```

4. 通过连接对象, 获取SQL语句执行对象:

   ```java
   Statement state = con.createStatement();
   ```

5. 调用方法执行SQL语句:

   ```java
   String sql = "xxxx";
   int result = state.executeUpdate(sql); //这个方法只能执行 insert update delete 的sql语句,不能执行查询语句
   ```

6. 关闭连接, 释放资源

   ```java
   state.close();
   con.close();
   ```

7. 查询语句执行:

   ```java
   String sql = "xxxx"; //查询语句
   ResultSet rs = state.executeQuery(sql); //返回结果集
   //结果集使用完后也需要关闭释放资源
   rs.close();
   ```

8. 防止SQL注入:

   ```java
   String sql = "SELECT * FROM users WHERE username=? AND pwd=?";  // 使用问号做点位符
   PreparedStatement pst = con.prepareStatement(sql);
   pst.setObject(1,"gongxm");
   pst.setObject(2,"123456");
   ResultSet rs = pst.executeQuery();
   ...
   pst.close();//释放资源
   ```

   