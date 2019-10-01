#DBCP
 ####1. 导入jar包
   - commons-dbcp-1.4.jar
   - commons-pool-1.5.6.jar

####2. 创建数据源对象

   ```java
   BasicDataSource dataSource = new BasicDataSource();
   ```

####3. 设置参数

   - 常用配置项:

     <table>
         <tr>
         	<td>分类</td>
             <td>属性</td>
             <td>说明</td>
         </tr>
         <tr><td rowspan='4'>必须项</td><td>driverClassName</td><td>驱动</td></tr>
         <tr><td>url</td><td>连接地址</td></tr>
         <tr><td>username</td><td>用户名</td></tr>
         <tr><td>password</td><td>密码</td></tr> 
         <tr><td rowspan='4'>可选项</td><td>maxActive</td><td>最大连接数</td></tr>
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
   
   - 配置文件配置
   
     ```properties
     driverClassName=com.mysql.jdbc.Driver
     url=jdbc:mysql://localhost:3306/mydatabase
     username=root
     password=123456
     ```
   
     代码:
   
     ```java
     Properties prop = new Properties();
     prop.load(new FileInpustStream("config.properties"));
     DataSource dataSource = BasicDataSourceFactory.createDataSource(prop);
     ```
   
     

#### 4. 连接池的使用:

   ```java
   QueryRunner qr = new QueryRunner(dataSource); //创建查询对象时, 传入了连接池对象
   qr.query(sql,handler,params);              //在使用的时候就不需要自己获取连接了, 自动获取
   ```

   

# C3P0

#### 1.导入jar包

	- c3p0-0.9.5.4.jar

#### 2.代码配置方式

```java
ComboPooledDataSource cpds = new ComboPooledDataSource();
cpds.setDriverClass( "com.mysql.jdbc.Driver" ); 
cpds.setJdbcUrl( "jdbc:mysql://localhost:3306/mydatabase" );
cpds.setUser("root");                                  
cpds.setPassword("123456");                                  
```



#### 3.xml文件配置方式

```xml
<c3p0-config>
  <default-config>
    <property name="driverClass">com.mysql.jdbc.Driver</property>
    <property name="jdbcUrl">jdbc:mysql://localhost:3306/database2</property>
      <property name="user">root</property>
      <property name="password">123456</property>
  </default-config>

  <named-config name="mainDataBase">
    <property name="driverClass">com.mysql.jdbc.Driver</property>
    <property name="jdbcUrl">jdbc:mysql://localhost:3306/database1</property>
      <property name="user">gongxm</property>
      <property name="password">99886128</property>
  </named-config>
</c3p0-config>
```

代码:

```java
//默认加载类路径下的c3p0-config.xml文件
ComboPooledDataSource cpds = new ComboPooledDataSource();//使用配置文件里的default配置
ComboPooledDataSource cpds = new ComboPooledDataSource("mainDataBase");// 使用配置文件中的mainDataBase配置

```



#c3p0与dbcp区别

- dbcp没有自动回收空闲连接的功能

- c3p0有自动回收空闲连接功能

