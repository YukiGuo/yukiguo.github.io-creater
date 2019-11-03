---
title: "JS函数的执行时机"
date: 2019-09-19T21:26:03+08:00
draft: false
---

#### 1.函数需要经过调用后才能执行
#### 2.函数内涉及到的变量，需要确定调用前变量的数值，不一定是初始值，如果调用后更改变量值也不会影响到函数的返回值
#### 3. 如果函数内部涉及到了setTimeout(()=>{},0),需要先执行for 循环，然后再执行setTimeout
#### 4.for循环 & setTimeout 一起使用时的机制
```
let i=0
for(i=0;i<6;i++){
setTimeout(()=>{console.log(i)},0)
}//打印出6个6 
//因为setTimeout()内的函数会在for循环结束之后再执行，且每次循环都会有一个setTimeOut()
//所以i=6时，循环结束，一起打印出6个6。
```
```
for(let i=0;i<6;i++){
setTimeout(()=>{console.log(i)},0)
}//打印出0-5,因为JS在for 和let 一起用的时候每次循环会创建一个i
```
```
//打印 0-5的其它方法
let i=0;
while (i<6)
{
   console.log(i)
    i++
}
```
