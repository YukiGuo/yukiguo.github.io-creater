---
title: "CSS布局"
date: 2019-08-25T12:57:09+08:00
draft: false
---
#### 兼容性  gird 布局>flex 布局> float布局
#### 固定宽度布局       
#### 不固定宽度布局
### float布局(专门为IE定制的布局)
 1. 子元素：float:left 和width(最后一个子元素可以不设置宽度会根据内容自动，可以加一个max-width)
 2. 父元素：.clearfix::after{
     content:'';
     display:inline-block;
     clear:both;
 }
 3. IE 6 & 7存在双倍margin bug 解决方法:


    margin-left:10px;_margin-left:5px;


    或者设置：display：block；
#### 响应式布局

### flex 布局 


1. container
  * display:flex | inline-flex;
  * flex-direction:row |column |row-reverse |column-reverse;
  * flex-wrap:nowrap|wrap;
  * justify-content:flex-start|flex-end|center|space-between|space-around|space-evenly;   *主轴对齐方式*
  * align-items:stretch|flex-start|flex-end|center;  *次轴对齐方式*
  * align-content:stretch|flex-start|flex-end|center|space-between|space-around  *主轴多行对齐方式*

  
----
2. items
    * order:num;  *item的显示顺序按照order从小到大显示，默认为0*
    * flex-grow:num ;  *每个item占据的空间，数字越大，空间越大*
    * flex-shrink: num  *空间不够时，数字越大，缩小的程度越大，为0时表示不会被缩小*
    * align-self: stretch|flex-start|flex-end|center *单个item的对齐方式 *

### gird 布局

##### 小技巧

img 标签 添加背景颜色后有多余的东西，可以用vertical-align:top/middle

CSS做页面布局时 border 会干扰页面，这时可以用outline