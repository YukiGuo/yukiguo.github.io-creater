---
title: "Webpack入门"
date: 2019-12-07T21:33:04+08:00
draft: false
---

#### webpack的作用
1. 转译代码(ES6转为ES5，SCSS转为CSS),可以使得低版本的浏览器也兼容代码
2. 构建build
3. 代码压缩
4. 代码分析


#### webpack 安装
``` 
mkdir webpack-demo
cd webpack-demo
npm init -y  ---创建一个package.json文件
npm install webpack webpack-cli --save-dev
```

#### HTTP 缓存
* 浏览器在加载网址时，需要加载对应的css,js等文件，如果设置了响应头的ResponseHeader的Cache-Control:public,max-age=缓存期限，且js或者css的文件名没有改动，则会直接从内存读取，不会重新下载，缩短了加载的时间
* index.html的数据不应该缓存，这样可以发现及时发现js 或者css的更新，使得用户获取到最新的页面


#### webpack 转译JS
1.  `npx webpack`
2. 配置
``` javascript
const path = require('path');
module.exports = {
  mode: "production",//开发模式 development
  entry: './src/index.js',//入口文件
  output: {
    filename: 'main.js'?"index.[contenthash].js",//出口文件
    // 文件名中的hash,为了使得更改内容时自动更新出口JS文件的文件名，
    //文件名改变时就不再使用缓存，重新下载新文件
  },
};
```

#### webpack生成HTML文件
1. 安装HtmlWebpackPlugin插件 `npm install --save-dev html-webpack-plugin`
2. 设置config.js
``` javascript
var HtmlWebpackPlugin = require('html-webpack-plugin');
module.exports = {
  plugins: [new HtmlWebpackPlugin(
       { title: "XXXX", //设置网页title，
      template: "src/assets/index.html" 
      // 设置网页的模板路径，没有此项的话也会在dist目录生成一个index.html
      //次文件的title内容可以设置为><%= htmlWebpackPlugin.options.title %>
      //则会根据此配置的title更新
       }
  )]
};
```


####  webpack引入CSS
1. 在js 文件中引入css   ` import css from 'file.css' `


##### 方法1.直接将css内容写到 style标签中
2. 安装 css-loader和style-loader   ```npm install --save-dev css-loader/style-loader`
3. 配置 config.js 
``` javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
};
```


##### 方法2.将css抽取成文件，并在index.html中引入
2. 安装MiniCssExtractPlugin插件 `npm install --save-dev mini-css-extract-plugin`
3. 配置 config.js 
``` javascript
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
module.exports = {
  plugins: [
    new MiniCssExtractPlugin({
      filename: '[name].[contenthash].css',
      chunkFilename: '[id].[contenthash].css',
      ignoreOrder: false, // Enable to remove warnings about conflicting order
    }),
  ],
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          {
            loader: MiniCssExtractPlugin.loader,
            options: {
              publicPath: '../',
              hmr: process.env.NODE_ENV === 'development',
            },
          },
          'css-loader',
        ],
      },
    ],
  },
};
```

#### 引入SASS,Less,Stylus
1. SASS 安装 sass-loader,和dart-sass `npm install sass-loader dart-sass webpack --save-dev`
1. Less 安装 less 和less-loader
1.  Stylus 安装 stylus 和stylus-loader
2. 配置 config.js 

``` javascript
module.exports = {
  module: {
    rules: [
      {
        //SASS
        test: /\.s[ac]ss$/i,
        use: [
          'style-loader',
          'css-loader',
          {
            loader:'sass-loader',
             options:{implementation:require('dart-css')}
          }
        //Less
        // test: /\.less$/,
        // use: ['style-loader','css-loader','less-loader']
         //Stylus
        // test: /\.styl$/,
        // use: ['style-loader','css-loader','stylus-loader']
        ],
      },
    ],
  },
};
```


#### webpack 引入图片
1. js中引入图片` import png from './xxxx'`
2. 安装file-loader `npm install file-loader --save-dev`
3. 配置 config.js ; file-loader会自动给图片文件名加hash
```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(png|jpe?g|gif)$/i,
        use: [
          {
            loader: 'file-loader',
          },
        ],
      },
    ],
  },
};
```

#### 懒加载
1. 动态import可以像调用函数一样来动态的导入模块。以这种方式调用，将返回一个 promise 。js中引入一个需要懒加载的js `import(./lazy.js)`
```javascript
const promise =import('/modules/my-module.js')\
promise.then((module) => {
  });
```

#### plugin和loader 的区别
* loader 加载器，用来加载资源文件，例webpack中的内置bable-loader，可以加载JS，将高版本的JS转为低版本的JS,以便于更多浏览器支持，css-loader和style-loader 将css加载为页面的style标签。支持一对一的文件加载
* plugin 插件，用来扩展 Webpack 功能，plugin的功能更加的丰富，而不仅局限于资源的加载。例如MiniCssExtractPlugin,将css抽取成文件，并在html中引入


#### 不同模式下使用不同的css打包方式
1. 可以新建文件config.common.js 用来储存共同的属性,config.prod.js储存 产品发布模式时的配置 ,config.deve.js储存 产品开发模式时的配置
2. config.prod.js 或者 config.deve.js 通过...来继承common的属性


#### build
* 因为webpack时会创建一个新的dist目录，所以先移除dist目录，创建脚本 `rm -rf dist && webpack` 


#### webpack server--dev
1. 安装 `npm install --save-dev webpack-dev-server`
2. 配置 
```javascript
  module.exports = {
   devServer: {    contentBase: './dist',
  },
```
3. 脚本配置package.json

``` javascript
  {
   "start": "webpack-dev-server --open",
},
```
4. 运行 `npm run start`

#### github一键部署