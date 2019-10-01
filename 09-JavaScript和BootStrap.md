# JavaScript

#### 1.JavaScript的组成

	- ECMAScript:基本语法
	- BOM:Browser Object Model 浏览器对象模型
	- DOM:Document Object Model 文档对象模型



#### 2.JavaScript的引入

- 页内

  ```javascript
  <script type="text/javascript">
      function test(){
      	alert("TEST");
  	}
  </script>
  ```

- 外部文件

  ```javascript
  <script type="text/javascript" src="../js/main.js"></script>
  ```



#### 3.JavaScript中的数据类型

- 原始类型
  - undifined
  - boolean
  - string
  - number
  - null
- 引用类型



#### 4.JavaScript中的运算符

基本与java语言中的一致, 有一个特殊的, ===只有两边的值和类型都相同时,结果为true



#### 5.JavaScript中的BOM对象中常用的方法

- window
  -  setInterval() : 设置间隔执行内容
  -  setTimeout(): 设置定时执行内容
  -  clearInterval(): 清除间隔执行内容
  -  clearTimeout():清除定时执行内容

- location
  - href: 跳转到指定链接

#### 6.JavaScript中的DOM对象中常用的方法

- 获取元素
  - document.getElementById() 				: 通过ID获取到元素
  - document.getElementsByTagName()  : 通过标签名获取到元素
  - document.getElementsByName()        : 通过name属性获取到元素
- 创建元素:
  - document.createElement()    : 创建元素
  - document.createTextNode()  : 创建文本对象
- 添加节点
  - element.appendChild()	: 在最后添加一个节点
  - element.insertBefore()    : 在某个元素之前插入一个节点
- 删除节点
  - element.removeChild()    : 删除元素



#### 7.JavaScript中的内置对象

- Array : 数组
- Math : 数学相关
- Boolean
- Date : 日期相关
- Number
- String
- Regexp: 正则相关



#### 8.全局函数

- parseInt() 								: 字符串转换成整数
- parseFloat()					         : 字符串转换成小数
- decodeURI()                            : 解码编码过的字符串
- encodeURI()                            : 编码字符串(**不支持特殊字符**)
- decodeURIComponent()       :解码编码过的字符串
- encodeURIComponent()       : 编码字符串(**支持特殊字符**)
- eval(str)                                    : 把一段字符串转换成代码执行



#### 9.JavaScript中的事件(加粗的为常用事件)

| 属性            | 当以下情况发生时，出现此事件   | FF   | N    | IE   |
| :-------------- | :----------------------------- | :--- | :--- | :--- |
| onabort         | 图像加载被中断                 | 1    | 3    | 4    |
| **onblur**      | 元素失去焦点                   | 1    | 2    | 3    |
| **onchange**    | 用户改变域的内容               | 1    | 2    | 3    |
| **onclick**     | 鼠标点击某个对象               | 1    | 2    | 3    |
| **ondblclick**  | 鼠标双击某个对象               | 1    | 4    | 4    |
| onerror         | 当加载文档或图像时发生某个错误 | 1    | 3    | 4    |
| **onfocus**     | 元素获得焦点                   | 1    | 2    | 3    |
| onkeydown       | 某个键盘的键被按下             | 1    | 4    | 3    |
| onkeypress      | 某个键盘的键被按下或按住       | 1    | 4    | 3    |
| onkeyup         | 某个键盘的键被松开             | 1    | 4    | 3    |
| **onload**      | 某个页面或图像被完成加载       | 1    | 2    | 3    |
| onmousedown     | 某个鼠标按键被按下             | 1    | 4    | 4    |
| **onmousemove** | 鼠标被移动                     | 1    | 6    | 3    |
| **onmouseout**  | 鼠标从某元素移开               | 1    | 4    | 4    |
| **onmouseover** | 鼠标被移到某元素之上           | 1    | 2    | 3    |
| onmouseup       | 某个鼠标按键被松开             | 1    | 4    | 4    |
| onreset         | 重置按钮被点击                 | 1    | 3    | 4    |
| onresize        | 窗口或框架被调整尺寸           | 1    | 4    | 4    |
| onselect        | 文本被选定                     | 1    | 2    | 3    |
| **onsubmit**    | 提交按钮被点击                 | 1    | 2    | 3    |
| **onunload**    | 用户退出页面                   | 1    | 2    | 3    |





# JQuery

#### 1.引入JQuery文件

```javascript
<script type="text/javascript" src="../js/JQuery.js"></script>
```



#### 2.基本语法

```javascript
/*以下内容相当于JavaScript中的window.onload()*/
$(function(){
    /*根据ID获取元素对象*/
    var $dv = $("#id");

	//把JQuery对象转换成JavaScript对象
    //第一种方式
    var obj1 = $dv[0];
    
    //第二种方式
    var obj2 = $dv.get(0);

});


//JavaScript对象转换成JQuery对象: 格式 $(js对象)
var d1 = document.getElementById("id");
$(d1).html("xxx");
```



#### 3.JQuery中的常用特效方法

- show()			: 显示
- hide()			 : 隐藏
- slideDown()  : 向下滑动
- slideUp()		: 向上滑动
- fadeIn()		  : 淡入
- fadeOut()	   : 淡出
- animate()       : 自定义动画
- toggle()		   : 一个组件绑定多个函数



#### 4.选择器

- 基本选择器

  - ID选择器

    - 用法: $("#ID")

  - 类选择器

    - 用法: $(".类名")

  - 元素选择器

    - 用法: $("标签名") 

  - 通配符选择器

    - 用法: $("通配符") 

  - 并列选择器

    - 用法: $("选择器1,选择器2,选择器3") 


​    

- 层级选择器

  - 后代选择器: 用空格表示   $("div img")   //获取div里面的**所有**img元素
  - 子元素选择器: 用>表示     $("div>img")  //获取div里面**第一层级**的所有img元素
  - 下一个兄弟元素: 用+表示  $("div+img") //获取div元素后面的**第一个同级**的img元素
  - 后面的所有兄弟元素: 用~表示  $("div~img") //获取div元素**后面**的所有**同级**的img元素
- 过滤选择器

  - :first 第一个
    - $("#id div:first")    // 获取#id元素中的第一个div元素
  - :last  最后一个
    - $("#id:last")  //获取#id中的最后一个元素
  - :odd 奇数个
    - $("#id div:odd")  //获取#id中的奇数的div元素, 索引从0开始
  - :even 偶数个
    - $("#id div:even")  //获取#id中的偶数的div元素, 索引从0开始
  - :eq     指定那一个
    - $("#id div:eq(1)")  //获取#id中的指定位置的div元素, 索引从0开始
- 内容选择器
  - :contains(text) :获取包含指定文本的元素
  - :empty    获取无子（元素）节点的所有元素
  - has(selector) :   $("div:has(p)").addClass("test"); // 给所有包含 p 元素的 **div 元素**添加一个 text 类
  - :parent  : 获取有子元素的指定元素         $("div:parent") //获取有子元素的div元素

  - 属性选择器

    - 用法: 

    ```javascript
    $("[href]") 选取所有带有 href 属性的元素。
    
    $("[href='#']") 选取所有带有 href 值等于 "#" 的元素。
    
    $("[href!='#']") 选取所有带有 href 值不等于 "#" 的元素。
    
    ("[href='.jpg']") 选取所有 href 值以 ".jpg" 结尾的元素。
    ```

  - CSS 选择器

    ```javascript
    $("p").css("background-color","red");
    ```



- 表单选择器

| 选择器                | 实例        | 选取              |
| :------------------- | :---------- | :---------------- |
| :input | $(":input")    | 所有 <input> 元素              |
| :text | $(":text")     | 所有 type="text" 的 <input> 元素     |
| :password | $(":password") | 所有 type="password" 的 <input> 元素 |
| :radio | $(":radio")    | 所有 type="radio" 的 <input> 元素    |
| :checkbox | $(":checkbox") | 所有 type="checkbox" 的 <input> 元素 |
| :submit | $(":submit")   | 所有 type="submit" 的 <input> 元素   |
| :reset | $(":reset")    | 所有 type="reset" 的 <input> 元素    |
| :button | $(":button")   | 所有 type="button" 的 <input> 元素   |
| :image | $(":image")    | 所有 type="image" 的 <input> 元素    |
| :file | $(":file")     | 所有 type="file" 的 <input> 元素     |

- 表单属性
| 选择器                | 实例        | 选取              |
| :------------------- | :---------- | :--------------- |
| :enabled | $(":enabled")  | 所有激活的 input 元素   |
| :disabled | $(":disabled") | 所有禁用的 input 元素   |
| :selected | $(":selected") | 所有被选取的 input 元素 |
| :checked | $(":checked")  | 所有被选中的 input 元素 |



#### 5.jQuery 属性操作方法

| 方法                 | 描述                     |
| :------------------ | :----------------------- |
| addClass() | 向匹配的元素添加指定的类名。        |
| attr() | 设置或返回匹配元素的属性和值。          |
| hasClass() | 检查匹配的元素是否拥有指定的类。     |
| html() | 设置或返回匹配的元素集合中的 HTML 内容。 |
| removeAttr() | 从所有匹配的元素中移除指定的属性。       |
| removeClass() | 从所有匹配的元素中删除全部或者指定的类。 |
| toggleClass() | 从匹配的元素中添加或删除一个类。         |
| val() | 设置或返回匹配元素的值。                 |





#### 6.jQuery 文档操作常用方法

| 方法                         | 描述                  |
| :------------------------- | :----------------------------- |
| addClass() | 向匹配的元素添加指定的类名。                         |
| after()| 在匹配的元素之后插入内容。                           |
| append()| 向匹配元素集合中的每个元素结尾插入由参数指定的内容。 |
| appendTo() | 向目标结尾插入匹配元素集合中的每个元素。             |
| attr() | 设置或返回匹配元素的属性和值。                       |
| before()| 在每个匹配的元素之前插入内容。                       |
| clone() | 创建匹配元素集合的副本。                             |
| empty() | 删除匹配的元素集合中所有的子节点。                   |
| hasClass() | 检查匹配的元素是否拥有指定的类。                     |
| html() | 设置或返回匹配的元素集合中的 HTML 内容。             |
| insertAfter() | 把匹配的元素插入到另一个指定的元素集合的后面。       |
| insertBefore()| 把匹配的元素插入到另一个指定的元素集合的前面。       |
| prepend()| 向匹配元素集合中的每个元素开头插入由参数指定的内容。 |
| prependTo() | 向目标开头插入匹配元素集合中的每个元素。             |
| remove() | 移除所有匹配的元素。                                 |
| removeAttr() | 从所有匹配的元素中移除指定的属性。                   |
| removeClass() | 从所有匹配的元素中删除全部或者指定的类。             |
| replaceAll() | 用匹配的元素替换所有匹配到的元素。                   |
| replaceWith() | 用新内容替换匹配的元素。                             |
| text()| 设置或返回匹配元素的内容。                           |
| toggleClass() | 从匹配的元素中添加或删除一个类。                     |
| val() | 设置或返回匹配元素的值。                             |





#### 7.JQuery的遍历

- 方式一

  ```javascript
  $(function(){
      var arr = new Array("zhangsan","lisi","wangwu");
      $.each(arr,function(index,value){
          //数据操作
      })
  });
  ```

  

- 方式二

  ```javascript
  $(function(){
       var arr = new Array("zhangsan","lisi","wangwu");
      $(arr).each(function(index,value){
           //数据操作
      })
  });
  ```

  



#### 8.JQuery的事件

| 方法                    | 描述               |
| :----------------------------- | :-------------------------- |
| bind() | 向匹配元素附加一个或更多事件处理器               |
| change() | 触发、或将函数绑定到指定元素的 change 事件       |
| click() | 触发、或将函数绑定到指定元素的 click 事件        |
| dblclick()| 触发、或将函数绑定到指定元素的 double click 事件 |
| select()| 触发、或将函数绑定到指定元素的 select 事件                   |
| submit()| 触发、或将函数绑定到指定元素的 submit 事件                   |
| toggle() | 绑定两个或多个事件处理器函数，当发生轮流的 click 事件时执行。 |
| hover() | 一个模仿悬停事件（鼠标移动到一个对象上面及移出这个对象）的方法 |



# BootStrap框架

- 基于HTML CSS JavaScript的前端框架, 主要用于设计响应式页面(方便电脑,PAD和手机使用同一套页面, 会自动根据当前屏幕分辨率调整页面的显示)
- 参考网站: [BootStrap](https://www.bootcss.com/)



#### 1.引入文件

```html
<!-- 最新版本的 Bootstrap 核心 CSS 文件 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

<!-- 可选的 Bootstrap 主题文件（一般不用引入） -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

<!-- 最新的 Bootstrap 核心 JavaScript 文件 -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
```



#### 2.设置标签

```html
 <meta name="viewport" content="width=device-width, initial-scale=1">
```



#### 3.栅格系统

Bootstrap 提供了一套响应式、移动设备优先的流式栅格系统，随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多12列

栅格系统用于通过一系列的**行（row）与列（column）**的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。下面就介绍一下 Bootstrap 栅格系统的工作原理：

- “行（row）”必须包含在 `.container` （固定宽度）或 `.container-fluid` （100% 宽度）中，以便为其赋予合适的排列（aligment）和内补（padding）。
- 通过“行（row）”在水平方向创建一组“列（column）”。
- 你的内容应当放置于“列（column）”内，并且，只有“列（column）”可以作为行（row）”的直接子元素。
- 类似 `.row` 和 `.col-xs-4` 这种预定义的类，可以用来快速创建栅格布局。Bootstrap 源码中定义的 mixin 也可以用来创建语义化的布局。
- 通过为“列（column）”设置 `padding` 属性，从而创建列与列之间的间隔（gutter）。通过为 `.row` 元素设置负值 `margin` 从而抵消掉为 `.container` 元素设置的 `padding`，也就间接为“行（row）”所包含的“列（column）”抵消掉了`padding`。
- 负值的 margin就是下面的示例为什么是向外突出的原因。在栅格列中的内容排成一行。
- 栅格系统中的列是通过指定1到12的值来表示其跨越的范围。例如，三个等宽的列可以使用三个 `.col-xs-4` 来创建。
- 如果一“行（row）”中包含了的“列（column）”大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列。
- 栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ， 并且针对小屏幕设备覆盖栅格类。 因此，在元素上应用任何 `.col-md-*`栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ， 并且针对小屏幕设备覆盖栅格类。 因此，在元素上应用任何 `.col-lg-*`不存在， 也影响大屏幕设备



##### 栅格参数

通过下表可以详细查看 Bootstrap 的栅格系统是如何在多种屏幕设备上工作的。

|                       | 超小屏幕 手机 (<768px)     | 小屏幕 平板 (≥768px)                                | 中等屏幕 桌面显示器 (≥992px) | 大屏幕 大桌面显示器 (≥1200px) |
| :-------------------- | :------------------------- | :-------------------------------------------------- | :--------------------------- | :---------------------------- |
| 栅格系统行为          | 总是水平排列               | 开始是堆叠在一起的，当大于这些阈值时将变为水平排列C |                              |                               |
| `.container` 最大宽度 | None （自动）              | 750px                                               | 970px                        | 1170px                        |
| 类前缀                | `.col-xs-`                 | `.col-sm-`                                          | `.col-md-`                   | `.col-lg-`                    |
| 列数（column）        | 12                         |                                                     |                              |                               |
| 最大列宽（column）    | 自动                       | ~62px                                               | ~81px                        | ~97px                         |
| 槽宽（gutter）        | 30px （每列左右均有 15px） |                                                     |                              |                               |
| 可嵌套                | 是                         |                                                     |                              |                               |
| 偏移（Offsets）       | 是                         |                                                     |                              |                               |
| 列排序                | 是                         |                                                     |                              |                               |



##### 实例：从堆叠到水平排列

使用单一的一组 `.col-md-*` 栅格类，就可以创建一个基本的栅格系统，在手机和平板设备上一开始是堆叠在一起的（超小屏幕到小屏幕这一范围），在桌面（中等）屏幕设备上变为水平排列。所有列（column）必须放在`.row` 内。

![](https://raw.githubusercontent.com/gongxm/JavaEE/master/imgs/bootstrap-栅格系统实例.jpg)

```html
<div class="row">
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
  <div class="col-md-1">.col-md-1</div>
</div>
<div class="row">
  <div class="col-md-8">.col-md-8</div>
  <div class="col-md-4">.col-md-4</div>
</div>
<div class="row">
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4">.col-md-4</div>
</div>
<div class="row">
  <div class="col-md-6">.col-md-6</div>
  <div class="col-md-6">.col-md-6</div>
</div>
```



##### 实例：流式布局容器

```html
<div class="container-fluid">
  <div class="row">
    ...
  </div>
</div>
```



##### 实例：移动设备和桌面屏幕

是否不希望在小屏幕设备上所有列都堆叠在一起？那就使用针对超小屏幕和中等屏幕设备所定义的类吧，即 `.col-xs-*` 和 `.col-md-*`。请看下面的实例，研究一下这些是如何工作的。

![](https://raw.githubusercontent.com/gongxm/JavaEE/master/imgs/bootstrap-栅格系统实例2.jpg)

```html
<!-- Stack the columns on mobile by making one full-width and the other half-width -->
<div class="row">
  <div class="col-xs-12 col-md-8">.col-xs-12 .col-md-8</div>
  <div class="col-xs-6 col-md-4">.col-xs-6 .col-md-4</div>
</div>

<!-- Columns start at 50% wide on mobile and bump up to 33.3% wide on desktop -->
<div class="row">
  <div class="col-xs-6 col-md-4">.col-xs-6 .col-md-4</div>
  <div class="col-xs-6 col-md-4">.col-xs-6 .col-md-4</div>
  <div class="col-xs-6 col-md-4">.col-xs-6 .col-md-4</div>
</div>

<!-- Columns are always 50% wide, on mobile and desktop -->
<div class="row">
  <div class="col-xs-6">.col-xs-6</div>
  <div class="col-xs-6">.col-xs-6</div>
</div>
```



#### 实例：手机、平板、桌面

在上面案例的基础上，通过使用针对平板设备的 `.col-sm-*` 类，我们来创建更加动态和强大的布局吧

![](https://raw.githubusercontent.com/gongxm/JavaEE/master/imgs/bootstrap-栅格系统实例3.jpg)

```html
<div class="row">
  <div class="col-xs-12 col-sm-6 col-md-8">.col-xs-12 .col-sm-6 .col-md-8</div>
  <div class="col-xs-6 col-md-4">.col-xs-6 .col-md-4</div>
</div>
<div class="row">
  <div class="col-xs-6 col-sm-4">.col-xs-6 .col-sm-4</div>
  <div class="col-xs-6 col-sm-4">.col-xs-6 .col-sm-4</div>
  <!-- Optional: clear the XS cols if their content doesn't match in height -->
  <div class="clearfix visible-xs-block"></div>
  <div class="col-xs-6 col-sm-4">.col-xs-6 .col-sm-4</div>
</div>
```



##### 实例：多余的列（column）将另起一行排列

如果在一个 `.row` 内包含的列（column）大于12个，包含多余列（column）的元素将作为一个整体单元被另起一行排列。

![](https://raw.githubusercontent.com/gongxm/JavaEE/master/imgs/bootstrap-栅格系统实例4.jpg)

```html
<div class="row">
  <div class="col-xs-9">.col-xs-9</div>
  <div class="col-xs-4">.col-xs-4<br>Since 9 + 4 = 13 &gt; 12, this 4-column-wide div gets wrapped onto a new line as one contiguous unit.</div>
  <div class="col-xs-6">.col-xs-6<br>Subsequent columns continue along the new line.</div>
</div>
```



##### 响应式列重置

即便有上面给出的四组栅格class，你也不免会碰到一些问题，例如，在某些阈值时，某些列可能会出现比别的列高的情况。为了克服这一问题，建议联合使用 `.clearfix`

![](https://raw.githubusercontent.com/gongxm/JavaEE/master/imgs/bootstrap-栅格系统实例5.jpg)

```html
<div class="row">
  <div class="col-xs-6 col-sm-3">.col-xs-6 .col-sm-3</div>
  <div class="col-xs-6 col-sm-3">.col-xs-6 .col-sm-3</div>

  <!-- Add the extra clearfix for only the required viewport -->
  <div class="clearfix visible-xs-block"></div>

  <div class="col-xs-6 col-sm-3">.col-xs-6 .col-sm-3</div>
  <div class="col-xs-6 col-sm-3">.col-xs-6 .col-sm-3</div>
</div>
```

除了列在分界点清除响应， 您可能需要 **重置偏移, 后推或前拉某个列**

```html
<div class="row">
  <div class="col-sm-5 col-md-6">.col-sm-5 .col-md-6</div>
  <div class="col-sm-5 col-sm-offset-2 col-md-6 col-md-offset-0">.col-sm-5 .col-sm-offset-2 .col-md-6 .col-md-offset-0</div>
</div>

<div class="row">
  <div class="col-sm-6 col-md-5 col-lg-6">.col-sm-6 .col-md-5 .col-lg-6</div>
  <div class="col-sm-6 col-md-5 col-md-offset-2 col-lg-6 col-lg-offset-0">.col-sm-6 .col-md-5 .col-md-offset-2 .col-lg-6 .col-lg-offset-0</div>
</div>
```



##### 列偏移

使用 `.col-md-offset-*` 类可以将列向右侧偏移。这些类实际是通过使用 `*` 选择器为当前元素增加了左侧的边距（margin）。例如，`.col-md-offset-4` 类将 `.col-md-4` 元素向右侧偏移了4个列（column）的宽度。

![](https://raw.githubusercontent.com/gongxm/JavaEE/master/imgs/bootstrap-栅格系统实例6.jpg)

```html
<div class="row">
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4 col-md-offset-4">.col-md-4 .col-md-offset-4</div>
</div>
<div class="row">
  <div class="col-md-3 col-md-offset-3">.col-md-3 .col-md-offset-3</div>
  <div class="col-md-3 col-md-offset-3">.col-md-3 .col-md-offset-3</div>
</div>
<div class="row">
  <div class="col-md-6 col-md-offset-3">.col-md-6 .col-md-offset-3</div>
</div>
```

You can also override offsets from lower grid tiers with `.col-*-offset-0` classes.

```html
<div class="row">
  <div class="col-xs-6 col-sm-4">
  </div>
  <div class="col-xs-6 col-sm-4">
  </div>
  <div class="col-xs-6 col-xs-offset-3 col-sm-4 col-sm-offset-0">
  </div>
</div>
```



##### 嵌套列

为了使用内置的栅格系统将内容再次嵌套，可以通过添加一个新的 `.row` 元素和一系列 `.col-sm-*` 元素到已经存在的 `.col-sm-*` 元素内。被嵌套的行（row）所包含的列（column）的个数不能超过12（其实，没有要求你必须占满12列）。

![](https://raw.githubusercontent.com/gongxm/JavaEE/master/imgs/bootstrap-栅格系统实例7.jpg)

```html
<div class="row">
  <div class="col-sm-9">
    Level 1: .col-sm-9
    <div class="row">
      <div class="col-xs-8 col-sm-6">
        Level 2: .col-xs-8 .col-sm-6
      </div>
      <div class="col-xs-4 col-sm-6">
        Level 2: .col-xs-4 .col-sm-6
      </div>
    </div>
  </div>
</div>
```



##### 列排序

通过使用 `.col-md-push-*` 和 `.col-md-pull-*` 类就可以很容易的改变列（column）的顺序。

![](https://raw.githubusercontent.com/gongxm/JavaEE/master/imgs/bootstrap-栅格系统实例8.jpg)

```html
<div class="row">
  <div class="col-md-9 col-md-push-3">.col-md-9 .col-md-push-3</div>
  <div class="col-md-3 col-md-pull-9">.col-md-3 .col-md-pull-9</div>
</div>
```

#### CSS

#### 组件

#### JavaScript插件

