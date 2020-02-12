---
title: "Vue"
date: 2019-12-22T14:23:16+08:00
draft: false
---
#### Vue 两个版本
1. cdn引入：完整版 vue.js , 非完整版 vue.runtime.js (生产环境则后缀名为min.js)
2.  完整版有compiler，非完整版没有compiler，compiler占用40%的内存
3. 使用方法
  * 完整版使用template,会用到编译器
```javascript
new Vue({
  template:`
    <div id="app">{{n}}<button @click="add">+1</button></div>`,
  el:"#app",
    data(){
   return{ n:0}
  },
  methods:{
    add(){this.n+=1}
  } 
})
```
 * 非完整版使用render，不需要编译器
 ```javascript
new Vue({
  el:"#app",
  data(){
   return{ n:0}
  },
  methods:{
    add(){
      this.n+=1
   }},
  render(h){
  return h('div', [this.n,h('button',{on:{click:this.add}},'+1')])
}
})
```
  * 非完整版本还可以使用vue-loader,可以把.vue翻译成h构建方法，但是这种方式SEO不友好
 ```vue
<!--demo.vue文件-->
<template>
    <div>
      <div >{{n}}</div>
        <button @click="add"> +1</button>
    </div>
</template>
<script>
export default {
    data(){
       return{n:0}
    },
    methods:{
        add(){this.n+=1}
    }}
</script>
```
```javascript
import demo from './demo.vue'//引入demo组件
new Vue({
  el:"#app",
//直接渲染demo,不用自己写h函数
  render(h){
     return h(demo)}
})
```
#### template 三种写法
1. 完整版本---1
Html文件
<div id="app">{{n}}
<button></button>
<div>
main.js文件
new Vue({
  el:"#app"
  data:{},
  methods
})

2. 完整版本---2
main.js文件
new Vue({
  el:"#app",
  template:`
  <div >{{n}}
   <button></button>
  <div>
  `
  data:{n:0},
  methods:{}
})

3. vue单文件
<template>
  <div >{{n}}
   <button></button>
  <div>
</template>  
<script>
export default{
  data(){
    n:0
  },
  methods:{},
}
</script>
main.js文件
new Vue({
  render:h=>h(XXX)
}).$mount("#app")

#### template 语法，使用XML语法
#### 指令Directive

##### 展示内容
* 表达式 
  1. {{表达式}}，可以写表达式,运算，调用函数，如果值为undefined或者null,则不显示
  2. <div v-text='表达式'></div>
* HTML内容
   <div v-html='<strong>hi</strong>'></div>
* 展示两个花括号{{}},v-pre不会对模板进行编译
    <div v-pre><{{n}}/div>
##### 绑定属性
*  绑定src <img v-bind:src='x'/>,可以简写为<img :src="x"/>
* 绑定对象 <div :style="{border:'1px solid red',height:'100'}"></div> 100px可以简写为100
#### 绑定事件
* v-on:click=add，简写为@click=add, 后面也可直接接代买@click='n+=1'
* <a  @ click.prevent='x' href="baidu.com"></a>,阻止默认动作并执行新的函数(修饰符)

#### 条件判断
```html
<div v-if='x>0'>第一种请求</div>
<div v-else-if='x===0'>第二种请求</div>
<div v-else>第三种请求</div>
```
#### 循环
```html
<div v-for="(item,index) in array" :key="index">必须有Key
索引{{index}}---值{{item.value}}
</div>
```

#### 显示&隐藏
* v-show
<div v-show ="n%2===0">n是偶数</div>

#### v-model
#### v-slot
#### v-clock
#### v-once
#### 修饰符
* @click.stop 阻止事件传播冒泡
* @click.prevent 阻止事件默认动作
* @click.stop.prevent 
* @keypress.keyCode||keyAlias="fn" ,
* .sy
#### vue构造选项（options）
1. el
  *  挂载点，需要渲染在页面的哪一部分`new Vue({el:'#app')}`
  *  可以使用$mount 代替，``new Vue{()}.$mount('#app')`
2. data
  * data 有函数和对象两种写法，优先使用函数方法，在vue组件中只能写函数方法   
3. methods
  1. 方法和函数的区别，方法是面向对象的(obj.add())，函数是单独的(add())
  2. 两种使用方法 
    * 通过@click="add" 调用
    * 直接在页面中使用{{even()}},展示array中的偶数部分
    ```javascript
    data() {
    return {
       array:[0,1,2,3,4,5,6,7,8,9]
     }},
     methods:{
      even(){return this.array.filter(i=>i%2===0)}
      }

    ```
4. components组件,三种使用方法
    1. 在Vue的实例中引入单文件组件
       * 创建单文件组件demo.vue,在main.js 中通过import引入，`import demo from './demo.vue`
       * vue实例中引入
```javascript
      new Vue =({
        components:{demo:demo},
        template:`<div><demo/></div>`
      })
```  
    2. 直接在main.js中创建components组件
```javascript
    Vue.component('demo2',{
      template:`<div>Demo2</div>`})
      //然后在Vue实例中template引用
```
   3. 在Vue实例中创建组件   
```javascript
   new Vue({
   components:{
     demo3:{
      template:`<div>Demo3</div>`}
```

#### 生命周期钩子
1. beforeCreate
2. created :出现在内存中，不出现在页面中
3. beforeMount
4. mounted :出现在页面中了
5. beforeUpdate
6. updated: 页面更新了
7. activated
8. deactivated
9. beforeDestroy
10. destroyed :从页面中消失，例如v-if指令中，隐藏了组件则会调用


#### props


#### Vue  数据响应式
 1. 如果修改vm.n,则UI 中的n 则会更新成最新的值`const vm = new Vue({data:{n:0}})` 
 2.  利用 Object.defineProperty
 3. Vue data的Bug
   * 只能监听本来就存在的值，如果不存在则会报错
   *  但是如果这个值是对象，那么只会监听到第一层，不会监听到第二层。例如 obj={a:1},但是页面中渲染了<div>{{obj.b}}</div>,则不会报错，如果通过methods的方法设置obj.b的值，页面也不会显示，无法监听本来不存在的obj.b
 4. 解决方法：通过Vue.set,或者this.$set
   * 新增key
   * 自动创建代理和监听(如果没有) 
   ```javascript
   methods:{
     setB(){
       Vue.set(this.obj,b,1)
       //this.$set(this.obj,b,1)
     }
   }
   ```

  5. 数组的变异方法
    1. 数组是特殊的对象，每次增加数组的长度，都需要通过Vue.set
    2. Vue 通过篡改了js Array数组的push,pop,reverse,shift ,unshift,sort ,splice
    ``` javascript
    class VueArray extends Array{
      push(...args){
        const oldLength = this.length
        super.push(...args)
        console.log('push')
        for(let i=oldLength;i<this.length;i++>){
          Vue.set(this,i,this[i])
        }
      }
    }
    const a=new VueArray(1,2,3,4)
    ```

1. getter 
2. setter 



#### computed属性 & watch属性
1. computed  计算属性
   * computed:{
     get(){},
     set(){}
   } 
   * 默认有缓存，如果依赖属性没有变动,则不会重新计算，methods每次都会计算，getter 和setter默认是不会缓存的，是Vue自行做了处理

2. watch 监听属性
```javascript
watch：{
  n(oldValue,newValue){
  }
}
watch:{
  'user.email':function(){

  }
  'user.name':{
    handler(){},
   immediate:true,
   deep:true 
   //watch 监测数据的变化时，对于对象obj={a:"a"},如果将obj.a=b默认为obj没有变化,如果需要obj.a变化了，obj也变化的话就需要设置deep:true
  }
} 
```
* watch内部不能使用箭头函数