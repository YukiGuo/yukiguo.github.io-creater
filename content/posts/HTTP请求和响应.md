---
title: "HTTP请求和响应"
date: 2019-12-11T20:08:52+08:00
draft: false
---
#### 请求

1. 请求行，请求动词/路径 版本号
  *  请求动词
     * 共有GET/POST/PUT/PATCH/DELETE5中
     * GET用来获取内容，POST用来上传内容

2. 请求头
  1. HOST 域名+端口号
  2. Accept text/html(默认值)
  3. Content-Type:请求体的格式

3. 请求体(格式由Content-Type指定)
  
4. 注意
  * GET请求没有请求体
  * 请求头和请求体中间有一个回车  
  * 大小写不敏感，但是JS敏感
5. 发出请求
  1. 用 curl 发出请求
    1. curl -v http://localhost:8888
    2. 设置请求动词 :  curl -v -X POST http://localhost:8888
    3. 设置路径和查询参数  curl -v -X POST http://localhost:8888/xxx?wd=hi (不能加锚点,锚点不会发到服务器 )
    4. 设置请求头
       * -H 'Name: Value' 或者 --header 'Name: Value'
       * curl -v -X POST -H 'Accept:text/html'http://localhost:8888
    5. 设置请求体
       * -d '内容'或者 --data'内容'
6. Node.js 读取请求
  1. 读取请求动词 request.method
  2. 读取路径 
     * request.url,带查询参数
     * request.path,不带查询参数
     * request.query,只有查询参数
  3. 读取请求头
     * request.Headers['Accept']
  4. 读取响应体     


#### 响应
1. 状态行
  * 协议名/版本 状态码 状态码字符串
2. 响应头
  * Content-Type:响应体的格式
3. 响应体  

4. 注意
 * 响应头和响应体中间有空格
 * [状态码明细](https://www.w3.org/Protocols/rfc2616/rfc2616-sec6.html)

5. Node.js 设置响应
   1. 设置状态码 response.statusCode =333
   2. 设置响应头 response.setHeader("Content-Type","text/html;charset=utf-8")
   3. 设置响应体 response.write("内容"),可追加分两次写