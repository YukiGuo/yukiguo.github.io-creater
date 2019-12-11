---
title: "ES6常用语法"
date: 2019-11-06T21:32:12+08:00
draft: false
---

---
title: "ES6语法-解构赋值"
date: 2019-11-03T11:02:36+08:00
draft: true
---
### 解构赋值
##### 解构赋值语法是一种 Javascript 表达式。通过解构赋值, 可以将属性/值从对象/数组中取出,赋值给其他变量。
1. 数组

```javascript
     let a,b,c arr=[2,3,5] [a,b,c]=arr//将2,3,5分别赋值给a,b,c
     let [bar, foo] = [1] // foo 解构不成功，为undefined
     let [x, y] = [1, 2, 3] //不完全解构 x=1,y=2
     //将剩余数组赋值给一个变量
     let  [a, ...b] = [1, 2, 3];// a =1,b=[2,3]
```
2. 对象

```JavaScript
//对象的属性没有次序，变量必须与属性同名，才能取到正确的值。
let { a, b } = { a: 'aaa', b: 'bbb' }
// 如果变量名与属性名不一致，必须写成下面这样
let obj = { first: 'hello', last: 'world' }
let { first: f, last: l } = obj;
//对象的解构赋值是下面形式的简写
let { foo: foo, bar: bar } = { foo: 'aaa', bar: 'bbb' }
```
3. 字符串
``` javascript
const [a, b, c, d, e] = 'hello'
let {length : len} = 'hello'
```
4. 交换变量
``` javascript
var a = 1;
var b = 3;
[a, b] = [b, a];
```