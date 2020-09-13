---
title: 'Vercel+Github+Coding三线部署HEXO,提升访问速度'
tags:
  - vercel
  - 加速
  - CDN
categories: hexo
abbrlink: 38770
date: 2020-08-07 17:34:51
---

{%note, 之前已经用github+coding双线部署过博客：[传送门](https://www.heson10.com/posts/54971.html)。因为我一直用的联通，访问coding还是挺快的，知道有些移动宽带的网友反应博客打不开。我才意识到，coding对移动不太友好。这两天刚好看到colsrch那有一篇关于使用vercel的[文章](https://colsrch.top/posts/56951997/index.html)，便在此做下记录！%}

<!--more-->
{%note success, 
1.用github账号注册vercel


%}

{%note success, 

2.克隆github的public仓库


%}
{%note success, 

3.域名解析默认和移动线路到vercel提供的ip地址，联通线路cname到coding，境外就直接github

%}

vercel配置完毕：
![](https://cdn.jsdelivr.net/gh/heson525/pic@master/pic/20200807175232.png)

未配置vercel前双线部署测速：

![Snipaste_2020-08-05_20-33-51](https://cdn.jsdelivr.net/gh/heson525/pic@master/pic/Snipaste_2020-08-05_20-33-51.png)

配置后三线部署测速：

![](https://cdn.jsdelivr.net/gh/heson525/pic@master/pic/Snipaste_2020-08-05_20-34-12223.png)