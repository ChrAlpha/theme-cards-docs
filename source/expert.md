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

>   「Cards」v0.5 最重要更新，请确保你使用的主题版本不低于 `0.5.0`。

基于 Hexo 3.0 新增「数据文件」特性，无需直接更改主题 `_config.yml` 便可达到相同效果。

在**站点根目录**下创建 `source/_data/cards.yml`（若 `source/_data` 目录不存在，请新建）。并将你需要修改的内容填写至此（**无需**复制整个主题配置文件），根据约定，这里的内容将覆盖主题配置文件中对应的内容。

例子：

比如你需要修改 opengraph 配置，在主题配置文件中是：

```yaml
# <head> 标签配置
head: 
  
  # 网站图标
  favicon: /favicon.ico
  
  # 社交分享链接
  opengraph: 
    enable: true
    type: 
    twitter_card: summary_large_image
    twitter_id: 
    twitter_site: 
    image: page.thumbnail
    fb_admins: 
    fb_app_id: 

  # 自定义 head
  custom_head: 
    # - ''
    # - ''
```

你只需要在 `source/_data/cards.yml` 中添加：

```yaml
head: 
  opengraph: 
    twitter_id: ichralpha
    twitter_site: ichralpha
```

## CDN

使用 CDN 获取所需的静态资源通常能使请求更加快速、稳定。而主题默认采用 [jsDelivr](https://www.jsdelivr.com)（国内备案，网宿接入，100 SLA，在全球范围内都有很不错的速度），当然你也可以自行选择其他 CDN。

此方面配置请在主题配置文件中定位到 `vendors` 并修改相应配置。

### style

主题默认 CSS 文件，如果你有自定义 `style` ，请务必替换为相应的 CDN 地址或者将此项留空。

**jsDelivr**

```yaml
style: https://cdn.jsdelivr.net/npm/hexo-theme-cards@0.5/dist/css/style.min.css
```

**UNPKG**

```yaml
style: https://unpkg.com/hexo-theme-cards@0.5/dist/css/style.min.css
```

### highlight

目前仅支持默认代码高亮，如果你有修改 `source/github.min.css`，也请替换为相应的 CDN 地址或者将此项留空。

**jsDelivr**

```yaml
highlight: https://cdn.jsdelivr.net/npm/hexo-theme-cards@0.4/dist/css/github.min.css
```

**UNPKG**

```yaml
highlight: https://unpkg.com/hexo-theme-cards@0.4/dist/css/github.min.css
```

### back_to_top

返回顶部按钮，此 JS 用于平滑滚动。

**jsDelivr**

```yaml
back_to_top: https://cdn.jsdelivr.net/npm/hexo-theme-cards@0.2/dist/js/b2t.min.js
```

**UNPKG**

```yaml
back_to_top: https://unpkg.com/hexo-theme-card@0.2/dist/js/b2t.min.js
```

### darkmode

暗色模式切换按钮。

**jsDelivr**

```yaml
darkmode: https://cdn.jsdelivr.net/npm/hexo-theme-cards@0.4/dist/js/darkmode.min.js
```

**UNPKG**

```yaml
darkmode: https://unpkg.com/hexo-theme-cards@0.4/dist/js/darkmode.min.js
```

### lazyload

Vanilla-Lazyload 12.0.0 [https://github.com/verlok/lazyload](https://github.com/verlok/lazyload)

主题内置图片 Lazyload 功能，默认调用 Vanilla Lazyload。

详见 [https://theme-cards.ichr.me/expand/#Lazyload](/expand/#Lazyload)

**jsDelivr**

```yaml
lazyload: https://cdn.jsdelivr.net/npm/vanilla-lazyload@12.0.0/dist/lazyload.min.js
```

**UNPKG**

```yaml
lazyload: https://unpkg.com/vanilla-lazyload@12.0.0/dist/lazyload.min.js
```

**cdnjs**

```yaml
lazyload: https://cdnjs.cloudflare.com/ajax/libs/vanilla-lazyload/12.0.0/lazyload.min.js
```

**css.net**

```yaml
lazyload: https://cdnjs.loli.net/ajax/libs/vanilla-lazyload/12.0.0/lazyload.min.js
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

https://www.mathjax.org/

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

### busuanzi 

[https://busuanzi.ibruce.info](https://busuanzi.ibruce.info)

不蒜子计数系统。

详见 [https://theme-cards.ichr.me/third-party/#不蒜子](https://theme-cards.ichr.me/third-party/#不蒜子)

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

### jQuery

jQuery 3.4.1 [https://github.com/jquery/jquery/](https://github.com/jquery/jquery/) [https://jquery.com/](https://jquery.com/)

详见 [https://theme-cards.ichr.me/expand/#jQuery](https://theme-cards.ichr.me/expand/#jQuery) 

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

详见 [https://theme-cards.ichr.me/expand/#fancybox](https://theme-cards.ichr.me/expand/#fancybox)

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

