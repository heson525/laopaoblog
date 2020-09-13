---
title: hexo博客访问速度优化：又拍云CDN
tags:
  - CDN
  - hexo
  - 又拍云
categories: hexo
guanzhu: true
thumbnail: 'https://picup.heson10.com/img/20200813232438.png'
abbrlink: 30982
date: 2020-08-13 23:10:20
description:
---
{%note ,为了追求极致的博客访问速度，还是决定把博客挂上又拍云CDN，之前已经申请了又拍云联盟，每个月送15GB的CDN流量，关键还是HTTPS的。访问速度已经在17CE测试过了，全国绿油油的一片，简直不能太香😂%}<!--more-->

![](https://picup.heson10.com/img/20200813232438.png)

## 注册又拍云

1.注册又拍云：{% btn 点我注册, https://console.upyun.com/register/?invite=BkHDGCzMw, fas fa-download %}

2.加入又拍云联盟：https://www.upyun.com/league   点击申请

3.在网站底部footer处加上又拍云LOGO。{% btn 又拍云LOGO下载, https://www.upyun.com/static/upyun_logos.zip, fas fa-download %}
4.耐心等待审核成功通知。

## 创建CDN服务

- 在又拍云上创建一个CDN服务，设置如下图：

![](https://picup.heson10.com/img/20200813234224.png)

- 记住又拍云提供的CNAME地址，去域名提供商解析到加速域名（我的是www.heson10.com ）

![image-20200813234602731](https://picup.heson10.com/img/image-20200813234602731.png)

## Coding上的设置



先解绑域名，取消强制https，待又拍云CDN挂上HTTPS后在绑定

![image-20200813235703994](https://picup.heson10.com/img/image-20200813235703994.png)

## Github上的设置

同样，github上也要取消强制HTTPS

![image-20200813235808288](https://picup.heson10.com/img/image-20200813235808288.png)

## 又拍云CDN配置

- 配置SSL（HTTPS）

  1.进入HTTPS设置

  ![image-20200814000448667](https://picup.heson10.com/img/image-20200814000448667.png)

  2.申请一个免费SSL证书，推荐免费的Let's Encryppt 的证书

  ![image-20200814000338674](https://picup.heson10.com/img/image-20200814000338674.png)

  3.开启HTTPS

  ![image-20200814000528966](https://picup.heson10.com/img/image-20200814000528966.png)

- 优化配置

  - 开启 Gzip 和 Brotli，压缩级别调到3
  - 开启页面压缩
  - HTTP 302 调度
  - 开启TLS1.3，最低建议TLSv1.1
  - 开启 HTTP/2 + Server Push
  - WebP 自适应
  - 开启源站资源迁移

{%note sucess ,这样设置后更快！上效果图——又拍云CDN加速效果%}
 ![image-20200814235054951](https://picup.heson10.com/img/image-20200814235054951.png)




## 最后

至此，又拍云CDN就弄好了，加速很明显。遇到问题，请在下方回复。码字不易请多多支持！

## 更新问题

8月16日更新：

Q:开启了源站资源迁移功能，修改博客css等样式文件，长时间不刷新。

A:开启源站资源迁移功能后，会把CSS 、js等文件迁移到又拍云云存储。要在对应的云存储中，使用 FTP 或者文件管理，删除或上传最新的CSS 、js样式脚本。