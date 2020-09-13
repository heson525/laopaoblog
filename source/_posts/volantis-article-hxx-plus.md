---
title: 优化Volantis主题中文章页面h1—h6标签（排版更清爽）
abbrlink: 35039
date: 2020-08-16 22:43:41
tags:
	- volantis
	- 主题
	- 优化
categories: hexo
description:
thumbnail: https://cdn.jsdelivr.net/gh/volantis-x/cdn-org/blog/Logo-Cover@3x.png
---
{%note ,Volantis是一个非常优秀的主题，各种模块化的小功能让人眼前一亮。但.........这个文章内容页h1、h2、h3等标签感觉都是一个样，加上昏暗的#444颜色，着实让人感觉很着急。特别是今天写这个Valine教程合集的时候，因为标题太多了，眼睛都快瞎了。赶紧优化一下！%}<!--more-->

## 修改h1-h6颜色

在`hexo\themes\volantis\source\css\_layout`文件夹下找到`article.styl`文件

在开头处增加h1-h6颜色参数：

```stylus
//自定义参数设置
$color-h2 = #ad2121
$color-h3 = #0028bb
$color-h4 = #ad9521
```

以上是我加的，一般文章里不用h1标题，我就没有加进去，h5h6用的很少，我也就没加了。



## 加粗h1-h6

同样是`article.styl`文件，找到h1-h6标签样式处：

```stylus
  h1
    text-align: $textalign-h1
    color: $color-h1
    margin-top: $gap-h2
  h2
   ...
```

给每个加上`font-weight: bold`，如下图：

```stylus
  h1
    font-weight: bold
    text-align: $textalign-h1
    color: $color-h1
    margin-top: $gap-h2
  h2
    font-weight: bold
    text-align: $textalign-h2
    color: $color-h2
    margin-top: $gap-h2
  h3
    font-weight: bold
    text-align: $textalign-h3
    color: $color-h3
    margin-top: $gap-h3
  h4
    font-weight: bold
    text-align: $textalign-h4
    color: $color-h4
    margin-top: $gap-h4
  h5
    font-weight: bold
    color: $color-h5
    margin-top: $gap-paragraph
  h6
    font-weight: bold
    color: $color-h6
    margin-top: $gap-paragraph
```

或者直接在开头加

```stylus
h1,h2,h3,h4,h5,h6
    font-weight: bold
```

## 效果对比图

![volantis修改h1](https://picup.heson10.com/img/volantis修改h1.jpg)



长文效果图预览：[所有关于Valine的配置都在这里【合集】](https://www.heson10.com/posts/28396.html)

{%note warning ,自用修改，不喜勿喷。%}

