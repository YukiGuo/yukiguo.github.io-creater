---
title: "hugo个人博客搭建"
date: 2019-08-18T15:56:52+08:00
draft: false
---

1. 安装Hugo
2. 创建目录：id.github.io-creator  ` hugo new site id.github.io-creator`
3. 设置主题 
```
    $ cd id.github.io-creator
    $ git init
    $ git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
    $ echo 'theme = "ananke"' >> config.toml
  ```
4. 添加第一篇博文 
```
 $ hugo new posts/my-first-post.md
 $ hugo server -D
 ```
6. 创建静态页面
  * 在当前目录创建了一个public文件夹,新建 .gitignore文并,内容填写public，
  并将public单独创建创建本地仓库并且上传github
 ```
$ hugo     
$ cd public
$ git init 
$ git add .
$ git commit -m "开博啦"
$ github页面新建仓库 命名为 id.github.io
$ git remote add origin ssh
$ git push -u origin master
```
* github设置 :setting --GitHub Pages ---master branch ,后面显示的地址则是博客的静态地址


7. 本地id.github.io-creator文件丢失后就不能再编辑博客了，因此需要将此目录上传到github
<hr>

##### 注意:编辑完第二篇博客后上传时，创建public文件时，目录在 id.github.io-creator内，运行hugo








