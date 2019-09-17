---
title: "HTTP入门"
date: 2019-08-30T21:29:47+08:00
draft: false
---
#### 一、IP Internet Protocol  网际协议
##### 1. 两个作用：
1. 如何定位设备
2. 封装数据报文，以跟其他设备交流

##### 2. 内网&外网
* 内网和外网通过路由器连接
* 内网的设备可以互相访问，但是不能访问外网
* 内网和外网是两个隔绝的空间，只有通过路由器才能互通
* 外网的设备可以相互访问但是无法访问你的内网

##### 3. 特殊的Ip
* 127.0.01 表示自己
* localhost 也表示自己 区别是可以通过C盘hosts文件更改
* 0.0.0.0 不表示任何设备

##### 4. port 端口 总计 共有65535个端口
* HTTP : 80端口
* HTTPS : 443 端口
* FTP : 21 端口


##### 5. IP和域名的对应关系
1. 一个域名可以对应不同的端口 -----负载均衡
2. 一个IP可以对应不同的域名   ------共享主机

##### 6.域名

   1. 域名是由一串用点分隔的字符组成的互联网上某一台计算机或计算机组的名称，用于在数据传输时标识计算机的电子方位。域名可以说是一个IP地址的代称，目的是为了便于记忆后者
   2.  DNS(Domain Name System): 连接域名和IP
       * 浏览器向DNS服务器询问xiedaimala.com对应的IP
       * DNS 回复一个IP
       * 浏览器再向对应的IP端口，80/443发送请求
       * 请求内容是查看 xiedaimala.com的首页


  3. 域名层次   ：域名名由一或多个部分组成，这些部分通常连接在一起，并由点分隔，一个域名的层次结构，从右侧到左侧隔一个点依次下降一层。
     * 顶级域名---二级域名---三级域名
     ![alt 域名层级](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/DNS_schema.svg/1199px-DNS_schema.svg.png)
* IP 查询 命令  ping baidu.com
* 询问 IP 命令  nslookup baidu.com


#### 二、URL Uniform Resource Locator 统一资源定位符
 * 协议+域名或IP+端口+路径+查询字符串+锚点   *https://baike.baidu.com/item/?wd=URL/#3*
   * 查询参数 用一个页面不同的内容
   * 锚点 同一个内容 不同位置-----*锚点不支持中文，锚点不会传到服务器*

#### 三、HTTP HyperText Transfer Protocol  超文本传输协议 ----- 基于TCP 和IP两个协议
1. HTTP请求 -----借助用户代理发送请求(User Agent)


 1.  命令行发出http请求
      * curl -v http://baidu.com
      * curl -s -v https://baidu.com
 2. chrome 地址栏发送请求 
 3. HTTP 规定请求和响应的格式


注意：http server -c -1 -p 80 *-p 80为请求端口*，一个端口只能被占用一次
