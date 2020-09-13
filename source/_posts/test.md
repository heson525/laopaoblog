---
title: Hexo在coding上持续集成
date: 2020-08-09 23:58:28
tags:
	- hexo
	- 持续集成
	- coding
	- 部署
abbrlink: 27150
categories: hexo
---
{%note success, 能看到这篇文章的时候，代表已经实现hexo在coding上的持续集成%}<!--more-->

## 开始之前

- 确保已经实现github和coding双部署
- 确保已经获取github令牌，[传送门](https://heson.xyz/posts/57815.html#GitHub)
- 确保已经获取coding令牌，[传送门](https://heson.xyz/posts/57815.html#Coding-token)
- 并在根目录如图配置过，[传送门](https://heson.xyz/posts/57815.html#%E4%BF%AE%E6%94%B9%E6%A0%B9%E7%9B%AE%E5%BD%95-config-yml%E6%96%87%E4%BB%B6)

![](https://pic.heson.xyz/img/image-20200727130801522.png)

## coding新建博客源码仓库并上传博客源码

- 新建名字为hexoblog的私有空白仓库（不要readme.md初始化），用来存放博客源码

![](https://cdn.jsdelivr.net/gh/heson525/pic@master/pic/image-20200810104503190.png)

这个是我建立的hexoblog仓库，记住这个地址。

- 找到博客源码目录：

  ![image-20200810104755029](https://pic.heson.xyz/wallpapers/image-20200810104755029.png)

- 删除`.git`文件**(这个是隐藏文件)**后，进入git bash（一般情况主题文件里有一个.git文件也要删除，以免报错）

- 用`git init`初始化仓库

- 因为你不是第一次用git上传，所以**不用**设置用户名、邮箱，否则：

  ```shell
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"
  ```

- 关联远程仓库

  ```shell
  git remote add origin https://令牌用户名:令牌密码@项目地址
  ```

  这个地方注意一下，因为是私有仓库，这里要填**带令牌**的https地址，coding令牌获取[传送门](https://heson.xyz/posts/57815.html#Coding-token)，如图（**绿色文字**）：

  ![image-20200810105415871](https://pic.heson.xyz/img/image-20200810105415871.png)

- **分行**输入一下代码：

  ```shell
  git add .     //添加目录下所有发生改变的文件
  git commit -m '上传博客源码（随意填写）'           //注释信息一定要写，方便标记
  git push -u origin master      //本地仓库代码提交至远程仓库
  ```

- 上传后如图所示：

  ![image-20200810110715075](https://pic.heson.xyz/img/image-20200810110715075.png)

  

## 构建持续集成

- 新建一个持续集成

  ![image-20200810111129460](https://pic.heson.xyz/img/image-20200810111129460.png)

  点最下面的自定义：

  ![image-20200810111154516](https://pic.heson.xyz/img/image-20200810111154516.png)

- 开始新建

  ![image-20200810111319057](https://pic.heson.xyz/img/image-20200810111319057.png)

- 填写构建代码

  ![image-20200810111631188](https://pic.heson.xyz/img/image-20200810111631188.png)

代码如下：

```shell
pipeline {
  agent any
  stages {
    stage('克隆项目') {
      steps {
        sh 'git clone https://你的令牌用户名:令牌密码@e.coding.net/hesonxyz/hexoblog/hexoblog.git（这换成博客源码地址） .'
        sh 'ls -a'
      }
    }
    stage('安装依赖') {
      steps {
        sh 'ls -a'
        sh 'npm install -g hexo-cli'
        sh 'npm install hexo --save'
        sh 'npm install'
      }
    }
    stage('构建发布') {
      steps {
        sh 'hexo clean && hexo g && hexo d'
      }
    }
  }
}
```



- 触发规则一般是推送到`master`时触发构建，如图：

  ![image-20200810111911987](https://pic.heson.xyz/img/image-20200810111911987.png)

## 后期使用问题

- 更新博文：

1._post文件夹直接新建md文件；

2.软件（ git小乌龟）推送至仓库，触发自动构建。

**（稍后详细介绍）**

- 固定链接问题

因为使用过hexo-abbrlink插件，部署之后如果要修改md文件，记得要在抬头加上abbrlink的值

![image-20200810112504260](https://pic.heson.xyz/img/image-20200810112504260.png)

