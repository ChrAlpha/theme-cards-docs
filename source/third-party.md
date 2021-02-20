---
title: 第三方服务
type: docs
permalink: third-party/
date: 2020-04-24 10:30:16
---





由于 Hexo 静态站点特殊性，无法原生支持文章评论与数据统计等，这些部署在服务器的动态网站很容易实现的功能，这时一个普遍的解决方案便是借助第三方服务。「Cards」原生支持 9 种评论系统，以及 5 种站点数据统计服务，尽可能帮助每一个用户解决此痛点。如果你认为还有其他优秀、可取的服务我们没有内置，也欢迎新建 issue 或提交 PR。

## 评论服务

评论系统在主题配置文件 `comments` 处设置，通过 `use` 字段选择评论系统。

```yaml
comments: 
  use: 
```

- `use`：将需要开启的评论系统的名称填入，例如 `disqusjs`。

>   除非你有特别考量，不然我们 **不建议** 同时开启超过 1 个评论服务。

### Disqus

[https://disqus.com/](https://disqus.com/)

「Cards」提供两种使用 Disqus 的方式，分别是常规开启与 DisqusJS。

```yaml
comments: 
  use: disqus

  disqus: 
    shortname: 
```

如果你决定使用常规模式，只需填写 `shortname` 即可。如果你还不清楚你的 `shortname` ，可以登陆评论管理后台查看。

![](/assets/img/disqus-shortname.png)

### DisqusJS

由于 Disqus 在某些地区访问困难，可以选择使用 DisqusJS 更好地加载 Disqus 评论。

```yaml
comments: 
  use: disqusjs
    
  disqusjs: 
    shortname: 
    siteName: 
    api: 
    apikey: 
    admin: ''
    nesting: 2
```

你可以前往 [DisqusJS - README](https://github.com/SukkaW/DisqusJS/blob/master/README.md) 了解相关参数细节。

### Valine

[https://valine.js.org](https://valine.js.org/)

Valine，一款基于 LeanCloud 的评论系统。

```yaml
comments: 
  use: valine 
  
  valine: 
    appId: 
    appKey:
    placeholder: 
    path: 
    avatar: 
    meta: [nick, mail, link]
    pageSize: 
    lang: 
    visitor: 
    highlight: 
    avatarForce: 
    recordIP: 
    serverURLs: 
    enableQQ: 
    requiredFields: [nick, mail]
    emojiCDN: 
    emojiMaps: 
```

你可以阅读 Valine 文档中的 [快速开始](https://valine.js.org/quickstart.html) 与 [配置项](https://valine.js.org/configuration.html) 了解相关参数细节。一般情况下，你只需要一个 LeanCloud 账号即可。

### MiniValine

[https://github.com/MiniValine/MiniValine](https://github.com/MiniValine/MiniValine) 

MiniValine，一款基于 LeanCloud 的轻量级评论系统。

```yaml
comments: 
  use: minivaline
  
  minivaline:  
    appId: 
    appKey: 
    mode: 
    placeholder: 
    pathname: 
    adminEmailMd5: 
    master: 
    friends: 
    tagMeta: 
    math: 
    md: 
    lang: 
    emoticonUrl:
    NoRecordIP: 
    maxNest: 
    pageSize: 
    enableQQ: 
    visitor: 
    serverURLs: 
```

你可以阅读 MiniValine 文档中的 [Opinions](https://github.com/MiniValine/MiniValine#options) 了解相关配置项。一般情况下，你只需要一个 LeanCloud 账号即可。

### Artalk

[https://github.com/qwqcode/Artalk](https://github.com/qwqcode/Artalk) 

Artalk，一款简洁有趣的自托管评论系统。

```yaml
comments: 
  use: artalk
  
  artalk: 
    serverUrl: 
    placeholder: 
    noComment: 
    defaultAvatar: 
    pageKey: 
    gravatar: 
      cdn: 
    readMore: 
      pageSize: 
      autoLoad: 
    emoticons: 
```

你可以阅读 [Artalk 文档](https://github.com/qwqcode/Artalk) 了解相关配置项。

### Gitalk

[https://github.com/gitalk/gitalk](https://github.com/gitalk/gitalk)

```yaml
comments: 
  use: gitalk
  
  gitalk:
    repo:
    owner:
    clientID:
    clientSecret:
```

你可以阅读 Gitalk 文档中的 [Options](https://github.com/gitalk/gitalk/blob/master/readme-cn.md#%E8%AE%BE%E7%BD%AE) 了解相关参数细节。该插件需要使用 **GitHub Application**，如果还未创建请 [点击这里](https://github.com/settings/applications/new) 申请。

### Gitment

[https://github.com/imsun/gitment](https://github.com/imsun/gitment)

```yaml
comments: 
  use: gitment
  
  gitment:
    repo:
    owner:
    client_id:
    client_secret:
```

你可以阅读 [Gitment 文档](https://github.com/imsun/gitment#3-render-gitment) 了解相关参数细节。该插件需要使用 **GitHub Application**，如果还未创建请 [点击这里](https://github.com/settings/applications/new) 申请。

### 来必力

[https://livere.com/](https://livere.com/)

```yaml
comments: 
  use: levere
  
  livere: 
    livere_uid:
```

「Cards」内置了 `ciry_version` 版本的来必力，该版本是免费的。你可以在 Livere 管理后台获取 UID。

### 畅言

[http://changyan.kuaizhan.com/](http://changyan.kuaizhan.com/)

```yaml
comments: 
  use: changyan
  
  changyan: 
    appid:
    conf:
    thread_key_type: path 
```

你可以在畅言后台安装方式找到你的 `appid` 与 `conf`。而 `thread_key_type` 为页面区分参数，默认使用页面路径区分。如果你经常更改链接，也可以在每篇文章的 `front-matter` 中自定义一个参数来区分，例如：

 ```yaml
// front-matter of each post
---
cy: [ unique id ]
---
 ```

```yaml
// theme config
changyan:
  enable: true
  appid:
  conf:
  thread_key_type: cy
```

### Wildfire

[https://wildfire.js.org/](https://wildfire.js.org/)

```yaml
comments: 
  use: wildfire
    
  wildfire: 
    database_provider: firebase # firebase | wilddog
    wilddog_site_id:
    firebase_api_key:
    firebase_auth_domain:
    firebase_database_url:
    firebase_project_id:
    firebase_storage_bucket:
    firebase_messaging_sender_id:
    theme: light # light | dark
    locale: en
```

你可以阅读 [官方文档](https://wildfire.js.org/#/zh-cn/) 了解参数细节及如何使用。

### Twikoo

[https://twikoo.js.org/](https://twikoo.js.org/) 

Twikoo，一款基于 [腾讯云 CloudBase](https://cloudbase.net/) 的评论系统。

```yaml
comments:
  use: twikoo
  
  twikoo:
    envId:  # 你的 CloudBase 环境 ID
```

你可以阅读 Twikoo 文档 [快速上手](https://twikoo.js.org/quick-start.html#%E4%BA%91%E5%87%BD%E6%95%B0%E9%83%A8%E7%BD%B2) 部分了解如何配置 Cloudbase 云函数 。一般情况下，你只需要一个 CloudBase 免费应用即可。

## 数据统计服务

### Google Analytics

[https://analytics.google.com/](https://analytics.google.com/)

```yaml
analytics: 
  google_site_id: 
  gtags_site_id: 
```

登陆 Google Analytics 后，前往「设置 - 跟踪信息 - 跟踪代码」处获取 **跟踪 ID**。Google 提供两种跟踪方式，分别 `google_site_id` 传统跟踪，或 `gtags_site_id` 新统计方式。后者需要请求更大的文件，可能会对页面加载有一定影响。

### 百度统计

[http://tongji.baidu.com](http://tongji.baidu.com/) 

登陆百度统计后台，在获取跟踪代码处得到你的跟踪 ID。

```html
   | <script>
   |     var _hmt = _hmt || [];
   |     (function() {var hm = document.createElement('script');
 =>|     hm.src = 'https://hm.baidu.com/hm.js?[跟踪 ID]';
   |     var s = document.getElementsByTagName('script')[0];
   |         s.parentNode.insertBefore(hm, s);
   |     })();
   | </script>
```

然后将该 ID 设置到 `baidu_site_id` 中。

```yaml
analytics: 
  ...
  baidu_site_id: 
```

### CNZZ

[https://web.umeng.com](https://web.umeng.com/) 

CNZZ 已被友盟收购，登陆后台找到代码安装页面。

```html
<script src="//s95.cnzz.com/z_stat.php?id=[ 跟踪 ID ]&web_id=[ 跟踪 ID ]" language="JavaScript"></script>
```

将该 ID 设置到 `cnzz_site_id` 中。

```yaml
analytics: 
  
  cnzz_site_id: 
```

### Cloudflare Web Analytics

[https://support.cloudflare.com/hc/en-us/articles/360052685432-Cloudflare-Web-Analytics](https://support.cloudflare.com/hc/en-us/articles/360052685432-Cloudflare-Web-Analytics) 

Cloudflare Web Analytics，Cloudflare 提供的*免费、隐私优先*的统计服务（无需替换 Cloudflare DNS 解析或接入 Cloudflare CDN）。

```yaml
analytics: 
  
  cloudflare_site_id: 
```

在提示你插入的 JS 片段中找到 `token`，那便是你的 `cloudflare_site_id`。

![](/assets/img/cloudflare-web-analytics-setup.png)