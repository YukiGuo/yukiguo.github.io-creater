---
title: "MVC浅析"
date: 2019-12-22T20:17:46+08:00
draft: false
---
#### MVC
1. M 模型（Model），负责操作所有数据
2. V 视图（View），负责所有UI界面
3. C 控制器 Controller），连接交互和数据模型的一个控制器
``` javascript
import './app1.css'
import $ from 'jquery'

const eventBus = $(window)
// 数据相关都放到m
const m = {
  data: {
    n: parseInt(localStorage.getItem('n'))
  },
  create() {},
  delete() {},
  update(data) {
    Object.assign(m.data, data)
    eventBus.trigger('m:updated')
    localStorage.setItem('n', m.data.n)
  },
  get() {}
}
// 视图相关都放到v
const v = {
  el: null,
  html: `
  <div>
    <div class="output">
      <span id="number">{{n}}</span>
    </div>
    <div class="actions">
      <button id="add1">+1</button>
      <button id="minus1">-1</button>
      <button id="mul2">*2</button>
      <button id="divide2">÷2</button>
    </div>
  </div>
`,
  init(container) {
    v.el = $(container)
  },
  render(n) {
    if (v.el.children.length !== 0) v.el.empty()
    $(v.html.replace('{{n}}', n))
      .appendTo(v.el)
  }
}
// 其他都c
const c = {
  init(container) {
    v.init(container)
    v.render(m.data.n) // view = render(data)
    c.autoBindEvents()
    eventBus.on('m:updated', () => {
      console.log('here')
      v.render(m.data.n)
    })
  },
  events: {
    'click #add1': 'add',
    'click #minus1': 'minus',
    'click #mul2': 'mul',
    'click #divide2': 'div',
  },
  add() {
    m.update({n: m.data.n + 1})
  },
  minus() {
    m.update({n: m.data.n - 1})
  },
  mul() {
    m.update({n: m.data.n * 2})
  },
  div() {
    m.update({n: m.data.n / 2})
  },
  autoBindEvents() {
    for (let key in c.events) {
      const value = c[c.events[key]]
      const spaceIndex = key.indexOf(' ')
      const part1 = key.slice(0, spaceIndex)
      const part2 = key.slice(spaceIndex + 1)
      v.el.on(part1, part2, value)
    }
  }
}
```

#### EventBus
1. 对各组件进行监听，和实现各组件进行通信
  * EventBus.on（）监听事件
  * EventBus.trigger（）触发事件
``` javascript
//eventBus 触发 m:updated
eventBus.trigger('m:updated')
//监听 m:updated，当 m:updated 触发时，执行事件
eventBus.on('m:updated',()=>{
     v.render(m.data.n)
 })
```

#### 表驱动编程

表驱动法是一种编程模式，从表里面查找信息而不是使用逻辑语句（if…else…switch），当是很简单的情况时，用逻辑语句很简单，但如果逻辑很复杂，再使用逻辑语句就很麻烦了。
比如查找一年中每个月份的天数，如果用表驱动法，完全不需要写一堆if…else…语句，直接把每个月份的天数存到一个数组里就行了，取值的时候直接下标访问，最多针对二月判断一下闰年。
#### 模块化
将具有不同的功能的js封装起来，独立在不同的文件中，最后在入口文件中一起引入。