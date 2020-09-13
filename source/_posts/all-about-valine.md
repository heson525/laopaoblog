---
title: 所有关于Valine评论系统的配置都在这里【合集】
tags:
	- valine
	- 评论
	- 合集
	- 配置
seo_title: hexo博客valine评论系统配置合集（valine-admin、微信提醒、博主标签）
abbrlink: 28396
date: 2020-08-16 10:27:26
categories: hexo
description:
thumbnail: https://picup.heson10.com/img/valine%E9%85%8D%E7%BD%AE%E5%90%88%E9%9B%86.png
pin: 置顶
---
{%note ,用Hexo博客的小伙伴们对于Valine并不陌生，这款快速、简洁且高效的无后端评论系统，既能快速加载又能提供文章阅读统计，加上一些魔改，可以增加微信与QQ提醒、后台管理、垃圾评论过滤，可以说非常好用。本文主要是介绍配置Valine和可能会遇到的问题【合集】，很多都是搬运过来的教程，文后会附上参考资料。在此感谢这些大佬的参考教程。%}<!--more-->





## 目录

以下标题点击可直接跳转：

- [Hexo设置Valine评论系统](/posts/28396.html#Hexo%E8%AE%BE%E7%BD%AEValine%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F)
- [Valine增强版配置：博主标签、评论后台、微信qq提醒、垃圾评论过滤](/posts/28396.html#Valine%E5%A2%9E%E5%BC%BA%E7%89%88%E9%85%8D%E7%BD%AE%EF%BC%9A%E5%8D%9A%E4%B8%BB%E6%A0%87%E7%AD%BE%E3%80%81%E8%AF%84%E8%AE%BA%E5%90%8E%E5%8F%B0%E3%80%81%E5%BE%AE%E4%BF%A1qq%E6%8F%90%E9%86%92%E3%80%81%E5%9E%83%E5%9C%BE%E8%AF%84%E8%AE%BA%E8%BF%87%E6%BB%A4)
- [解决LeanCloud流控问题](/posts/28396.html#%E8%A7%A3%E5%86%B3LeanCloud%E6%B5%81%E6%8E%A7%E9%97%AE%E9%A2%98)

{%p center red  ,如有其他疑问，或者还需要添加的教程，请在评论区留言。%}

{% btn center large,评论区直达, #comments %}





## Hexo设置Valine评论系统

### 申请LeanCloud账号

{%note , Valine 是基于LeanCloud开发的，所以要去LeanCloud申请一个Serverless服务。%}

1.官网地址：https://leancloud.cn/   （国内版）     https://leancloud.app/   （国际版）

{%note warning, 国内和国际版功能上没有区别，只不过国版版本绑定后台域名时，需要绑定备案域名%}

2.注册后登陆，创建一个应用，名称随意填写，开发版即可。

3.进入刚才创建的应用→点击设置→应用Keys→记录**AppID**、**AppKey**

![image-20200816112412581](https://picup.heson10.com/img/image-20200816112412581.png)





### Volantis主题开启valine评论

1.打开主题配置文件，开启Valine评论

![image-20200816115120959](https://picup.heson10.com/img/image-20200816115120959.png)

2.开启文章阅读数量统计

要在主题配置文件以下地方加上`counter`和`valinecount`，才能开启

![image-20200816114141334](https://picup.heson10.com/img/image-20200816114141334.png)

3.配置好了之后记得要设置**安全域名**：[传送门](https://valine.js.org/quickstart.html#%E5%AE%89%E5%85%A8%E5%9F%9F%E5%90%8D)

{%note , Valine官网已经给出了集成了valine评论功能的主题，开启方法跟上面大同小异：1.找到主题评论模块设置；2.按照相关参数进行设置。欢迎各位小伙伴选用支持valine的主题→[传送门](https://valine.js.org/hexo.html)%}



## Valine增强版配置：博主标签、评论后台、微信qq提醒、垃圾评论过滤

{%note , Valine增强版主要功能是给Valine评论增加一个后台管理功能，经过DesertsP、zhaojun1998、HCLonely、Dreamy.TZK等多位大佬开发、修改，现在功能逐渐完善并实现邮件回复提醒、微信QQ消息推送、邮件回复模板多样化、垃圾评论过滤等功能，主要基于小康修改的valine-admin ，为了符合自己的口味，专门%}

### 博主、小伙伴、访客标签

效果如图所示：

博主![image-20200816122716653](https://picup.heson10.com/img/image-20200816122716653.png)

小伙伴![image-20200816122744048](https://picup.heson10.com/img/image-20200816122744048.png)

访客![image-20200816122809206](https://picup.heson10.com/img/image-20200816122809206.png)

下面以Volantis设置为例：

-  添加js链接、并在配置文件增加参数

使用的是懒人大佬修改的js：

```html
https://cdn.jsdelivr.net/gh/HCLonely/Valine@latest/dist/Valine.min.js
```

{% folding cyan open, 与原生的相比，多了以下功能： %}

- 添加博主，小伙伴，访客标签

- 添加浏览器和操作系统图标，需 `fontawesomeV5` 支持

- 邮箱检测更严格

- 增加 QQ 邮箱识别（原版只能通过昵称栏输入 QQ 号识别）

- meta placeholder 可自定义

{% endfolding %}

{% folding cyan open, 使用方法与原生的类似，不同的是可以多设置几个参数： %}

|      参数       |     类型     |                说明                |           默认           |                     示例                     |
| :-------------: | :----------: | :--------------------------------: | :----------------------: | :------------------------------------------: |
|     tagMeta     |    Array     |          标签要显示的文字          | [“博主”,“小伙伴”,“访客”] |           [“博主”,“小伙伴”,“访客”]           |
|     master      | Array/String |        md5 加密后的博主邮箱        |            []            |     [“fc2c9b067f65c9e2d7057ba797f7cfca”]     |
|     friends     |    Array     |       md5 加密后的小伙伴邮箱       |            []            |     [“4a713ec085a4431f15a8da0942656713”]     |
| metaPlaceholder |    Object    |       meta placeholder 内容        |            {}            | {“nick”:“昵称 / QQ 号”,“mail”:“邮箱 (必填)”} |
|     verify      |   Boolean    | 评论时是否需要验证，需 jQuery 支持 |          false           |                     true                     |

{% endfolding %}

- volantis在主题配置文件中可直接更换，如图：

![image-20200816122250476](https://picup.heson10.com/img/image-20200816122250476.png)

MD5加密网站：https://md5jiami.51240.com/

-  修改主题文件

  找到主题文件`volantis\layout\_third-party\comments\valine\script.ejs`，按图添加增加的配置

  ![image-20200816123439166](https://picup.heson10.com/img/image-20200816123439166.png)

代码：

```ejs
      master: '[<%= theme.comments.valine.master %>]',
      friends: '[<%= theme.comments.valine.friends %>]'
```

至此，就可以在主题配置文件中，直接填写master和friends参数，通过MD5加密的邮箱地址判断博主和小伙伴了。其他参数、其他主题原理相同：


{% folding cyan open, 原理 %}

{% radio green checked, 在配置文件增加参数。 %}
{% radio red checked, 主题模板里增加参数调用。%}

{% endfolding %}

### 部署Valine-Admin评论后台

#### 创建应用

进入leancloud，登陆之前创建的Valine应用

![image-20200816143208797](https://picup.heson10.com/img/image-20200816143208797.png)

#### 进行部署

安利下我用的自己valine-admin-server （基于小康大佬），去掉了一些二次元的东西（本博主年龄偏大，对此不感冒😂）。

地址如下：

```html
 https://github.com/heson525/Valine-Admin-Server
```



![image-20200816143419197](https://picup.heson10.com/img/image-20200816143419197.png)

![- ](https://picup.heson10.com/img/image-20200816144049811.png)



![image-20200816144630444](https://picup.heson10.com/img/image-20200816144630444.png)

#### 绑定评论后台域名

{%note warning ,国内leancloud绑定域名必须使用备案过的域名%}

![image-20200816192418216](https://picup.heson10.com/img/image-20200816192418216.png)



#### 添加参数

| 变量名       | 说明                                                         | 示例                    |
| :----------: | :-----------------------------------: | :---------------------------------: |
| SITE_NAME    | [必填] 网站名称                                              | 黑石博客                |
| SITE_URL     | [必填] 网站地址，最后不要加 /                                | https://www.heson10.com |
| SMTP_USER    | [必填] SMTP 服务用户名，一般为邮箱地址。                     | mail@heson10.com        |
| SMTP_PASS    | [必填] SMTP 密码，一般为授权码，而不是邮箱的登陆密码，请自行查询对应邮件服务商的获取方式 | XXXXXXXXXX              |
| SMTP_SERVICE | [新版支持] 邮件服务提供商，[内置支持](https://nodemailer.com/smtp/well-known/) | 163                     |
| SENDER_NAME  | [必填] 寄件人名称。                                          | 黑石博客                |
| TO_EMAIL | [可选] 博主通知收件地址，默认使用 SMTP_USER | mail@heson10.com |
| BLOGGER_EMAIL | [可选] 如果设置则作为后台管理员邮箱（/sign-up 页面设置），不设置则默认以 SMTP_USER | mail@heson10.com |
| TEMPLATE_NAME | [必填] 设置提醒邮件的主题 | custom2 |
| AKISMET_KEY | [可选] Akismet Key 用于垃圾评论检测，设为 MANUAL_REVIEW 开启人工审核，留空不使用反垃圾 | xxxx |
| ADMIN_URL | [可选] 后台管理地址 (非博客地址) | https://xxxx.leanapp.cn/ |
| COMMENT | [可选] 评论 div 的 ID 名 | #comments |
| SCKEY | [可选] server 酱的 SCKEY | xxx |
| AKISMET_KEY | [可选] Akismet Key 用于垃圾评论检测 | xxxxxxxxxxxx |
| QMSG_KEY | [可选] Qmsg 酱的密钥 | xxxxx |
| QQ | [可选] Qmsg 酱发送的 qq，不填为全部。支持多个，用英文逗号分隔即可 | 535668586 |
| DISABLE_EMAIL | [可选]，填写则代表停止发送邮件 | TRUE |
| QQ_SHAKE | [可选]，填写代表发送 QQ 戳一戳 | TRUE |
| ICP | [可选] 备案信息，直接填写即可。 | 赣ICP备20008960号 |
| INFO | [可选] 自定义信息输出，支持 HTML 代码 | <p style='color:red'>test<p> |
| favicon | [可选] 网页 favicon 图标 | https://cdn.jsdelivr.net/gh/heson525/pic@master/pic/favicon.ico |
| SPAM_WORDS | [可选] 需要对屏蔽的关键词，关键词用半角逗号分隔 | 单号，物流 |
| MAIN_COLOR | [可选] 仅针对 custom2 模板主题的主要颜色 | #ff9191 |
|   MAIN_IMG    |             [可选] 仅针对 custom2 模板主题的头图             |               https://bing.rthe.net/wallpaper                |

当使用自定义邮件服务器时（需将 `SMTP_SERVICE` 变量删掉哦！）

|   变量名    |                             说明                             |       示例        |
| :---------: | :----------------------------------------------------------: | :---------------: |
|  SMTP_HOST  |  邮件服务提供商 SMTP 地址，此项需要自行查询或询问其服务商。  | `smtp.ym.163.com` |
|  SMTP_PORT  | 邮件服务提供商 SMTP 端口，*此项需要自行查询或询问其服务商*。 |        994        |
| SMTP_SECURE | 是否启用加密，默认为 `true`，一般不需要设置，如有特殊请自行配置。 *此项需要自行查询或询问其服务商*。 |       true        |

此项目的主题字段

| 模板名称 |                        说明                        |
| :------: | :------------------------------------------------: |
| default  |                      默认主题                      |
| rainbow  |                   原版的 rainbow                   |
| custom1  | 基于[🎉梨花町の肾兄さん🎉](https://pbas.club/)的模板 |
| custom2  |                对 custom1 的改进版                 |

设置位置：

![image-20200816192116792](https://cdn.jsdelivr.net/gh/heson525/pic@master/pic/image-20200816192116792.png)

#### 后台管理员注册

打开绑定的域名 +`/sign-up`，例如我的域名为 `https://leancloud.heson10.com/`，那么我访问的地址就是 `https://leancloud.heson10.com/sign-up`。接下来设置你的登录信息。

![image-20200816194246888](https://picup.heson10.com/img/image-20200816194246888.png)

#### 后台评论管理

登录地址：https://leancloud.heson10.com

![image-20200816194400223](https://picup.heson10.com/img/image-20200816194400223.png)

 至此，Valine-admin已设置完毕。

### 微信、QQ提醒

#### 微信Server酱 SCKEY 获取

官网注册：http://sc.ftqq.com/3.version

- 用github账户登录
- 获取SCKEY并填入变量
- 在Server酱上绑定微信即可

#### QQmsg 密钥获取（官网要停业了，暂停注册）

官网注册：https://qmsg.zendee.cn/

最近貌似官网要停业了，已经不开放注册了

建议设置微信提醒。

![image-20200816193845192](https://picup.heson10.com/img/image-20200816193845192.png)

### 垃圾评论过滤

{%note info,Akismet (Automattic Kismet) 是应用广泛的一个垃圾留言过滤系统，其作者是大名鼎鼎的 WordPress 创始人 Matt Mullenweg，Akismet 也是 WordPress 默认安装的插件，其使用非常广泛，设计目标便是帮助博客网站来过滤留言 Spam。有了 Akismet 之后，基本上不用担心垃圾留言的烦恼了。
启用 Akismet 后，当博客再收到留言会自动将其提交到 Akismet 并与 Akismet 上的黑名单进行比对，如果名列该黑名单中，则该条留言会被标记为垃圾评论且不会发布。%}

只需在`AKISMET_KEY`变量上填入`Akismet Key`

申请地址：https://akismet.com/development/



## 解决LeanCloud流控问题

之前几天后台不能发送邮件通知，查看日志显示"因流控原因，通过定时任务唤醒体验版实例失败，建议升级至标准版云引擎实例避免休眠"，相信大家会碰到这样的问题。

因为好多都是同一时间用定时任务触发容器运行，leancloud服务器不堪重负。

多得理论性知识可直接查看小康大佬的[这篇帖子](https://www.antmoe.com/posts/ff6aef7b/index.html)。下面只讲方法：

### 解决方法之GitHub+Actions大法

#### 新建一个Token

方法之前教程有写很详细，[点这里](https://www.heson10.com/posts/57815.html#GitHub)。不过这里用到的权限很少。勾上：

- repo    
- admin:repo_hook
- worflow

{%note warning, **TOKEN名字请务必使用**`GITHUB_TOKEN`%}

#### Fork项目地址

地址： https://github.com/blogimg/WakeLeanCloud

进入后点击右上角的 fork，这样会fork到自己的账户下。

![image-20200816183305383](https://picup.heson10.com/img/image-20200816183305383.png)

#### 配置唤醒项目

在自己fork的仓库下，进入Secrets ，设置SITE变量

![image-20200816183547131](https://picup.heson10.com/img/image-20200816183547131.png)

填评论后台的地址，这个leancloud国内版本是自己域名绑定的后台地址。我的是https://leancloud.heson10.com

![image-20200816183822992](https://picup.heson10.com/img/image-20200816183822992.png)

#### 启动

接下来对自己的项目点个 star 就能启动了，启动后请切换到 actions，看看是否运行成功。

![image-20200816183913657](https://picup.heson10.com/img/image-20200816183913657.png)

在actions选项，可以看是否唤醒成功。

![image-20200816183958108](https://picup.heson10.com/img/image-20200816183958108.png)

如果你的 GitHub 从来没有用过 actions，那么需要先 “了解”。方法很简单，点击绿色的按钮即可。

![image-20200816184035113](https://picup.heson10.com/img/image-20200816184035113.png)

然后再取消star，再点击一次就可以看到了。










{% folding cyan open, 参考文档%}

{% radio green checked, 1.Valine官方文档：https://valine.js.org/ %}
{% radio red checked, 2.懒人大佬：https://blog.hclonely.com/posts/409d3090/  %}

{% radio yellow checked, 3.小康博客：https://www.antmoe.com/posts/2380732b/index.html %}



{% endfolding %}

