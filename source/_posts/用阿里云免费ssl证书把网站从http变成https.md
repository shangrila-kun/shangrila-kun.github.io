---
title: 用阿里云免费ssl证书把网站从http变成https
date: 2017-11-18 20:32:00
tags: sql
toc: true
categories: database
author: shangrila-kun
---

​	实验室小程序需要调用到全程版接口，但是全程版接口都是http形式，需要http转https，整理了这篇文章，解决这个问题。

​<!--more-->

### 1、登录阿里云后台找到产品与服务、找到证书

[![用阿里云免费ssl证书把网站从http变成https](https://imgsa.baidu.com/exp/w=500/sign=ccb7fe399813b07ebdbd50083cd79113/77c6a7efce1b9d16cabfe379f8deb48f8c5464a9.jpg)步骤阅读](http://jingyan.baidu.com/album/9f7e7ec09c80976f281554f1.html?picindex=1)

### 2、免费购买完成后，在订单里不去信息，输入需要使用Https服务的详细子域名，填写个人信息

![img](http://images2015.cnblogs.com/blog/601899/201703/601899-20170331115509555-875540633.png)

### 3、完成信息后，接下来就是等待审批结果了，审批通过后，下载，

![img](http://images2015.cnblogs.com/blog/601899/201703/601899-20170331115606945-2078304494.png)

据自己服务器的实际情况 ，选择相应类型，完成安装，我的是nginx。

### 4、将下载的两个文件安装到nginx

​	建议安装最新的nginx，nginx依赖

​	nginx依赖以下模块：l  gzip模块需要 zlib 库l  rewrite模块需要 pcre 库l  ssl 功能需要openssl库

#### 4.1.安装pcre

1. 获取pcre编译安装包，在[http://www.pcre.org/](http://www.pcre.org/)上可以获取当前最新的版本
2. 解压缩pcre-xx.tar.gz包。
3. 进入解压缩目录，执行./configure。
4. make & make install

#### 4.2.安装openssl

1. 获取openssl编译安装包，在[http://www.openssl.org/source/](http://www.openssl.org/source/)上可以获取当前最新的版本。
2. 解压缩openssl-xx.tar.gz包。
3. 进入解压缩目录，执行./config。
4. make & make install

#### 4.3.安装zlib

1. 获取zlib编译安装包，在[http://www.zlib.net/](http://www.zlib.net/)上可以获取当前最新的版本。


1. 解压缩openssl-xx.tar.gz包。

2. 进入解压缩目录，执行./configure。

3. make & make install 

   #### 4.4安装nginx

     1.获取nginx，在http://nginx.org/en/download.html上可以获取当前最新的版本。

     2.解压缩nginx-xx.tar.gz包。

   1. 进入解压缩目录，执行./configure
   2. make & make install

   若安装时找不到上述依赖模块，使用--with-openssl=<openssl_dir>、--with-pcre=<pcre_dir>、--with-zlib=<zlib_dir>指定依赖的模块目录。如已安装过，此处的路径为安装目录；若未安装，则此路径为编译安装包路径，nginx将执行模块的默认编译安装。