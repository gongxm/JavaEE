# HTML

1. HTML文件的基本结构

   ```html
   <!DOCTYPE html>  <!--文档声明, 这个是HTML5的声明-->
   <html>	<!--开始-->
       <head> <!--头部开始-->
           <meta charset="utf-8"/>
           <title>标题</title>
       </head>
       <body>
           <!--主体部分-->
       </body>
   </html><!--结尾-->
   ```

2. 常用标签

  - 字体标签:
  	 	- font:字体标签, 可以控制字体的大小和颜色
  	   	b:字体加粗
  	      	i:斜体
  	      	u:字体加下划线
  
  - 排版标签:	
       - h1-h6:标题标签
       - p:段落标签, 两个段落之间会有一定的空白分开
       - center:内容居中
       - hr:分隔线
  
  - 图片标签:
  	 	img:src指定图片位置, width:指定图片宽度,height:指定图片高度,alt:图片找不到时显示的提示文字
  	
  - 列表标签:
  		
  	- 有序列表:
  	
  	  ```html
  	  <ol>
  	  	<li></li>
  	  	<li></li>
  	  </ol>
  	  ```
  	
  	- 无序列表:
	
  	  ```html
  	  <ul>
  	      <li></li>
  	      <li></li>
  	  </ul>
  	  ```
  	
  	  
  
    - 超链接标签
  
      a : href指定链接路径, target指定打开的方式(当前页面**_self**或者新页面**_blank**)
  
  - 表单标签:
  
    - form: 定义一个表单
  
      - action: 表单提交的地址
      - method: 表单提交的方式, 默认是get方式
  
    - 表单中常用的组件
  
      ```html
      <input type="text"/>		:文本框
      	属性:
      		name:表单元素的名称
      		value:文本框的默认值
      		size:文本框的长度
      		maxlength:文本框最大输入的文本长度
      		readonly:只读文本框
      <input type="password"/>	:密码框
      <input type="button"/>		:按钮,没有功能,需要指定功能
      <input type="submit"/>		:提交按钮,提交表单
      <input type="reset"/>		:重置按钮,用于清空表单中的数据
      <input type="radio"/>		:单选按钮
      <input type="checkbox"/>	:复选框
      <input type="file"/>		:文件选择
      <input type="hidden"/>		:隐藏字段
      
      <select>		:下拉框
          	<option>选项</option>
      </select>
      
      <textarea>文本域,可填写多行文本</textarea>
      ```
  
      ```html
      H5扩展标签:
      <input type="email"/>
      <input type="color"/>
      <input type="date"/>
      <input type="number"/>
      ```
  
  - 框架标签
  
    - frameset:指定页面切割比例
  
    - frame: 指定页面显示内容
  
    - 示例代码:
  
      ```html
      <frameset rows="20%,*">  <!--页面分成两部分,第一部分占20%,第二部分占剩余的大小-->
      	<frame src="top.html" name="top"/>
          <frameset cols="15%,*"><!--页面再次分成两部分,第一部分占15%,第二部分占剩余的大小-->
              <frame src="left.html" name="left"/>
              <frame src="right.html" name="right"/>
          </frameset>
      </frameset>
      ```
  
    - 如何把left.html中链接点击后的页面在right.html中显示:
  
      ```html
      left.html中的链接写成以下方式即可:
      <a href="http://www.baidu.com" target="right">百度一下</a>
      ```
  
  - 块标签:
  
    - **div**: 一个div块独占一行
    - **span**: span块默认在同一行



# css(Cascading Style Sheet : 层叠样式表)

#### CSS基本语法

```css
选择器{属性:值;属性:值;属性:值;...}
```

#### CSS的引入方式

- 行内

  ```css
  <h1 style="color:red;font-size:100px;">标题</h1>
  ```

- 页内

  ```css
  <style type="text/css">
  h1{
      color:red;
      font-size:20px;
  }
  </style>
  ```

  

- 外部文件

  ```html
  <link href="../css/main.css" rel="stylesheet" type="text/css"/>
  ```

#### CSS选择器

##### 元素选择器(标签选择器)

```css
<style type="text/css">
div{
    width:50px;
    height:20px;
}

a{
   font-size:25px;
}
</style>
```

##### ID选择器

```css
<style type="text/css">
#dd{
    color:red;
}
</style>

<div id="dd"></div>
```

##### 类选择器

```css
<style type="text/css">
.divClss{
    color:blue;
}
</style>

<div class="divClass"></div>
```

##### 后代选择器

格式: 标签1 标签2{ xxx }   表示控制的是标签1里面的标签2的样式

```css
<style type="text/css">
/*div 里面所有的的a标签的内容显示红色*/
div a{
    color:red;
}
</style>
```

##### 属性选择器

- 把所有含有title属性的内容显示为红色

```css
*[title]{
    color:red;
}
```

- 把含有href属性的a标签内容显示为红色

```css
a[href]{
    color:red;
}
```

- 把同时含有title和href属性的**a标签**内容显示为蓝色

```css
a[title][href]{
    color:blue;
}
```

- 假设希望将指向 Web 服务器上某个指定url的超链接变成红色

```css
a[href="http://www.gongxm.com/"] {
    color: red;
}
```

- 把多个属性-值选择器链接在一起来选择一个文档

```css
a[href="http://www.gongxm.com/"][title="首页"] {
    color: red;
}
```

- 根据部分属性值选择,需要使用波浪号（~）。

假设想选择 class 属性中包含 important 的元素

```css
/*所有p标签中包含有important类的显示为红色*/
p[class~="important"] {
    color: red;
}
```

假设需要选择img标签中alt文本中包含cover的图片

```css
img[alt~="cover"]{
    border:1px solid blue;
}
```

##### 子串匹配属性选择器

| 类型           | 描述                               |
| -------------- | ---------------------------------- |
| [title^="abc"] | 选择title属性值以abc开头的所有元素 |
| [title$="abc"] | 选择title属性值以abc结尾的所有元素 |
| [title*="abc"] | 选择title属性值中包含abc的所有元素 |

例如: 所有包含指定链接的a标签显示为红色

```css
a[href*="http://www.gongxm.com/"]{
    color:red;
}
```

##### 特定属性选择类型

一般来说，**[属性|="值"]** 可以用于任何属性及其值

假设一个 HTML 文档中有一系列图片，其中每个图片的文件名都形如 ***figure-1.jpg*** 和 ***figure-2.jpg***。就可以使用以下选择器匹配所有这些图像：

```css
img[src|="figure"] {
    border: 1px solid blue;
}
```

| 选择器              | 描述                                                         |
| :------------------ | :----------------------------------------------------------- |
| [attribute]         | 用于选取带有指定属性的元素。                                 |
| [attribute=value]   | 用于选取带有指定属性和值的元素。                             |
| [attribute~=value]  | 用于选取属性值中包含指定词汇的元素。                         |
| [attribute\|=value] | 用于选取带有以指定值开头的属性值的元素，该值必须是整个单词。 |
| [attribute^=value]  | 匹配属性值以指定值开头的每个元素。                           |
| [attribute$=value]  | 匹配属性值以指定值结尾的每个元素。                           |
| [attribute*=value]  | 匹配属性值中包含指定值的每个元素。                           |



##### 子元素选择器

选择div中的a标签

```css
/*这个规则只选择了第一个div中的a标签, 不会选择第二个div中的a标签*/
div>a{
	color:red;
}

<div> <a href="http://www.gongxm.com/">首页</a></div>
<div> <p><a href="http://www.baidu.com/">百度一下</a></p></div>
```

- 跟后代选择器的区别: 
  - 子元素选择器只选择div里面直接跟着的a标签, 不会选择嵌套到p标签里面的a标签
  - 后代选择器是选择div里面的所有a标签, 不管嵌套了多少层

##### 相邻兄弟选择器

- 选择指定元素后面紧跟着的那个元素, 并且两个元素具有相同的父元素:

```css
/*选择h1后面的p元素, 注意:h1元素不会被选择*/
h1+p{
    color:red;
}

<h1></h1>
<p></p> <!--这个p元素会被选中, 后面的不会被选中-->
<p></p>
<p></p>
```





##### 选择器分组

```css
/*所有h1标签,a标签,div标签的内容都显示为红色*/
h1,a,div{
    color:red;
}
```

#### CSS浮动

```css
/*div向右浮动*/
.divClass{
    float:right;
}
```

| 值      | 描述                                                 |
| :------ | :--------------------------------------------------- |
| left    | 元素向左浮动。                                       |
| right   | 元素向右浮动。                                       |
| none    | 默认值。元素不浮动，并会显示在其在文本中出现的位置。 |
| inherit | 从父元素继承 float 属性的值                          |

#### 清除浮动

```css
img{
  float:left;
  clear:both;
}
```

| 值      | 描述                                  |
| :------ | :------------------------------------ |
| left    | 在左侧不允许浮动元素。                |
| right   | 在右侧不允许浮动元素。                |
| both    | 在左右两侧均不允许浮动元素。          |
| none    | 默认值。允许浮动元素出现在两侧。      |
| inherit | 规定应该从父元素继承 clear 属性的值。 |



#### 伪类

- 超链接

```css
a:link {color: #FF0000}		/*未访问链接颜色*/
a:visited {color: #00FF00}	/*访问后链接颜色*/
a:hover {color: #FF00FF}	/*悬浮时链接颜色*/
a:active {color: #0000FF}	/*点击时链接颜色*/

注意:
1.在 CSS 定义中，a:hover 必须位于 a:link 和 a:visited 之后，这样才能生效！
2.在 CSS 定义中，a:active 必须位于 a:hover 之后，这样才能生效！
```



#### CSS中的定位

- position
  - relative:相对定位
  - absolute:绝对定位 
- margin: 外边距
- padding: 内边距