---
title: "Javascript入门"
date: 2019-09-09T21:26:03+08:00
draft: false
---
#### 1.表达式
1 + 3叫做表达式（expression），指一个为了得到返回值的计算式
#### 2.语句
语句（statement）是为了完成某种任务而进行的操作，例如一行赋值语句。语句和表达式的区别在于，前者主要为了进行某种操作，一般情况下不需要返回值；后者则是为了得到返回值，一定会返回一个值。
#### 3.大小写敏感
#### 4.空格 没有实际意义，不影响断句即可
#### 5.回车 大部分没有意义，但是return 后面不可以加回车，否则会返回undefined
#### 6.标识符 
  * 第一个字母：Unicode 编码字母，$ 或 _ 或中文
  * 第二个字母：上面所有内容和数字


#### 7.注释 : // ------单行注释  ； /*  */ ------多行注释
  * 踩坑注释
  * 为什么代码会写得这么奇怪，遇到了什么bug

#### 8.区块 block 被大括号包裹的多行代码{ }通常与if,for,while联合使用

#### 9.if语句 ------ if (表达式){语句1}else{语句2}
   * { } 在语句只有一句时可以省略，但是不推荐，无{ }的只执行到第一句代码结束(逗号隔开的也为一个语句)
   * if 表达式可以为(a=1)，但是这样会改变a的值。判断建议使用(a===1)
   * 语句1 和语句2 都可以嵌套
```
//语句1嵌套，并且省略了{ }
var a=9
if (a<100>)
    if (1<10>)
    console.log('a<10')
成立    
//语句2 嵌套
if(a>100){
}else{
    if (a<10>){
        console.log('a<10')
     }
}    
//语句2 嵌套省略{ }
if(a>100){
}else if (a<10>){
     console.log('a<10')
}else{
}
// 缩进
if(a = 1)
   console.log('a')
   console.log('a=9') //{}省略，只执行第一句

if(a==9)
console.log('a=1'),console.log('a!=1')   //都执行
   ```   
   
#### 10. 几个表达式

1. 问号冒号表达式:表达式1？语句1:语句2 ------ 例子 a>b?a:b(求大值)
2. && 短路逻辑 A && B && C && D------取第一个假值或者D,并不会取true 或者false
3. || 短路逻辑  A && B && C && D------取第一个真值或者D,并不会取true 或者false


#### 11.switch语句
首先设置表达式 n（通常是一个变量）。随后表达式的值会与结构中的每个 case 的值做比较。如果存在匹配，则与该 case 关联的代码块会被执行。请使用 break 来阻止代码自动地向下一个 case 运行。
大部分时间不可以省略break，少部分可以利用break
```
switch (n){
    case 1:星期一
      break;
    case 2:星期二
      break;
    case 3:星期三
      break;
    case 4:星期四
      break;
    case 5:星期五
      break;
    case 6:星期六
      break;
    case 7:星期日
      break;  
    default: 
      break;     
}
// 同时判断两种情况
switch(n){
    case 1:
    case 3:
      console.log('单数')
      break;
    case 2:
    case 4:
      console.log('双数')  
      break;
}
```
#### 12.while循环------while(表达式){语句}
  1. 判断表达式真假
  2. 当表达式为真，执行语句然后再判断表达式真
  3. 当表达式为假跳出循环
  4. do{语句}while(表达式)
  5. do/while 循环是 while 循环的变体。该循环会在检查条件是否为真之前执行一次代码块，然后如果条件为真的话，就会重复这个循环。
  ```
  //以下是一个死循环，因为浮点数不精确
  var a=0.1
  while(a!==1){
    console.log(a)
    a+=0.1
  }
  ```

#### 13. for 循环------for(语句1；表达式；语句3){循环体}


   1. 先执行语句1，初始化
   2. 判断表达式2真假
   3. 如果为真，执行循环体，再执行语句3
   4. 如果为假，退出循环


```
var d= new Date();
 for(var i=0;i<5;i++){
     setTimeout(function(){console.log(d+'i='+i)},1000)
  }
 //结果
Wed Sep 11 2019 22:57:27 GMT+0800 (中国标准时间)i=5
Wed Sep 11 2019 22:57:27 GMT+0800 (中国标准时间)i=5
Wed Sep 11 2019 22:57:27 GMT+0800 (中国标准时间)i=5
Wed Sep 11 2019 22:57:27 GMT+0800 (中国标准时间)i=5
Wed Sep 11 2019 22:57:27 GMT+0800 (中国标准时间)i=5

var d= new Date();
 for(let i=0;i<5;i++){
     setTimeout(function(){console.log(d+'i='+i)},1000)
  }
//结果
Wed Sep 11 2019 23:05:47 GMT+0800 (中国标准时间)i=0
Wed Sep 11 2019 23:05:47 GMT+0800 (中国标准时间)i=1
 Wed Sep 11 2019 23:05:47 GMT+0800 (中国标准时间)i=2
 Wed Sep 11 2019 23:05:47 GMT+0800 (中国标准时间)i=3
Wed Sep 11 2019 23:05:47 GMT+0800 (中国标准时间)i=4
```   
#### 14.break和continue
  * break跳过当前循环
  * continue 跳过本次循环

#### 15.label  
* foo: {console.log(1);break foo;console.log('不输出');}console.log(2);
* {foo: 1}---表示一个label,不是一个对象，当a={foo: 1}才是一个对象，chorme浏览器句末加分号;