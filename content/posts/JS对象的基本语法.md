---
title: "JS对象的基本用法"
date: 2019-09-20T21:26:03+08:00
draft: false
---

##JS 对象基本用法
#### 声明对象的方式
 1. `let obj ={'name':'frank','age':18}`
 2. `let obj =new Object({'name':'frank','age':18})`
 3. `console.log({'name':'frank','age':18})`--不声明直接使用
 
##### 注意
   * 键名是字符串，不是标识符，可以包含任意字符
   * 引号可以省略，省略之后只能写标识符--键名有空格是不可以省略
   * 就算引号省略了，键名还是字符串
   * obj[key]:value  ----[]号表示属性名是变量，先求值，再转字符串
   * 除了字符串，Symbol也可以做属性名
##### 奇怪的属性值
   * 所有属性名都会自动变成字符串
     ``` 
        let obj ={
        1:'a',
        1e2:true,//会自动计算后再转为字符串
        0XXF:false //会自动转化为10进制再转为字符串}     
    ```
#### 隐藏属性

1. JS里每个对象都有一个隐藏属性
2. 这个隐藏属性储存着其共有属性组成的对象的地址
3. 这个共有属性组成的对象叫做原型
4. 也就是说隐藏属性储存着原型的地址

#### 对象的增删改查
##### 删
1. obj.name = undefined ---只删除属性值
2. delete obj.name   ---删除属性名和属性值
3. delete obj['name']  ---删除属性名和属性值
* 'name' in obj --- 检查obj是否含有属性名
* 'name' in obj && obj.xxx ===undefined ---有属性名，但是没有值

##### 查
1. 读取对象自身所有的属性  Object.keys(obj)
2. 读取对象的属性值  Object.values(obj)
3. 读取对象的属性名和属性值  Object.entries(obj) ----得到是length个数组
4. 读取共有属性 console.dir(obj)或者obj.__proto__ (不推荐)
5. 'toString' in obj ---检查是否有这个属性--自身属性和共有属性都算
6. obj.hasOwnProperty('name') ---检查这个属性是否是自身属性
7.两种查看属性的方法
  * 中括号语法：obj['key']----推荐
  * 点语法：obj.key 
  * 其它 ：obj[key]---key值是一个变量是使用此 语法
#####注obj['name'] == obj.name != obj[name] name 是字符串

##### 增改
1. 直接赋值
   * let obj = {name:'frank'}
   * obj.name = 'jane'
   * obj['name'] ='jane'
   * obj.['na'+'me'] ='jane'
   * let key = 'name' obj[key] =='jane'
   * 错误 obj[name] ='jane' --因为name是一个变量
2. 批量赋值
    Object.assign(obj,{1:'p1',2:'p2'})
3. 共有属性的增改(一般不要修改)
     * 无法通过自身修改或增加共有属性
     * 修改原型的共有属性 （不推荐）
        * obj.__proto__.toString ='xxx'
        * window.Object.prototype.toString = 'xxx'
        * obj.__proto__=null ---删除共有属性，值也可以是一个对象
        * Object.create  `let obj = Object.create(common)`  
####'name' in obj和obj.hasOwnProperty('name') 的区别
* 前者自身属性和共有属性都返回true，后者仅仅是自身属性才返回true

   
  
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         
         