# XML解析

- Document Object Model 文档对象模型, W3C推荐的解析 xml的方式
- SAX:Simple API for Xml  开源社区XML-DEV 几乎所有的XML解析器都支持它
- 常用开发包
  - JAXP:SUN公司推出的解析标准实现
  - Dom4J: 开源组织推出的解析开发包, 大部分公司在使用, 包括SUN公司

##DOM解析

- 优点:可以方便地操作任意标签和属性
- 缺点:如果xml文件比较大的话, 容易内存溢出

####常用方法

 - Document
   	- Element getRootElement() 获取根元素对象
- Element
  - List elements() 获取所有的子元素
  - List elements(String name) 根据指定的元素名称获取所有的子元素
  - Element element(String name) 根据指定的元素名称,获取子元素对象
  - String elementText(String name): 根据指定的元素名称,获取子元素中的文本
  - String getText() 获取当前元素对象的文本
  - void setText(String text)设置当前元素对象的文本
  - String attributeValue(String name)  根据指定的属性名称获取其对应的值
  - Element addAttribute(String name,String value):根据指定的属性名称和值进行添加或者修改



- Dom4J使用:

```java
SAXReader reader = new SAXReader();
Document doc = reader.read("xml路径");
```



## SAX解析

- 优点:
  - 解析速度快
  - 占用内存少
- 缺点
  - 无法知道当前解析标签（节点）的上层标签，及其嵌套结构，仅仅知道当前解析的标签的名字和属性，要知道其他信息需要自己编码
  - 只能读取XML，无法修改XML
  - 无法随机访问某个标签（节点）

- 使用方式

  ```java
   // 1.获取解析工厂
  SAXParserFactory factory = SAXParserFactory.newInstance();
  // 2.从解析工厂获取解析器
  SAXParser parse = factory.newSAXParser();
  // 3.得到解读器
  XMLReader reader=parse.getXMLReader();
  // 4.设置内容处理器
  reader.setContentHandler(new MyHandler());
  // 5.读取xml的文档内容
  reader.parse("person.xml");
  ```

- 创建Handler

  ```java
  class MyHandler extends DefaultHandler {
      /**
       * @desc 文档解析开始时调用，该方法只会调用一次
       * @param
       * @return void
       */
      @Override
      public void startDocument() throws SAXException {
          System.out.println("----解析文档开始----");
      }
  
      /**
       * @desc 每当遇到起始标签时调用
       * @param uri xml文档的命名空间
       * @param localName 标签的名字
       * @param qName 带命名空间的标签的名字
       * @param attributes 标签的属性集
       * @return void
       */
      @Override
      public void startElement(String uri, String localName, String qName, Attributes attributes) throws SAXException {
          System.out.println("标签<"+qName + ">解析开始");
      }
  
      /**
       * @desc 解析标签内的内容的时候调用
       * @param ch 当前读取到的TextNode(文本节点)的字节数组
       * @param start 字节开始的位置，为0则读取全部
       * @param length 当前TextNode的长度
       * @return void
       */
      @Override
      public void characters(char[] ch, int start, int length) throws SAXException {
          String contents = new String(ch, start, length).trim();
          if (contents.length() > 0) {
              System.out.println("内容为-->" + contents);
          } else {
              System.out.println("内容为-->" + "空");
          }
      }
      /**
       * @desc 每当遇到结束标签时调用
       * @param uri xml文档的命名空间
       * @param localName 标签的名字
       * @param qName 带命名空间的标签的名字
       * @return void
       */
      @Override
      public void endElement(String uri, String localName, String qName) throws SAXException {
          System.out.println("标签</"+qName + ">解析结束");
      }
      /**
       * @desc 文档解析结束后调用，该方法只会调用一次
       * @param
       * @return void
       */
      @Override
      public void endDocument() throws SAXException {
          System.out.println("----解析文档结束----");
      }
  }
  ```

  