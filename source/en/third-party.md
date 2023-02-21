---
title: Third Party Services
type: docs
permalink: en/third-party/
date: 2020-04-24 10:30:16
---



Due to the nature of the Hexo static site, it cannot natively support features such as article commenting and data statistics that are easy to implement on dynamic websites deployed on servers. A common solution is to use third-party services. "Cards" natively supports 9 types of comment systems and 5 types of site data statistics services, aiming to help each user solve this pain point as much as possible. If you think there are other excellent and desirable services that we have not built-in, you are welcome to open an issue or submit a PR.

## Comments Services

The comment system is set in the theme configuration file `comments` and the comment system is selected through the `use`.

```yaml
comments: 
  use: 
```

- `use`: Enter the name of the comment system that needs to be enabled, such as `disqusjs`.

> Unless you have special considerations, we do NOT recommend enabling more than one comment service at the same time.

### Disqus

[https://disqus.com/](https://disqus.com/)

"Cards" provides two ways to use Disqus, regular enablement and DisqusJS.

```yaml
comments: 
  use: disqus

  disqus: 
    shortname: 
```

如果你决定使用常规模式，只需填写 `shortname` 即可。如果你还不清楚你的 `shortname` ，可以登陆评论管理后台查看。
If you decide to use the regular mode, simply fill in `shortname`. If you are not sure what your `shortname` is, you can log in to [Disqus management backend](https://admin.disqus.com) to check.

![](/assets/img/disqus-shortname.png)

### DisqusJS

Since Disqus is difficult to access in some regions, you can choose to use DisqusJS to better load Disqus comments.

```yaml
comments: 
  use: disqusjs
    
  disqusjs: 
    shortname: 
    siteName: 
    api: 
    apikey: 
    admin: ''
    adminLabel: 
    nesting: 2
```

You can go to [DisqusJS - README](https://github.com/SukkaW/DisqusJS/blob/master/README.md) to learn about the relevant parameter details.

### Valine

[https://valine.js.org](https://valine.js.org/)

Valine, a commenting system based on LeanCloud.

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

You can read the [Quick Start](https://valine.js.org/quickstart.html) and [Configuration](https://valine.js.org/configuration.html) in the Valine document to learn about the relevant parameter details. In general, you only need a LeanCloud account.

### MiniValine

[https://github.com/MiniValine/MiniValine](https://github.com/MiniValine/MiniValine) 

MiniValine, a lightweight commenting system based on LeanCloud.

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

You can refer to the "[Options](https://github.com/MiniValine/MiniValine#options)" section of the MiniValine documentation to learn about relevant parameter details. In general, you only need a LeanCloud account to use MiniValine.

### Artalk

[https://github.com/qwqcode/Artalk](https://github.com/qwqcode/Artalk) 

Artalk is a concise and interesting self-hosted commenting system.

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

You can refer to the [Artalk document](https://artalk.js.org/en/) to learn about related configuration options.

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

You can refer to the "[Options](https://github.com/gitalk/gitalk#options)" section of the Gitalk document to learn about related parameter details. This plugin requires GitHub Application. If you have not created one yet, please [apply here](https://github.com/settings/applications/new).

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

You can refer to the [Gitment document](https://github.com/imsun/gitment#3-render-gitment) to learn about related parameter details. This plugin requires GitHub Application. If you have not created one yet, please [apply here](https://github.com/settings/applications/new).

### LiveRe

[https://livere.com/](https://livere.com/)

```yaml
comments: 
  use: levere
  
  livere: 
    livere_uid:
```

"Cards" has the free version of LiveRe, `ciry_version`, built in. You can obtain the UID from the LiveRe management background.

### Changyan

[http://changyan.kuaizhan.com/](http://changyan.kuaizhan.com/)

```yaml
comments: 
  use: changyan
  
  changyan: 
    appid:
    conf:
    thread_key_type: path 
```

You can find your `appid` and `conf` in the installation method in the Changyan background. `thread_key_type` is the page differentiation parameter, which defaults to using the page path for differentiation. If you often change links, you can also customize a parameter in the `front-matter` of each article to differentiate, for example:

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

You can refer to the [official documentation](https://wildfire.js.org) to learn about related parameter details.

### Twikoo

[https://twikoo.js.org/](https://twikoo.js.org/) 

Twikoo, a comment system based on [Tencent CloudBase](https://cloudbase.net/).

```yaml
comments:
  use: twikoo
  
  twikoo:
    envId:  # Your CloudBase ID
```

You can refer to the [Quick Start](https://twikoo.js.org/en/quick-start.html) to learn about related parameter details. In general, you only need a CloudBase free account. 

## Web Statistics Service

### Google Analytics

[https://analytics.google.com/](https://analytics.google.com/)

```yaml
analytics: 
  google_site_id: 
  gtags_site_id: 
```

After logging into Google Analytics, step to "Settings - Tracking Info - Tracking Code" to obtain your Tracking ID. Google provides two tracking methods: `google_site_id` for traditional tracking, or `gtags_site_id` for the new tracking method. The latter may require a larger file request, which could have some impact on page performance.

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

CNZZ has been acquired by Umeng. After logging into the Umeng backend, go to the code installation page to obtain your tracking code.

```html
<script src="//s95.cnzz.com/z_stat.php?id=[ Traching ID ]&web_id=[ Traching ID ]" language="JavaScript"></script>
```

Then set the obtained Tracking ID to `cnzz_site_id`.

```yaml
analytics: 
  
  cnzz_site_id: 
```

### Cloudflare Web Analytics

[https://support.cloudflare.com/hc/en-us/articles/360052685432-Cloudflare-Web-Analytics](https://support.cloudflare.com/hc/en-us/articles/360052685432-Cloudflare-Web-Analytics) 

Cloudflare Web Analytics is a *free, privacy-first* statistics service offered by Cloudflare (no need to replace Cloudflare DNS resolution or access Cloudflare CDN).

```yaml
analytics: 
  
  cloudflare_site_id: 
```

Find your `cloudflare_site_id` in the JS snippet provided to you, which should include a `token`.

![](/assets/img/cloudflare-web-analytics-setup.png)