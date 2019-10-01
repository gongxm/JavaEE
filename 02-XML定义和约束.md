# 01.XML文件的组成部分

#####  文档声明

 - 文档声明必须写在第一行

 - 文档声明中常用的属性

   	- 版本: version (目前只有1.0)
   	- 字符编码: encoding (一般是UTF-8, 注意文件保存要和声明一致)
   	- 文档是否独立(有没有依赖其他XML文件): standalone (独立的话写yes)
   	- 示例:

   ```xml
   <?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
   ```

   

##### 元素

- 标签
   - XML中用标签表示元素和属性
   - 标签不能交叉嵌套
   - 一个XML文件中只能有一个根标签
   - 标签有两种写法
      - 有标签体: <name>张三</name>
      - 没有标签体的: <Person name="zhangsan" age="23" />

- 标签名称规范:

  - 可以包含字母,数字,减号,下划线和英文句点
  - 严格区分大小写
  - 只能以字母或下划线开头
  - 不能以xml(或XML, Xml等)开头
  - 名称字符之间不能有空格或制表符或冒号

- 元素表示一个对象, 一个XML文件中可以有多个对象

  

##### 元素属性

- 元素属性表示一个对象中的属性, 一个元素(对象)中可以有多个属性, 每个属性都有对应的属性名和属性值
- 属性值一定要用引号(单引号或双引号)引起来
- 属性名也是标签名
- 属性不能重复

##### 注释

示例:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!-- 
	注释:
		XML的注释只能写在文档声明的下面
		XML的注释不能嵌套!
-->
```



##### CDATA区

- CDATA是Character Data的缩写

- 作用: 标识该内容为普通文本,让解析器不要解析这部分内容

- 语法: <![CDATA[内容]]>

- 示例:

  ```xml
  <![CDATA[<name>zhangsan</name>]]>
  ```

  

##### 特殊字符

| 特殊字符 | 替代符号   |
| -------- | ---------- |
| &        | &amp;amp;  |
| <        | &amp;lt;   |
| >        | &amp;gt;   |
| "        | &amp;quot; |
| '        | &amp;apos; |



##### 处理指令(PI:Processing Instruction)

- 作用: 用来指挥软件如何解析XML文档的

- 语法: 必须以**"<?"**开头, 以**?>**结尾

- 常用处理指令:

  - XML声明

    ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    ```

  - xml-stylesheet指令

    ```xml
    <?xml-stylesheet type="text/css" href="main.css"?>
    ```

    

# 02.XML约束

- 作用: 约束xml书写的规范



## DTD约束

#### DTD文件定义:

  创建一个dtd文件: book.dtd

  ```xml-dtd
  <?xml version="1.0" encoding="UTF-8"?> 
  <!--这里的编码只能是UTF-8-->
  <!ELEMENT 书架(小说+)> 
  <!--这里声明根元素是书架, 书架中的元素是小说对象, +表示必须至少有一个小说对象, 可以有多个-->
   <!ELEMENT 小说(名称,作者,价格)> 
  <!--这里声明小说对象中必须有名称,作者,价格这三个属性-->
    <!ELEMENT 名称(#PCDATA)> 
  <!--这里声明名称属性的类型是普通文本类型-->
    <!ELEMENT 作者(#PCDATA)>
    <!ELEMENT 价格(#PCDATA)>
  ```

#### 引用方式:

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE 书架 SYSTEM "book.dtd"> <!--在这里引用dtd文件-->
  <书架>
  	<小说>
  		<名称>西游记</名称>
  		<作者>吴承恩</作者>
  		<价格>99.9</价格>
  	</小说>
  </书架>
  ```

#### 注意事项

  - 引用本地DTD文件的格式

    ```xml-dtd
    <!DOCTYPE 根元素名称 SYSTEM "DTD文档路径">
    
    例如:
    <!DOCTYPE 书架 SYSTEM "book.dtd">
    ```

    

  - 引用外部DTD文件的格式

    ```xml-dtd
    <!DOCTYPE 根元素名称 PUBLIC "DTD名称" "DTD文档的URL">
    
    例如:
    <!DOCTYPE web-app PUBLIC "-//Sun Microsystem,Inc.//DTD Web Application 2.3//EN" "http://java.sun.com/dtd/web-app_2_3.dtd">
    ```

  - DTD语法:

    - <ELEMENT 元素名称 使用规则>
      - 使用规则:
        - (#PCDATA): 指元素的主体内容只能是普通的文本(Parsed Character Data)
        - EMPTY:元素的主体为空,例如: <br/>
        - ANY: 元素的主体为任意类型
        - (子元素): 元素中包含的子元素
          - 如果子元素用逗号分开,必须按照声明顺序去编写XML文档
            - 例如: <!ELEMENT book(name,author,price)
          - 如果子元素用"|"分开, 说明任选其一
            - 例如: <!ELEMENT img(jpg|png|gif)
          - 用+ *  ? 表示元素出现的次数
            - 如果元素后面没有这些符号, 表示**必须且只能出现一次**
            - +:表示至少出现一次, 可以出现多次
            - *:表示可以出现0到多次
            - ?:表示只能出现0次或1次

#### DTD中定义属性

 - 使用ATTLIST关键字声明属性
   
  - 语法:
    
      ```xml-dtd
      <!ATTLIST 元素名
      	属性名1 属性值类型 设置说明
      	属性名2 属性值类型 设置说明
      	...
      >
      ```
    
- 属性值类型:

  - CDATA

  - 枚举:表示只能从枚举列表中任选其一, 例如:

    ```xml-dtd
<!ATTLIST 肉 品种(鸡肉|牛肉|猪肉|鱼肉) "鸡肉">
    ```

  -  ID:表示属性的取值不能重复

- 设置说明

  - \#REQUIRED:表示该属性必须出现

  - \#IMPLIED:表示该属性可有可无
  - \#FIXED:表示属性的取值为一个固定值,语法: \#FIXED "固定值"

  - 直接值:表示属性的取值为该默认值

    ```dtd
    <!ATTLIST book
    	name CDATA #REQUIRED 
    	author CDATA #IMPLIED
    >
    ```


​      

## Schema约束

- 更符合XML语法结构
- 对名称空间支持非常好
- 可以支持更多的数据类型,并支持用户自定义新数据类型
- Schema文档称为**模式文档**, 相当于一个类
- 对应的xml文档称为**实例文档**,相当于一个对象
- 名称空间相当于类的**包名**

#### XML Schema定义

创建一个文件: book.xsd

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema 
	<!--标准的名称空间-->
	xmlns:xs="http://www.w3.org/2001/XMLShema"
	<!--将该schema文档绑定到http://www.gongxm.com名称空间-->
	targetNamespace="http://www.gongxm.com"
>
<!--声明根元素名称-->
<xs:element name="书架">
    <!--声明根元素的内容是复杂类型的-->
    <xs:complexType>
        <!--声明子元素必须按顺序写属性内容,并且数量是不限制的-->
        <xs:sequence maxOccurs="unbounded">
        	<!--声明子元素名称-->
            <xs:element name="书">
            	<!--声明元素内容是复杂类型-->
                <xs:complexType>
                	 <!--声明必须按顺序写属性内容-->
                    <xs:sequence>
                    	<!--声明属性名称和类型-->
                        <xs:element name="书名" type="xs:string"/>
                        <xs:element name="作者" type="xs:string"/>
                        <xs:element name="价格" type="xs:string"/>
                    </xs:sequence>
                </xs:complexType>
            </xs:element>
        </xs:sequence>
    </xs:complexType>
</xs:element>
</xs:schema>	
```



#### XML Schema的使用

```xml
<?xml version="1.0" encoding="UTF-8"?>
<gongxm:书架
           xmlns:gongxm="http://www.gongxm.com"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://www.gongxm.com book.xsd"
           >
    <书>
        <书名></书名>
        <作者></作者>
        <价格></价格>
    </书>   
</gongxm:书架>
```

