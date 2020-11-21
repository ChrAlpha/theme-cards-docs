---
title: 进阶使用
type: docs
permalink: expert/
date: 2020-06-13 14:30:08
---

## 使用 Git 管理 Hexo

正如 [开始使用](/start/) 中提到的，我们建议使用 git 获取主题文件，以便第一时间跟进新版本。

但是如果你有使用 Git 管理整个站点文件的需求话，需要使用 `git submodule` 避免冲突。

`git submodule` 允许将另一个仓库克隆至你的项目，同时还保持提交的独立。

1.  获取「Cards」为子模块

    ```bash
    git submodule add https://github.com/ChrAlpha/hexo-theme-cards.git themes/cards
    ```

2.  跟进「Cards」为远程最新版本

    ```bash
    git submodule update --remote
    ```

这样一来，之后只需要克隆站点仓库便可获取站点文件及主题文件。

```bash
git clone --recurse-submodules https://github.com/ChrAlpha/[website source].git
```

更多关于 `git submodule` 的详细内容可以参考 [Git 文档](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97)。

## 平滑更新

基于 Hexo 3.0 新增「数据文件」特性，无需直接更改主题 `_config.yml` 便可达到相同效果。以此使得主题配置文件的修改可存储与主题文件夹外，方便直接使用 Git 管理主题版本，而无需每次更新手动更改主题配置文件。

在**站点根目录**下创建 `source/_data/cards.yml`（若 `source/_data` 目录不存在，请新建）。并将你需要修改的内容填写至此（**无需**复制整个主题配置文件），根据约定，这里的内容将覆盖主题配置文件中对应的内容。

>   此特性从「Cards」v5.0 开始支持。

{% note success %}

例子：

比如你需要修改 opengraph 配置，在主题配置文件中是：

```yaml
head: 

  favicon: 
  # ...

  opengraph: 
    enable: true
    type: 
    twitter_card: summary_large_image
    twitter_id: 
    twitter_site: 
    image: page.thumbnail
    fb_admins: 
    fb_app_id: 
```

你只需要在 `source/_data/cards.yml` 中添加：

```yaml
head: 
  opengraph: 
    twitter_id: ichralpha
    twitter_site: ichralpha
```

{% endnote %}

## CDN

使用 CDN 获取所需的静态资源通常能使请求更加快速、稳定。而主题默认采用 [jsDelivr](https://www.jsdelivr.com)（国内备案，网宿接入，100 SLA，在全球范围内都有很不错的速度），当然你也可以自行选择其他 CDN。

此方面配置请在主题配置文件中定位到 `vendors` 并修改相应配置。

### style

主题默认 CSS 文件，如果你有自定义 `style` ，请务必替换为相应的 CDN 地址或者将此项留空。

**jsDelivr**

```yaml
style: https://cdn.jsdelivr.net/npm/hexo-theme-cards@1.2/dist/css/style/main.min.css
```

**UNPKG**

```yaml
style: https://unpkg.com/hexo-theme-cards@1.2/dist/css/style/main.min.css
```

### darkmode

暗色模式样式及切换按钮。

**jsDelivr**

```yaml
darkmode: 
  css: https://cdn.jsdelivr.net/npm/hexo-theme-cards@1.2/dist/css/style/dark.min.css
  js: https://cdn.jsdelivr.net/npm/hexo-theme-cards@1.2/dist/js/darkmode.min.js
```

**UNPKG**

```yaml
darkmode: 
  css: https://unpkg.com/hexo-theme-cards@1.2/dist/css/style/dark.min.css
  js: https://unpkg.com/hexo-theme-cards@1.2/dist/js/darkmode.min.js
```

### highlight

[https://theme-cards.ichr.me/expand/#highlight](/expand/#highlight) 

主题定制 highlight 样式。

**jsDelivr**

```yaml
highlight: https://cdn.jsdelivr.net/npm/hexo-theme-cards@1.2/dist/css/highlight/
```

**UNPKG**

```yaml
highlight: https://unpkg.com/hexo-theme-cards@1.2/dist/css/highlight/
```

### hljs

[https://highlightjs.org/](https://highlightjs.org/) 

原生 highlight.js 样式。

详见：[https://theme-cards.ichr.me/expand/#hljs](/expand/#hljs) 

**jsDelivr**

```yaml
hljs: https://cdn.jsdelivr.net/npm/highlight.js@10.1.2/styles/
```

**UNPKG**

```yaml
hljs: https://unpkg.com/highlight.js@10.1.2/styles/
```

**cdnjs**

```yaml
hljs: https://cdnjs.cloudflare.com/ajax/libs/highlight.js/10.1.2/styles/
```

**css.net**

```yaml
hljs: https://cdnjs.loli.net/ajax/libs/highlight.js/10.1.2/styles/
```

### prismjs

[https://prismjs.com/](https://prismjs.com/) 

PrismJS 样式。

详见：[https://theme-cards.ichr.me/expand/#prismjs](/expand/#prismjs) 

**jsDelivr**

```yaml
prismjs: https://cdn.jsdelivr.net/npm/prismjs@1.21.0/themes/
```

**UNPKG**

```yaml
prismjs: https://unpkg.com/prismjs@1.21.0/themes/
```

**cdnjs**

```yaml
prismjs: https://cdnjs.cloudflare.com/ajax/libs/prism/1.21.0/themes/
```

**css.net**

```yaml
https://cdnjs.loli.net/ajax/libs/prism/1.21.0/themes/
```

### lazyload

Vanilla-Lazyload 17.1.2 [https://github.com/verlok/lazyload](https://github.com/verlok/lazyload)

主题内置图片 Lazyload 功能，默认调用 Vanilla Lazyload。

详见 [https://theme-cards.ichr.me/expand/#Lazyload](/expand/#Lazyload)

**jsDelivr**

```yaml
lazyload: https://cdn.jsdelivr.net/npm/vanilla-lazyload@17.1.2/dist/lazyload.min.js
```

**UNPKG**

```yaml
lazyload: https://unpkg.com/vanilla-lazyload@17.1.2/dist/lazyload.min.js
```

**cdnjs**

```yaml
lazyload: https://cdnjs.cloudflare.com/ajax/libs/vanilla-lazyload/17.1.2/lazyload.min.js
```

**css.net**

```yaml
lazyload: https://cdnjs.loli.net/ajax/libs/vanilla-lazyload/17.1.0/lazyload.min.js
```

### valine

[https://github.com/xcss/Valine](https://github.com/xcss/Valine) [https://valine.js.org/](https://valine.js.org/)

Valine 评论系统。

详见 [https://theme-cards.ichr.me/third-party/#Valine](/third-party/#Valine)

**jsDelivr**

```yaml
valine: https://cdn.jsdelivr.net/npm/valine@1.4.14/dist/Valine.min.js
```

**UNPKG**

```yaml
valine: https://unpkg.com/valine@1.4.14/dist/Valine.min.js
```

**cdnjs**

```yaml
valine: https://cdnjs.cloudflare.com/ajax/libs/valine/1.4.14/Valine.min.js
```

**css.net**

```yaml
valine: https://cdnjs.loli.net/ajax/libs/valine/1.4.14/Valine.min.js
```

### minivaline

[https://github.com/MiniValine/MiniValine](https://github.com/MiniValine/MiniValine) [https://minivaline.github.io/](https://minivaline.github.io/)

MiniValine 评论系统。

详见 [https://theme-cards.ichr.me/third-party/#MiniValine](/third-party/#MiniValine)

**jsDelivr**

```yaml
minivaline: https://cdn.jsdelivr.net/npm/minivaline@2.7.5/dist/MiniValine.min.js
```

**UNPKG**

```yaml
minivaline: https://unpkg.com/minivaline@2.7.5/dist/MiniValine.min.js
```

### artalk

[https://github.com/qwqcode/Artalk](https://github.com/qwqcode/Artalk)

Artalk 评论系统。

详见 [https://theme-cards.ichr.me/third-party/#Artalk](/third-party/#Artalk)。

**jsDelivr**

```yaml
artalk:
  css: https://cdn.jsdelivr.net/npm/artalk@1.0.6/dist/Artalk.css
  js: https://cdn.jsdelivr.net/npm/artalk@1.0.6/dist/Artalk.js
```

**UNPKG**

```yaml
artalk:
  css: https://unpkg.com/artalk@1.0.6/dist/Artalk.css
  js: https://unpkg.com/artalk@1.0.6/dist/Artalk.js
```

### wildfire

[https://github.com/cheng-kang/wildfire](https://github.com/cheng-kang/wildfire/) [https://wildfire.js.org](https://wildfire.js.org/)

Wildfire 评论系统。

详见 [https://theme-cards.ichr.me/third-party/#Wildfire](/third-party/#Wildfire)

**jsDelivr**

```yaml
wildfire: https://cdn.jsdelivr.net/npm/wildfire@0.3.9/dist/wildfire.auto.js
```

**UNPKG**

```yaml
wildfire: https://unpkg.com/wildfire@0.3.9/dist/wildfire.auto.js
```

### mathjax

[https://www.mathjax.org/](https://www.mathjax.org/)

MathJax 数学公式渲染。

**jsDelivr**

```yaml
mathjax: https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
```

**UNPKG**

```yaml
mathjax: https://unpkg.com/mathjax@3/es5/tex-mml-chtml.js
```

**cdnjs**

```yaml
mathjax: https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.0.5/es5/tex-mml-chtml.js
```

**css.net**

```yaml
mathjax: https://cdnjs.loli.net/ajax/libs/mathjax/3.0.5/es5/tex-mml-chtml.js
```

### katex

[https://katex.org/](https://katex.org/)

KaTeX 数学公式渲染。

```yaml
katex:
  css: https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/katex.min.css
  js: https://cdn.jsdelivr.net/npm/katex@0.12.0/dist/katex.min.js
```

**UNPKG**

```yaml
katex:
  css: https://unpkg.com/katex@0.12.0/dist/katex.min.css
  js: https://unpkg.com/katex@0.12.0/dist/katex.min.js
```

**cdnjs**

```yaml
katex:
  css: https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.12.0/katex.min.css
  js: https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.12.0/katex.min.js
```

**css.net**

```yaml
katex:
  css: https://cdnjs.loli.net/ajax/libs/KaTeX/0.12.0/katex.min.css
  js: https://cdnjs.loli.net/ajax/libs/KaTeX/0.12.0/katex.min.js
```

### busuanzi 

[https://busuanzi.ibruce.info](https://busuanzi.ibruce.info)

不蒜子计数系统。

详见 [https://theme-cards.ichr.me/third-party/#不蒜子](/third-party/#不蒜子)

>   此项默认从官方 CDN 而非 jsDelivr 加载。

**官方 CDN**

```yaml
busuanzi: https://busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js
```

**jsDelivr**

```yaml
busuanzi: https://cdn.jsdelivr.net/npm/busuanzi@2.3.0/bsz.pure.mini.js
```

**UNPKG**

```yaml
busuanzi: https://unpkg.com/busuanzi@2.3.0/bsz.pure.mini.js
```

### Artitalk

[https://github.com/ArtitalkJS/Artitalk](https://github.com/ArtitalkJS/Artitalk) 

基于 Leancloud、可实时发布说说的 JS 组件。

**jsDelivr**

```yaml
artitalk: https://cdn.jsdelivr.net/npm/artitalk@3.1.2/artitalk.min.js
```

**UNPKG**

```yaml
artitalk: https://unpkg.com/artitalk@3.1.2/artitalk.jss
```

### jQuery

jQuery 3.4.1 [https://github.com/jquery/jquery/](https://github.com/jquery/jquery/) [https://jquery.com/](https://jquery.com/)

详见 [https://theme-cards.ichr.me/expand/#jQuery](/expand/#jQuery) 

**jsDelivr**

```yaml
jquery: https://cdn.jsdelivr.net/npm/jquery@3.4.1/dist/jquery.min.js
```

**UNPKG**

```YAML
jquery: https://unpkg.com/jquery@3.4.1/dist/jquery.min.js
```

**cdnjs**

```yaml
jquery: https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js
```

**css.net**

```yaml
jquery: https://cdnjs.loli.net/ajax/libs/jquery/3.4.1/jquery.min.js
```

### fancybox

fancybox 3.5.7 [https://github.com/fancyapps/fancybox/](https://github.com/fancyapps/fancybox/) [https://fancyapps.com/fancybox/3/](https://fancyapps.com/fancybox/3/) 

详见 [https://theme-cards.ichr.me/expand/#fancybox](/expand/#fancybox)

**jsDelivr**

```yaml
fancybox: 
  css: https://cdn.jsdelivr.net/npm/@fancyapps/fancybox@3.5.7/dist/jquery.fancybox.min.css
  js: https://cdn.jsdelivr.net/npm/@fancyapps/fancybox@3.5.7/dist/jquery.fancybox.min.js
```

**UNPKG**

```yaml
fancybox: 
  css: https://unpkg.com/@fancyapps/fancybox@3.5.7/dist/jquery.fancybox.min.css
  js: https://unpkg.com/@fancyapps/fancybox@3.5.7/dist/jquery.fancybox.min.js
```

**cdnjs**

```yaml
fancybox: 
  css: https://cdnjs.cloudflare.com/ajax/libs/fancybox/3.5.7/jquery.fancybox.min.css
  js: https://cdnjs.cloudflare.com/ajax/libs/fancybox/3.5.7/jquery.fancybox.min.js
```

**css.net**

```yaml
fancybox: 
  css: https://cdnjs.loli.net/ajax/libs/fancybox/3.5.7/jquery.fancybox.min.css
  js: https://cdnjs.loli.net/ajax/libs/fancybox/3.5.7/jquery.fancybox.min.js
```

### custom_script

自定义 scripts，将追加至 `</body>` 前。

