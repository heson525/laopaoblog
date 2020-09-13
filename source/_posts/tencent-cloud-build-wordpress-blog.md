---
title: 在腾讯云服务器上搭建WordPress博客
abbrlink: 44528
date: 2020-08-12 09:55:11
tags:
	- 博客
	- 搭建
	- WordPress
	- 云服务器
categories: WordPress
description:
thumbnail: https://pic.heson10.com/img/timg%5B1%5D
---
{%note ,准备做个WordPress主题演示站点，后期更新制作的主题会在此演示，准备找个便宜的云服务器作为载体。看到腾讯新用户有活动（99元/年），果断购入。开始搭建Wordpress博客。此篇文章就是边搭边写而来的。 %}<!--more-->

## 整体思路

- 购买云服务器
- SSH登陆，使用宝塔面板创建运行环境
- 搭建WordPress

## 教程

### 登入腾讯云

登陆后可以看到已经购买的实例，推荐买Linux版的实例，方便操作：

![image-20200812101234343](https://pic.heson10.com/img/image-20200812101234343.png)

### 重置密码

开始创建的随机密码太难记了，重新创建一个自己记得住的密码：

![image-20200812101337246](https://pic.heson10.com/img/image-20200812101337246.png)

### 登陆SSH终端

点击登陆按钮，输入刚才自己设置的密码，进入SSH终端

![image-20200812101829186](https://pic.heson10.com/img/image-20200812101829186.png)

### 创建宝塔面板

- 宝塔官网：https://www.bt.cn/

- 点击 `Linux版` 按钮，点击立即安装，会出现[安装教程](https://www.bt.cn/bbs/thread-19376-1-1.html)，找到Centos**（购买的时候会选择此系统）**安装命令

- 在终端输入安装代码（**右键→粘贴**），然后回车：

  ```shell
  yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh
  ```

  ![ssh](https://pic.heson10.com/img/ssh.gif)

- 等待安装完毕，记住登陆网址、用户名和密码（下图红色部分）

  ![image-20200812102623568](https://pic.heson10.com/img/image-20200812102623568.png)

### 登陆宝塔面板

- 在浏览器里输入 `外网面板地址` ，然后输入`用户名`和`密码`

- 登陆后直接安装LNMP环境：

  ![image-20200812102931833](https://pic.heson10.com/img/image-20200812102931833.png)

- 在等待安装的过程中，在左侧→面板设置栏目里面，修改**登陆地址、用户名和密码**，方便自己记录

  ![image-20200812103217643](https://pic.heson10.com/img/image-20200812103217643.png)

### 获取WordPress

中文官方下载地址：https://cn.wordpress.org/download/

我下载的是：**WordPress 5.4.2** 版本

![image-20200812103544039](https://pic.heson10.com/img/image-20200812103544039.png)

下载后解压缩，找到解压缩后的文件夹。

### 添加一个网站

- 在域名解析商那，把你自己的域名解析到面板左上角那个IP地址上

- 点击面板左侧**网站**→**添加站点**

  ![image-20200812110853838](https://pic.heson10.com/img/image-20200812110853838.png)

- 生成网站完毕

### 搭建WordPress

- 点击刚才生成的网站

- 点击上传

- 把wordpress程序传入根目录，完成后如下图：

  ![image-20200812112403897](https://pic.heson10.com/img/image-20200812112403897.png)

  可以先把wp博客文件压缩之后，上传压缩包，然后在面板解压

  **注意：**完成后一定和我上图的文件目录要一致，很多新手会出现根目录一个wordpress的文件夹，里面才是我这个文件，如果这样的话，访问地址就会变成：**http://绑定域名/wordpress**

### WordPress在线安装  

- 浏览器输入： http://绑定的域名/  就出现WordPress在线安装程序，选择简体中文→继续→现在就开始！

- 输入数据库配置信息

  - 面板上的信息：

  ![image-20200812113235771](https://pic.heson10.com/img/image-20200812113235771.png)

  - 我输入的信息：

    ![image-20200812113344494](https://pic.heson10.com/img/image-20200812113344494.png)

- 完成后设置：站点标题、用户名、密码等信息→安装

{%note success, 又一个wordpress站点诞生了！%}
{%note info, 腾讯云下的绑定的域名需要备案才能访问！%}


{% p red large, 此教程适合零基础的新手，不一定是腾讯云，阿里云、百度云，只要是云服务器都适用，码字不易，喜欢的请留言支持一下。 %}

  

  
