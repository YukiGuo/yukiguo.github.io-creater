---
title: "AJAX"
date: 2019-12-11T21:19:54+08:00
draft: false
---

#### AJAX 简介
  * 全称 Async Javascript And XML
  * AJAX是浏览器上的功能，浏览器在window上加了一个XMLHttpRequest9()的构造函数
  * 用JS通过它来发出请求和接收响应

#### 创建一个AJAX请求,并且请求css文件
1. 创建一个XMLHttpRequest() const request = newXMLHttpRequest() 
2. 调用对象的open方法，request.open("GET",'url')
3. 监听对象的onload和onerror
   * request.onload =(()=>{}) request.onerror =(()=>{})----不建议使用,没有非常好的匹配AJAx
   * 利用 onreadystatechange 优化
```javascript
    request.onreadystatechange = () => {
        if (request.readyState === 4 && request.status === 200) {
          const dom = request.responseXML
          const text = dom.getElementsByTagName("warning")[0].textContent
          console.log(text.trim())
        }
    }

```
4. 发送请求 request.send()
5. 创建style,并设置内容的InnerHTML(request.response)


#### readyState 
##### 返回一个 XMLHttpRequest  代理当前所处的状态
  *  值 0 ----UNSENT   -----          代理被创建，但尚未调用 open() 方法
  *  值 1 ----OPEND     -----         方法已经被调用
  *  值 2 ----HEADERS_RECEIVED  ---- 方法已经被调用，并且头部和状态已经可获得。
  *  值 3 ----LOADING          ----  下载中,responseText 属性已经包含部分数据
  *  值 4 ----DONE              ----  下载操作已完成。
