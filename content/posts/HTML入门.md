---
title: "HTML入门笔记1"
date: 2019-08-15T18:56:52+08:00
draft: false
---


### 一、HTML简介
全称为 HyperText Markup Language 是一种超文本标记语言，最初由Tim Berners-Lee 发明，现在已经更新到HTML5
### 二、Html 起手式
``` html
<!DOCTYPE html> <!--声明文档类型-->
<html lang="en">  <!--声明语言，中文zh-cn-->
<head>
    <meta charset="UTF-8"> <!--可以用于世界上所有语言编码-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
</body>
</html>
```
### 三、HTML章节标签
1. 标题标签: h1-h6 
2. 章节标签: section 
3. 文章标签: article
4. 段落标签: p 
5. 旁支标签: aside
6. 头部标签: header
7. 主要内容: main
8. 脚部标签: footer
9. 其它: div


### 四、标签的全局属性
1. id HTML元素的唯一的 id ,但是如果出现两个，也不会报错，如果id='xxx',js可以通过 直接调用，如果id名同window的全局属性则不可调用
2. class 
3. contenteditable 为true时表示用户可以编辑该内容
4. hidden
5. style 优先级: Js样式 > 内联样式 > css 样式
6. tabindex  通过鼠标tab健访问网页时的顺序，可以不按照顺序，为0时表示最后一个，为-1时表示不会被访问到
7. title 鼠标移到元素上时显示一段文本


### 五、内容标签
* ol + li ----orderlist item
* ul + li ----unorderlist item
* dl + dt + dd ----descriptionlist 
* pre html一般情况下多个空格，tab健，回车均显示一个空格，如果想要全部显示则可加上这个标签
* hr 分割线
* code 编码等宽字体
* hr分割线 br 换行  em 强调内容 strong 重要内容  内联引用 quote 块级引用blockquote
* a 超链接 属性有 href target 

