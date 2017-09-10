---
title: 添加Fork me on GitHub 小丝带
date: 2017-08-30 19:27:28
tags: Fork小丝带
categories: hexo干货系列
toc: true
---

**在自己的博客上面挂一个Fork me on GitHub简直是一个装逼神器，更能体现出一个程序员的气质，经过从网上查找，将查找内容整理如下：**

<!-- more -->

## 添加Fork me on GitHub 小丝带

### 操作过程

#### 第一步  创建一个ribbon.ejs

​	**在主题目录下的/layout/_partial下面创建一个ribbon.ejs，输入下面的代码进去**

~~~html
<div class="ribbon">
<a href="https://github.com/your username">Fork me on GitHub</a>
</div>
~~~

#### 第二步  添加代码到after_footer.ejs

​	**接着要在/layout/_partial/after_footer.ejs中加入一行**

~~~js
<%- partial('ribbon') %>
  //此代码的作用是确保这个div能在页面上显示出来。
~~~

#### 第三步  创建ribbon.styl

​	**添加css,hexo可以在主题目录的/source/css/_partial下创建一个ribbon.styl，然后把下面的代码复制进去。**

~~~css
.ribbon {
  background-color: #a00;
  overflow: hidden;
  white-space: nowrap;
  /* top right corner */
  position: fixed;
  right: -50px;
  top: 40px;
  /* 45 deg ccw rotation */
  -webkit-transform: rotate(45deg);
     -moz-transform: rotate(45deg);
      -ms-transform: rotate(45deg);
       -o-transform: rotate(45deg);
          transform: rotate(45deg);
  /* shadow */
  -webkit-box-shadow: 0 0 10px #888;
     -moz-box-shadow: 0 0 10px #888;
          box-shadow: 0 0 10px #888;
}
.ribbon a {
  border: 1px solid #faa;
  color: #fff;
  display: block;
  font: bold 81.25% 'Helvetica Neue', Helvetica, Arial, sans-serif;
  margin: 1px 0;
  padding: 10px 50px;
  text-align: center;
  text-decoration: none;
  /* shadow */
  text-shadow: 0 0 5px #444;
}
~~~

#### 第四步  在style.styl中添加内容

​	**复制一下代码到style.styl（在主题目录下面的\source\css下面）的最后添加一行（针对Hexo博客用户）：**

~~~css
if ribbon
    @import '_partial/ribbon'
~~~

### 效果图

​	**点击 [效果图](http://www.haoeasy.cn)     即可查看。**



