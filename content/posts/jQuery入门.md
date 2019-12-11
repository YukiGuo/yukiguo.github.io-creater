---
title: "JQuery入门"
date: 2019-11-07T20:21:13+08:00
draft: false
---
####  jQuery获取元素

1. 选择表达式可以是CSS选择器：

```javascript
$(document) //选择整个文档对象
$('#myId') //选择ID为myId的网页元素
$('div.myClass') // 选择class为myClass的div元素
$('input[name=first]') // 选择name属性等于first的input元素
```
2. 也可以是jQuery特有的表达式：

```javascript
$('a:first') //选择网页中第一个a元素
$('tr:odd') //选择表格的奇数行
$('#myForm :input') // 选择表单中的input元素
$('div:visible') //选择可见的div元素
$('div:gt(2)') // 选择所有的div元素，除了前三个
$('div:animated') // 选择当前处于动画状态的div元素
```
#### jQuery取值和赋值

1. 同一个函数，通过判断其参数的个数及类型，实现不同的操作（即重载）的方法来同时实现取值和赋值，常见的取值和赋值函数如下

``` javascript
.html() 取出或设置html内容
.text() 取出或设置text内容
.attr() 取出或设置某个属性的值
.width() 取出或设置某个元素的宽度
.height() 取出或设置某个元素的高度
.val() 取出某个表单元素的值
```

#### jQuery 的链式操作
1. jQuery(选择器)获取元素之后并不将这些元素返回，而是返回一个可以操作这些元素的对象，所以不必多次查找相同的元素，不同操作可以连在一起。jQ 提供了.end()方法，使得结果集可以后退一步：
```javascript
$("#p1")
    .addClass("red")
    .html("hello")
    .attr("title","head")
```

#### jQuery 如何创建元素

* 新元素直接传入jQuery的构造函数
```javascript
$('<p>Hello</p>');
$('<li class="new">new list item</li>');
$('ul').append('<li>list item</li>');
```
#### jQuery 如何移动元素
```javascript
$('div').insertAfter($('p')) //返回div元素
$('p').after($('div'))   //返回p元素

//使用这种模式的操作方法，一共有四对
.insertAfter()和.after()：在现存元素的外部，从后面插入元素
.insertBefore()和.before()：在现存元素的外部，从前面插入元素
.appendTo()和.append()：在现存元素的内部，从后面插入元素
.prependTo()和.prepend()：在现存元素的内部，从前面插入元素
```