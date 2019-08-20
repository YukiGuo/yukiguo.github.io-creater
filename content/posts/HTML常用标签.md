---
title: "HTML常用标签"
date: 2019-08-16T18:56:52+08:00
draft: false
---


### 一、 a标签 
#### 1. href 属性
 
 1. 网页链接:有三种方式
 1.https://www.baidu.com/  2. https//www.baidu.com/ 3. baidu.com
 2. 路径:绝对路径（httpserver所在目录为根目录），如果是双击打开的网页则是计算机根目录相对路径
 3. 伪协议：
   * javascript:+代码+;点击后触发执行js代码, 如果此处代码为空，会则不做任何操作。href="#"时会跳转到页面顶部，herf=""时会刷新页面
   * href="#xxx"  xxx表示id,跳转到当前页面id为xxx的地方
   * href="mailto:xxx@email.com"
   * href="tel:188xxxxx"


#### 2.  target 指定打开新连接页面的窗口

   * _self 当前页面打开
  * _blank 新建窗口打开
  * _top 最外层打开页面，针对html框架iframe网页
  * parent 父级打开网页，针对html框架iframe网页中，整个网页将重新载入打开目标网址地址
  * xxx 在一个自定义窗口打开页面


#### 3.  download 点击下载页面,一般不用
#### 4.  rel = noopener
### 二、 table 表格标签 
#### 1.table标签：
   table, thead, tbody, tr (table row), th( table head),td(table data)
#### 2. table CSS样式:
* 表格宽度table-layout:fixed,auto
* 边框合并,border-collapse  :collapse 
* 文字对齐: text-align, vertical-align
* 表格内边距:th & td padding 
   
### 三、 img图片标签
* 常用属性：height width src alt  
* 保证图片不变形，可以设置max-width:100%


### 四、 form  表单标签（必须包含一个 type="submit"的按钮）
#### 1.form 属性： 
  * action：被提交到的网页地址
  * autocomplete：on off览器能够根据用户之前在表单里输入的值自动补全 
  * method: 浏览器提交表单的HTTP方式来 post get dialog
  * target

#### 2.input 标签 
  * text ,password, number, tel ,email
  * button, hidden ,file ,search, submit 
  * checkboxes ,radio 可通过name，定义同一组选项
  * section---option下拉列表 ，可以通过对option的selected 设置默认选项
  * textarea 多行文本域