---
title: "JSON"
date: 2019-12-11T22:17:44+08:00
draft: false
---

#### 全称JavaScript Object Notation,是一种标记语言
#### JSON的基本数据类型
1. number 
2. string 只支持双引号
3. boolean
4. object
5. array
6. null


#### 两个方法
1. JSON.parse() , 用来解析JSON字符串，转化成JavaScript对应的数据类型
2. JSON.stringfy() ,用来将 JavaScript 值（对象或者数组）转换为一个 JSON 字符串
3. 因为 JS的数据类型多余JSON数据,所以不一定能成功,如果出错可以用try{}catch(error){}捕获错误
