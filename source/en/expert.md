---
title: Advanced Using
type: docs
permalink: en/expert/
lang: en
date: 2020-06-13 14:30:08
---

## Using Git With Hexo

As mentioned in the [Started](/en/start/), we recommend using Git to obtain the theme files so that you can promptly update to new versions.

If you want to manage your entire site with Git, you'll need to use `git submodule` to avoid conflicts.

`git submodule` allows you to clone another repository into your Git project while still keeping the commits separate.

1. Get "Cards" as a submodule

    ```bash
    git submodule add https://github.com/ChrAlpha/hexo-theme-cards.git themes/cards
    ```

2.  Update "Cards" to the latest version

    ```bash
    git submodule update --remote
    ```

In this way, you only need to clone the site repository to obtain both site and theme files.

```bash
git clone --recurse-submodules https://github.com/[ GitHub ID ]/[website source].git
```

For more detailed information on git submodule, please refer to the [Git document](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

## Smooth Updates

With the addition of [Data Files](https://hexo.io/docs/data-files.html) in Hexo 3.0, you can achieve the same effect as modifying theme `_config.yml` file without directly editing it. This allows for modifications to the theme configuration file to be stored outside of the theme folder, making it easy to manage theme versions with Git without manually changing the theme configuration file each time an update is released.

Create `source/_data/cards.yml` in the **root directory of your site** (if the `source/_data/` does not exist, create it). Enter the content you want to modify here (**without** copying the entire theme configuration file). The content here will overwrite the corresponding content in the theme configuration file.

> This feature is supported from "Cards" v0.5.0 onwards.

{% note success %}

Example:

Suppose you need to modify the OpenGraph configuration. In the theme configuration file, it looks like this:

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

You only need to add the following to `source/_data/cards.yml`:

```yaml
head: 
  opengraph: 
    twitter_id: ichralpha
    twitter_site: ichralpha
```

{% endnote %}

## CDN

Using a CDN to obtain required static resources can often result in faster and more stable requests. "Cards" defaults to using [jsDelivr](https://www.jsdelivr.com), but you can also choose to use another CDN of your choice.

To configure this, modify the `vendors` in the theme configuration file.

### style

主题默认 CSS 文件，如果你有自定义 `style` ，请务必替换为相应的 CDN 地址或者将此项留空。
Theme "Cards" default CSS. If you have modified 

**jsDelivr**

```yaml
style: https://cdn.jsdelivr.net/npm/hexo-theme-cards@1.4/dist/css/style/main.min.css
```

**UNPKG**

```yaml
style: https://unpkg.com/hexo-theme-cards@1.4/dist/css/style/main.min.css
```

### darkmode

Dark Mode related vendors

**jsDelivr**

```yaml
darkmode: 
  css: https://cdn.jsdelivr.net/npm/hexo-theme-cards@1.4/dist/css/style/dark.min.css
  js: https://cdn.jsdelivr.net/npm/hexo-theme-cards@1.4/dist/js/darkmode.min.js
```

**UNPKG**

```yaml
darkmode: 
  css: https://unpkg.com/hexo-theme-cards@1.4/dist/css/style/dark.min.css
  js: https://unpkg.com/hexo-theme-cards@1.4/dist/js/darkmode.min.js
```

### highlight

[Expansion Plugins - #highlight](/en/expand/#highlight) 

Customized highlight.js themes for "Cards".

**jsDelivr**

```yaml
highlight: https://cdn.jsdelivr.net/npm/hexo-theme-cards@1.4/dist/css/highlight/
```

**UNPKG**

```yaml
highlight: https://unpkg.com/hexo-theme-cards@1.4/dist/css/highlight/
```

### hljs

[https://highlightjs.org/](https://highlightjs.org/) 

Original highlight.js themes.

More info：[Expansion Plugins - #hljs](/en/expand/#hljs) 

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

PrismJS theme。

More Info: [Expansion Plugins - #prismjs](/en/expand/#prismjs) 

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
prismjs: https://cdnjs.loli.net/ajax/libs/prism/1.21.0/themes/
```

### lazyload

Vanilla-Lazyload 17.1.2 [https://github.com/verlok/lazyload](https://github.com/verlok/lazyload)

Vanilla Lazyload Plugin 

More info: [Expansion Plugins - #Lazyload](/en/expand/#Lazyload)

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

Valine comment system。

More info: [Third Party Services - #Valine](/en/third-party/#Valine)

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

MiniValine comment system。

More info: [Third Party Services - #MiniValine](/en/third-party/#MiniValine)

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

Artalk comment system。

More info: [Third Party Services - #Artalk](/en/third-party/#Artalk)。

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

Wildfire comment system。

More Info: [Third Party Services - #Wildfire](/en/third-party/#Wildfire)

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

MathJax rendering.

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

KaTeX rendering。

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

Busuanzi analytics system

More Info: [Third Party Services - #Busuanzi](/en/third-party/#Busuanzi)

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

Leancloud-based JS component for real-time publishing of sayings.

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

More Info: [Expansion Plugins - #jQuery](/en/expand/#jQuery) 

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

### fancyBox

fancyBox 3.5.7 [https://github.com/fancyapps/fancybox/](https://github.com/fancyapps/fancybox/) [https://fancyapps.com/fancybox/3/](https://fancyapps.com/fancybox/3/) 

More Info: [Expansion Plugins - #fancyBox](/en/expand/#fancyBox)

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

Costom scripts that will be appended before `</body>`.

