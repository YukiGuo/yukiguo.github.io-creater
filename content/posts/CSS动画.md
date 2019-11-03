---
title: "CSS动画"
date: 2019-08-26T16:40:05+08:00
draft: false
---
#### 1.浏览器渲染过程

1. 根据HTML构建 DOM 树
2. 根据 CSS 构建 CSSOM 树
3. 将 DOM 与 CSSOM 合并成一个渲染树
4. 根据渲染树布局Layout(文档流、盒模型、节点的大小及位置)
5. Painting 将各个节点绘制到屏幕上（边框颜色、文字颜色、阴影等）
6. Composite 根据层叠关系展示页面


#### 2.JS更新样式的三种方式
  * 1-6 过程全部重新走一遍----移动节点(div.remove())
  * 跳过Layout 布局----更改背景颜色
  * 跳过 Layout 布局和 Painting 绘制----改变transform

##### 每个属性触发什么流程，可以参考  https://csstriggers.com/
#### 3.CSS动画优化
* 坚持使用 transform 和 opacity 属性更改来实现动画,除此之外更改任何属性始终都会触发绘制，绘制通常是像素管道中开销最大的部分；应尽可能避免绘制，通过层的提升和动画的编排来减少绘制区域
* 使用 will-change 或 translateZ 提升移动的元素
* 避免过度使用提升规则；各层都需要内存和管理开销
* 避免使用 setTimeout 或 setInterval，请使用 requestAnimationFrame

#### 4.transform
 1. 移动 translate(x,y)，translateX|Y|Z(x) ,translate3d(x,y,z) ----x值可以为100px或者50%
 2. 旋转 rotate(angle)， rotateX|Y|Z(angle)， rotate3d(x,y,z,angle)----90deg,0.25turn,1.57rad
 3. 缩放 scale(x,y),scale3d(x,y,z),scaleX|Y|Z(x)
 4. 倾斜 skew(x-angle,y-angle),skewX|Y(angle)


##### 注：
 * inline 元素不支持 transform，需要先转为block
 *  3D 转换 父容器需要设置 perspective(n)
 * translate(-50%,-50%)，可以做绝对定位元素的居中
 * transform:scale(1.2) translate(100px);可以组合使用
 * 一般需要配合 transition 过渡
#### 5.transition 
1. 是 transition-property，transition-duration，transition-timing-function 和 transition-delay 
2. transition-property可以设置两个，并且用逗号隔开，或者all
3. transition-timing-function: linear|ease|ease-in|ease-out|ease-in-out|cubic-bezier(n,n,n,n)
* display:none => display:block 无法过渡，一般可以改为visibility:hidden =>visibility:visible
* 用 transform 实现中间点 .a===transform===.b
.b===transform===.c将 b.c 设置为两个CSS样式，用setTimeout监听并且add classList


#### 6.animation 
##### 1. @keyframes两种方式
1. ` @keyframes animationName
{
from {top:0px;}
to {top:200px;}
}`
2. `@keyframes animationName
{
0%   {top:0px;}
25%  {top:200px;}
50%  {top:100px;}
100% {top:0px;}
}`


##### 2. animation 语法
 * animation 属性是 animation-name，animation-duration, animation-timing-function，animation-delay，animation-iteration-count，animation-direction，animation-fill-mode 和 animation-play-state 属性的一个简写属性形式。
* ` animation-iteration-count: n|infinite-----动画循环次数`
* `animation-direction: normal|reverse|alternate|alternate-reverse|initial|inherit ---- 属性定义是否循环交替反向播放动画，如果动画被设置为只播放一次，该属性将不起作用。`
* `animation-fill-mode: none|forwards|backwards|both|initial|inherit;`
* `animation-play-state: paused|running;`


