---
title: 拓展插件
type: docs
permalink: expand/
date: 2020-04-24 10:30:20
---



## Mathjax

由于部分 LaTeX 语法会与 Markdown 语法冲突，此时最简单的方法是更换有针对优化过的渲染器。

```bash
npm uninstall hexo-renderer-marked --save

npm install hexo-renderer-markdown-it-plus --save
```

然后在站点配置文件中添加：

```yaml
markdown_it_plus:
  highlight: true
  html: true
  xhtmlOut: true
  breaks: true
  langPrefix:
  linkify: true
  typographer: true
  quotes: ‘’“”
  plugins:
    - plugin:
      name: markdown-it-mark
      enable: false
```

最后在需要渲染数学公式的文章 `front-matter` 中添加：

```yaml
---
mathjax: true
---
```

[hexo-renderer-markdown-it-plus](https://github.com/CHENXCHEN/hexo-renderer-markdown-it-plus) 

>   如果你之前有更换过渲染器，请根据自身实际情况调整。

## Lazyload

「Cards」自带图片 Lazyload 的 helper，你无需再安装其他插件。至于启用，你需要将「`optimize` - `lazyload`」条目复制粘贴到站点配置文件中并对应修改即可。

```yaml
lazyload:
  enable: true
  onlypost: false
  loadingImage: 
```

默认调用 [Vanilla lazyload](https://github.com/verlok/lazyload)，可以在主题配置文件 CDN 设置处修改。

## jQuery

事实上「Cards」在制作时一直避免依赖于 jQuery 而更倾向原生 JavaScript 实现，但是还是有部分组件必须调用 jQuery，例如后面提到的 fancybox。

你可以在主题配置文件中「`optimize` - `jquery`」直接修改相关配置。

```yaml
jquery: 
  enable: true
```

资源调用可以前往主题配置文件 CDN 设置处修改，默认使用 jsDelivr 公共 CDN 库加载。

## fancybox

图片点击放大插件，可以前往 Demo 中的图片测试页面查看效果。由于「Cards」定制了自己的 Lazyload 功能，所以即便开启图片懒加载也能很好地兼容 fancybox。

在「`optimize` - `fancybox`」中启用。由于此插件依赖 jQuery，如需使用请务必确保已经开启 jQuery。

```yaml
fancybox: 
  enable: true
  auto: false
```

设置 `enable: true` 开启 fancybox。默认不应用到所有图片，请在需要使用 fancybox 的包裹在 `<fancybox>` 标记内，例如：

```
<fancybox>
![](path/to/image)
</fancybox>
```

 而如果将 `auto: true` 开启，则自动应用到所有图片，无需包裹在 `<fancybox>` 内。

fancybox CSS 及 fancybox JS 默认采用 jsDelivr 公共 CDN 加载，可以前往主题配置文件 CDN 设置处修改。

## back_to_top

回到顶部按钮，提供两种方案，分别是引入 JavaScript 实现的平滑滚动回到顶部和直接页内链接 `#` 直接返回顶部。

```yaml
back_to_top: 
  enable: true
  smoothly: true
```

`smoothly` 参数控制着返回顶部实现方式：开启时引入 JavaScript 实现的平滑滚动回到顶部（`smoothly: true`），滑动体验优秀；关闭则是直接页内链接 `#` 直接返回顶部，虽然动效割裂，但无需再引入外部 JS（`smoothly: false`）。