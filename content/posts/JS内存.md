---
title: "JS内存"
date: 2019-10-11T23:03:56+08:00
draft: true
---

#### 浏览器的功能
* 发起请求 ---下载HTML---解析HTML---下载CSS---解析CSS----渲染界面---下载JS---解析JS---执行JS
* 功能模块:用户界面，渲染引擎，JS引擎，储存，一般处于不同的线程，JS是单线程
* JS渲染 ，跨线程通信，JS引擎通知渲染引擎，跨线程通信会比较慢，所以JS DOM操作性能差
* chrome使用的JS引擎是V8引擎，C++编写
* JS引擎的功能
    * 编译: 把JS代码翻译为机器能执行的字节码
    * 优化:改写代码，使更高效
    * 执行:执行上面的字节码，或者机器码
    * 垃圾回收: 把JS用完的内存回收，方便之后再次使用
