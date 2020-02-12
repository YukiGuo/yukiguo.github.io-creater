---
title: "JS对象的类"
date: 2019-09-21T21:26:03+08:00
draft: false
---

#### 构造函数 let obj = New X()
1. 自动创建了一个空对象
2. 自动为空对象关联原型，原型地址指定为X。prototype
3. 自动将空对象作为this关键字运行的构造函数
4. 自动return this

```javascript
{
    // 正方形使用 原型结合更紧密
    let squareList = [];
    let widthList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
    function CreateSquare(width) {
        let obj = Object.create(CreateSquare.squarePrototype)
        obj.width = width
        return obj
    }
    CreateSquare.squarePrototype = {
        getArea() {
            return (this.width * this.width)
        },
        getLength() {
            return (this.width * 4)
        },
        constructor: CreateSquare
    }

    for (let i = 0; i < 12; i++) {
        squareList[i] = CreateSquare(widthList[i])
    }

}

//使用new语法
 function CreateSquare(width) {
        this.width = width
    }
    CreateSquare.prototype.getArea = function () {
        return (this.width * this.width)
    }
    CreateSquare.prototype.getLength = function () {
        return (this.width * 4)
    }
    let square = new CreateSquare(5)
```

#### 构造函数本身X
1. X函数负责给对象本身添加属性
2. X.prototype 对象负责添加新对象的共有属性（X.prototype 存着原型的地址）


#### 如何确定一个对象的原型是什么？
 * 对象.__proto__===其构造函数.prototype
 *  Object.prototype === null,Object 是一个根对象，没有原型

##### 代码规范
1. 构造函数 首字母大写
2. 被构造出的对象首字母小写
3. 构造函数名称一般使用名词，其它函数名称使用动词开头

##### 
1. window 是由Window构造的
2. window.Object 是 Function 构造的
3. 浏览器构造了Function 并且指定它的构造者就是自己

#### Class新语法

```javascript 
class Square{
  constructor(width){
   this.width =width
  getArea(){return this.width*this.width}}
  getLength(){return this.width*4}

}
```
