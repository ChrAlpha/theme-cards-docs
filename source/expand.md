---
title: 拓展插件
type: docs
permalink: expand/
date: 2020-04-24 10:30:20
---



## Mathjax

在需要渲染数学公式的文章 `front-matter` 中添加：

```yaml
---
mathjax: true
---
```

>   如果你之前有更换过渲染器，请根据自身实际情况调整。

## Lazyload

「Cards」自带图片 Lazyload 的 helper，你无需再安装其他插件。至于启用，你需要将「`optimize` - `lazyload`」条目复制粘贴到 **站点配置文件** 中并对应修改即可。

```yaml
lazyload:
  enable: true
  onlypost: false
  loadingImage: 
```

默认调用 [Vanilla lazyload](https://github.com/verlok/lazyload)，可以在主题配置文件 CDN 设置处修改。

## fancybox

图片点击放大插件，可以前往 Demo 中的图片测试页面查看效果。由于「Cards」定制了自己的 Lazyload 功能，所以即便开启图片懒加载也能很好地兼容 fancybox。

在「`optimize` - `fancybox`」中启用。此插件依赖 jQuery。

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

返回顶部按钮，提供两种方案，分别是引入 JavaScript 实现的平滑滚动回到顶部和直接页内链接 `#` 直接返回顶部。

```yaml
back_to_top: 
  enable: true
  smoothly: true
```

`smoothly` 参数控制着返回顶部实现方式：开启时引入 JavaScript 实现的平滑滚动回到顶部（`smoothly: true`），滑动体验优秀；关闭则是页内链接 `#` 直接返回顶部，虽然动效割裂，但无需再引入外部 JS（`smoothly: false`）。

## darkmode

暗色模式，通过访问者终端 `prefers-color-scheme` 参数控制，亦添加手动切换按钮。

```yaml
darkmode: 
  enable: true
```

## note

标签插件，丰富引用块样式。

```
note: 
  enable: true
```

在文章中插入
```
{% note info 自定义小标题 %}
自定义正文
青山一道同云雨
明月何曾是两乡
{% endnote %}
```
默认支持的样式有 `info` `important` `tip` `caution` `warning`
[样式预览](/demo/2020/06/tag-plugin-note/)
可修改`\themes\cards\source\css\style\note.styl`进行自定义配色及新增更多样式
