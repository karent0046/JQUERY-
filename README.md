# JQUERY
jQuery 是一套兼容多浏览器的 javascript 脚本库. 核心理念是写得更少，做得更多.
- [DOM对象和JQuery包装集对象](#dom对象和jquery包装集对象)
    - [概念](#概念)
    - [Dom对象](#dom对象)
    - [JQUery包装集和对象](#JQUery包装集和对象)
- [JQuery选择器](#jquery选择器)
    - [基础选择器](#基础选择器)
    - [层次选择器](#层次选择器)
    - [表单选择器](#表单选择器)


## 官网
去官网http://jquery.com/ 下载
## 版本
版本有两种
完整版 : jquery-2.1.4.js -->学习版本

压缩版 : jquery-2.1.4.min.js -->开发版本
## 安装
在页面引入(建议在body后)

```<script src="js/jquery-2.1.4.js" type="text/javascript" ></script>```
## DOM对象和JQuery包装集对象
### 1.概念
通过 js 代码获取的对象都是 dom 对象
而通过 jQuery获取的对象是 jQuery 包装集对象，简称 jQuery 对象;
只有 jQuery 对象才能使用 jQuery 提供的方法。
### 2.Dom对象
javascript 中获取 Dom 对象,Dom 对象只有有限的属性和方法
例如:
```
var div = document.getElementById("testDiv")
var divs = document.getElementsByTagName("div")
```
### 3.JQUery包装集和对象
JQuery中无论对象是一个还是一组,都封装成一个 jQuery 包装集
```
var jQueryObject = $("#testDiv");
```

### 4.Dom 转 jQuery 对象
用$()方法进行包装

```
var domToJquery = $(divDom);
```

### 5.jQuery 对象转 Dom 对象
取数组中的元素转换
一共有两种方式
第一种:
```
var jqueryToDom = divJquery[0];
```
第二种:用遍历方法获得(不常用)
```
divJquery.each(function(index,element){
       console.log(this); // dom对象|
});
```
## JQuery选择器

### 1.基础选择器

1、ID选择器

格式：$("#id属性值") 

获取指定id值的对象(只会获取到第一个id的值)

2、类选择器

格式：$(".class属性值")

获取所有指定class属性值的元素

3、元素选择器

格式：$("元素名/标签名")

获取所有指定标签名的元素

4、通用选择器

格式：$("*")

获取所有的元素的对象

5、组合选择器

格式：$("选择器1,选择器2...")

### 2.层次选择器 Hierarchy
|选择器|名称|举例|
|:---|:---|:---|
|后代选择器|ancestor descendant|$("#parent div")选择id为parent的元素的所有div元素|
|子代选择器|parent > child|$("#parent>div")选择id为parent的直接div子元素|
|相邻选择器|prev + next|$(".blue + img")选择css类为blue的下一个img元素|
|同辈选择器|prev ~ sibling|$(".blue ~ img")选择css类为blue的之后的img元素|

### 3.表单选择器 form

|选择器|名称|举例|
|:---|:---|:---|
|表单选择器|:input|查找所有的input元素：$(":input")；注意：会匹配所有的 input、textarea、select 和 button 元素|
|文本框选择器| :text |查找所有文本框：$(":text")|
|密码框选择器 |:password |查找所有密码框：$(":password")|
|单选按钮选择器 |:radio| 查找所有单选按钮：$(":radio")|
|复选框选择器 |:checkbox| 查找所有复选框：$(":checkbox")|
|提交按钮选择器| :submit| 查找所有提交按钮：$(":submit")|
|图像域选择器| :image| 查找所有图像域：$(":image")|
|重置按钮选择器 |:reset |查找所有重置按钮：$(":reset")|
|按钮选择器| :button|查找所有按钮：$(":button")|
|文件域选择器| :file |查找所有文件域：$(":file")|

## jQuery DOM 操作

### 1.获取属性

|方法|说明|举例|
|:---|:---|:---|
|attr(属性名称) |获取指定的属性值，操作 checkbox 时选中返回checked，没有选中返回 undefined|attr('checked')attr('name')
prop(属性名称) |获取具有 true 和 false 两个属性的属性值| prop('checked')

### 2.设置属性

|方法|说明|举例|
|:---|:---|:---|
|attr(属性名称，属性值) |设置指定的属性值,操作checkbox时选中返回 checked，没有选中返回 undefined|attr('checked',’checked’)attr('name',’zs’)
|prop(属性名称，属性值) |设置具有 true 和 false 两个属性的属性值|prop('checked',’true’)

案例:

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>属性操作</title>
  <script src="../js/jquery-2.1.4.min.js"
  type="text/javascript"></script>
</head>
<body>
  <pre>
  <h5>1.attr()</h5>:设置或者返回元素的属性 ;
  <h5>2.prop()</h5>:设置 具有 true 和 false 两个属性的属性，
  如 checked, selected 或者 disabled。
  </pre>
  <hr />
  <a href="http://www.bjsxt.com" id="a1">尚学堂</a>
  <a href="http://www.sxt.cn" id="a2">速学堂</a>
   <input type="checkbox" name="all" checked="checked"/>全选
</body>
  <script type="text/javascript">
  //获取属性值：attr
  console.log($('#a1').attr('href'));
  console.log($(':checkbox').attr('name'));
  console.log($(':checkbox').attr('checked'));//若未选中显示
  undefined，选中显示 checked
  //获取属性值：prop
  console.log($(":checkbox").prop('checked'));//若未选中显示
  false，选中显示 true
  console.log($('#a2').prop('href'))
  //设置属性值
  $('#a1').attr('href','http://www.shsxt.com');
  $(":checkbox").prop("checked",false);
  //移除属性
  $('#a2').removeAttr('href');
  </script>
</html>
```
### 4.操作元素的样式

|方法|说明|
|:---|:---|
|attr(“class”)|	获取class属性的值，即样式名称|
|attr(“class”,”样式名”)|修改class属性的值，修改样式|
|addClass(“样式名”)|添加样式名称|
|css()|	添加具体的样式|
|removeClass(class)|移除样式名称|

案例:

```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>操作元素的的样式</title>
		<style type="text/css">
			div{
			    padding: 8px;
			    width: 180px;
			}
			.blue{
				background: blue;
			}
			.red {
				background: red;
			}
			.larger{
				font-size: 30px;
				background: pink;
			}
			.green {
				background : green;
			}
		</style>
	</head>
	<body>
		<h3>css()方法设置元素样式</h3>
		<div id="conBlue" class="blue larger">天蓝色</div>
        <div id="conRed">大红色</div>
        <div id="remove" class="blue larger">天蓝色</div>
	</body>
	<script src="js/jquery-1.9.0.min.js" type="text/javascript" charset="utf-8"></script>
	<script type="text/javascript">
		/* attr */
		// 设置元素的class属性（如果属性不存在，则添加属性）
		$("#conRed").attr("class","red");
		
		// 如果属性存在，则修改属性值
		$("#conBlue").attr("class","green");
		
		// addClass() 添加样式，原来的样式保留，如果出现相同的样式，以后面定义样式为准
		$("#conRed").addClass("larger");
		
		// css() 
		// 添加一个具体样式  css("样式名","样式值")
		$("#remove").css("color","red");
		// 同时添加多个具体的样式名 css({"样式名":"样式值","样式名":"样式值"})
		$("#remove").css({"color":"red","font-family":"楷体","background-color":"gray"})
	</script>
</html>
```

## 5.操作元素的内容
|方法|说明|
|:---|:---|
|html() |获取元素的 html 内容|
|html("html 内容")| 设定元素的 html 内容|
|text() |获取元素的文本内容，不包含 html|
|text("text 内容") |设置元素的文本内容，不包含 html|
|val() |获取元素 value 值|
|val(‘值’)| 设定元素的 value 值|

### 6.创建元素
$(‘元素内容’)即可

### 7.添加元素

|方法|说明|
|:---|:---|
|prepend(content)| 在被选元素内部的开头插入元素或内容，被追加的 content 参数，可以是字符、HTML 元素标记|
|$(content).prependTo(selector)|把 content 元素或内容加入 selector 元素开头|
|append(content) |在被选元素内部的结尾插入元素或内容，被追加的 content 参数，可以是字符、HTML 元素标记|
|$(content).appendTo(selector)|把 content 元素或内容插入 selector 元素内，默认是在尾部|
|before()| 在元素前插入指定的元素或内容:$(selector).before(content)|
|after()| 在元素后插入指定的元素或内容:$(selector).after(content)|

prepend和append是在元素的子集内部添加
before和after用于同辈之间添加

### 8.删除元素

|方法|说明|
|:---|:---|
|remove()| 删除所选元素或指定的子元素，包括整个标签和内容一起删|
|empty() |清空所选元素的内容|
