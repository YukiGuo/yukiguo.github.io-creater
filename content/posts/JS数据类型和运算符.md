---
title: "JS数据类型"
date: 2019-09-16T19:36:33+08:00
draft: false
---

#### 数字 与 字符串
1. 数字与字符串的区别
  * 数字是数字，字符串是字符串，要严谨
  * 数字可以加减乘除，字符串不可以
  * 字符串能用来表示电话号码，数字不行
  * JS中数字是用64位浮点数形式储存的，字符串是用类似UTF8形式储存的(UCS2)

2. 编码方式
  * 48-57表示 1-9 数字
  * 65-90 表示 A-Z
  * 97-122 表示 a-z
3. 编码发展
  * 国标局 GB2312 0000-FFFF 16位 ，两个字节，无法表示生僻字，日韩文 
  *  微软出了 GBK 国标扩 
  * 国标局 GB18030 不兼容GBK
  * 万国码 Unicode 收录13万多字符，全世界通用 ，三个字节以上
  * UTF-8 最少可用8位存一个字符

#### 布尔值 boolean  false true
1. 得到布尔值的三个方法
  * 否定运算 !value
  * 相等运算 == != === !==
  * 比较运算 > >= < <= 
2. 5个falsy值 :相当于false 但是又不是false
    . null undefined 0 NaN ''

#### 数字number
1. 写法：整数 小数 科学计数 八进制 十六进制 二进制
2. 特殊值:
    1.  +0 0 -0 1/0 =infinity 1/+0 =infinity 1/-0 =-infinity
    2.   infinity +infinity -infinity
    3.   NaN 0/0=NaN not a number 是一个数字 NaN==NaN is false
3. 64位浮点数
     * 符号占一位 (正0，负1) 
     * 指数占11位(-1023-1024)
     * 有效数字占 52位(开头的1省略)  
     * 可以储存最大值 Number.Max_value
     * JS的精度  二进制可以存52+1个有效数字即十进制最多存15-16，

#### 字符串 string
1. 储存机制 JS使用UTF-8 定长的两个字节存储
2. 写法 单引号'hello'，双引号"hello" ，反引号`hello`
3. 转义:
   * 字符串内含有引号  'It'\s ok',"It's ok "
   * \n 表示换行
   * \\ 表示 \
   * \r 表示会和
   * \t 表示tab制表符
   * \uFFFF 表示对应的Unicode字符
   * \xFF 表示前256个Unicode字符
4. 多行字符串
   * 反引号 直接换行即可
5.  属性
 * string.length 转义符号不算一个
 * string[index]  从林开始
6. base64转码
  * window.atob Base64编码的字符串转为正常字符串转码
  * window.btoa 正常字符串转码为转Base64编码的字符串


#### null &  undefined  ---JS的两个空值
  1. 如果一个变量声明了，但是没有复制，默认值就是undefined
  2. 如果一个函数 ，没有写return ,默认返回值是undefined
  3. 前端程序员习惯把对象的空值写为null，非对象的空值写为undefined，但这不是规范 


#### 符号 symbol
#### 对象object(包括 数组 日期) 
#### 变量声明 声明时既指定了值，又指定了类型
  1. 三种声明方式
   * var a = 1 过时的，不好用的方式
   * let a = 1  新的更合理的方式
   * const a =1 声明是必须赋值，且不能更改
   * a = 1 赋值方式，或者会在未声明变量时是会变全局变量
  2. let
    * 遵循块作用域 ，使用范围不能超出块级作用域{}
    * 在同一个作用域内不能重复声明
    * 声明时可以赋值，也可以不赋值
    * 必须先声明再使用，否则会报错
    * 全局声明的let变量，不会变成window 的属性
    * for 循环内使用let
  3. const
    * 声明时必须赋值，赋值后不能更改
    * 其它和let一致  
#### 类型转换
  1. 数字转为字符串
    * String() bug :位数太多会变成科学计数法
    * n + ''
  2. 字符串转为Number
    * Number(s)
    * s - 0
    * + s  
    * parseInt('123')  ==  变成整数
  3. 转为布尔值
    * Boolean(1)
    * !!(1) 
  4. 任何值转为string
    * .toString() 
    *  1.toString()会报错，因为默认为小数，可以改为1..toString() 或者 (1).toString 1 .toString()