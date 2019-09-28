1. 导入jar包
   - commons-dbcp-1.4.jar
   - commons-pool-1.5.6.jar

2. 创建数据源对象

   ```java
   BasicDataSource dataSource = new BasicDataSource();
   ```

3. 设置参数

   - 常用配置项:

     <table>
         <tr>
         	<td>分类</td>
             <td>属性</td>
             <td>说明</td>
         </tr>
         <tr>
     	<td rowspan='5'>必须项</td>
         </tr>
         <tr><td>driverClassName</td><td>驱动</td></tr>
         <tr><td>url</td><td>连接地址</td></tr>
         <tr><td>username</td><td>用户名</td></tr>
         <tr><td>password</td><td>密码</td></tr> 
         <tr>
     		<td rowspan='5'>可选项</td>
     	</tr>
         <tr><td>maxActive</td><td>最大连接数</td></tr>
         <tr><td>minIdle</td><td>最小空闲连接数</td></tr>
         <tr><td>maxIdle</td><td>最大空闲连接数</td></tr>
         <tr><td>initialSize</td><td>初始化连接数</td></tr> 
     </table>
   
   - 代码配置:
   
        ```java
     /*必须配置的:*/
     dataSource.setDriverClassName("com.mysql.jdbc.Driver");
     dataSource.setUrl("jdbc:mysql://localhost:3306/mydatabase");
     dataSource.setUsername("root");
     dataSource.setPassword("123456");
     /*可选配置的:*/
     dataSource.setInitialSize(10); 	//初始连接数
     dataSource.setMaxActive(8);		//最大连接数
     dataSource.setMaxIdle(5);		//最大空闲连接数
     dataSource.setMinIdle(1);		//最小空闲连接数
        ```



4. 连接池的使用:

   ```java
   QueryRunner qr = new QueryRunner(dataSource); //创建查询对象时, 传入了连接池对象
   qr.query(sql,handler,params);              //在使用的时候就不需要自己获取连接了, 自动获取
   ```

   