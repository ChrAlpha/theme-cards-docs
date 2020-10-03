---
title: 拓展插件
type: docs
permalink: expand/
date: 2020-04-24 10:30:20
---



## 代码高亮

Hexo 内置两款代码高亮插件——highlight.js 与 prismjs，而 highlight.js 又分为 Hexo 定制 highlight.js 与原生 highlight.js。这样就对应三个版本：Hexo 定制 highlight.js（`highlihgt`）、原生 highlight.js（`hljs`）与 prismjs（`prismjs`）。

### highlight

在**站点配置文件**中配置 [`highlight`](https://hexo.io/zh-cn/docs/syntax-highlight#config-yml) 字段。请确保 `enable` 为 `true` 且 `hljs` 为 `false`，并将 `primsjs.enable` 设为 `false`。

```
highlight:
  enable: true
  line_number: false
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false
prismjs:
  enable: false
  preprocess: true
  line_number: false
  tab_replace: ''
```

Hexo 定制 highlight.js 是无法直接使用 highlight.js 主题的，为此「Cards」主题定制了 代码高亮主题，并为更贴合主题样式做了些许改动。

由于许多代码高亮主题在亮色/暗色模式下可读性差异较大，在主题配置文件 `style` 字段下可以分别设置亮色/暗色模式下使用的代码高亮主题。

```yaml
style: 
  # ......
  
  highlight: 

    # 默认代码高亮主题
    default: 

    # 暗色代码高亮主题
    darkmode: 
```

这里只需填入代码高亮主题的名称，无需填入路径、后缀等，「Cards」在请求时会将其补全。而在 `vendors.highlight` 中可配置存放代码高亮主题的文件夹路径。

### hljs

在**站点配置文件**中配置 [`highlight`](https://hexo.io/zh-cn/docs/syntax-highlight#config-yml) 字段。请确保 `enable` 与 `hljs` 均为 `true` 且 `line_number` 与 `wrap` 均为 `false`，并将 `primsjs.enable` 设为 `false`。

```yaml
highlight:
  enable: true
  line_number: false
  auto_detect: false
  tab_replace: ''
  wrap: false
  hljs: true
prismjs:
  enable: false
  preprocess: true
  line_number: false
  tab_replace: ''
```

原生 highlight.js 可以直接使用 highlight.js 提供的 [主题](https://github.com/highlightjs/highlight.js/tree/master/src/styles)。同前者一致，在主题配置文件 `style.hljs` 字段下可以分别设置亮色/暗色模式下使用的代码高亮主题、在 `vendors.hljs` 中可配置存放代码高亮主题的文件夹路径。

### prismjs

在**站点配置文件**中配置 [`prismjs`](https://hexo.io/zh-cn/docs/syntax-highlight#PrismJS) 字段。请确保 `enable` 与 `preprocess` 均为 `true`，并将 `highlight.enable` 设为 `false`。

```yaml
highlight:
  enable: true
  line_number: false
  auto_detect: false
  tab_replace: ''
  wrap: false
  hljs: true
prismjs:
  enable: false
  preprocess: true
  line_number: false
  tab_replace: ''
```

prismjs 支持直接使用其提供的 [主题](https://github.com/PrismJS/prism/tree/master/themes)。在主题配置文件 `style` 字段下可以分别设置亮色/暗色模式下使用的代码高亮主题。

```yaml
style: 
  # ......
  
  prismjs: 

    # 默认代码高亮主题
    default: 

    # 暗色代码高亮主题
    darkmode: 
```

同样的，这里只需填入代码高亮主题的名称，无需填入路径、后缀等，「Cards」在请求时会将其补全。而在 `vendors.prismjs` 中可配置存放代码高亮主题的文件夹路径。

## 数学公式

在需要渲染数学公式的文章 `front-matter` 中添加：

```yaml
---
mathjax: true
---
```

>   如果你之前有更换过渲染器，请根据自身实际情况调整。

## 图片懒加载

「Cards」内置图片 Lazyload 插件，为避免冲突请勿安装其他插件。

从「Cards」v1.1.0 开始，**你无需将 `lazyload` 配置项移动至站点配置文件，直接修改主题配置文件便可使相关配置生效。**

```yaml
lazyload:
  enable: true
  onlypost: false
  loadingImage: 
```

## 站内搜索

「Cards」主题内置了站内搜索功能，为避免冲突请勿安装其他插件。在启用之前你需要为其单独 [生成一个页面](/pages/#搜索页面)。

从「Cards」v1.1.0 开始，**你无需将 `search` 配置项移动至站点配置文件，直接修改主题配置文件便可使相关配置生效。**

```yaml
search:
  enable: true
  path: search.json
  field: All  # Page | Post | All
```

其中，`path` 为生成网站数据库的路径，`field` 为数据获取范围。

## 标签插件

标签插件，丰富引用块样式。

```
note: true
```

在文章中使用此插件：

```
{% note [ type ] 自定义小标题 %}

自定义正文

{% endnote %}
```

其中 `[ type ]` 可选填：`info`、`important`、`tip`、`caution`、`warning`，分别对应 5 种样式。

可前往 [主题 Demo](/demo/) 查看 [样式预览](/demo/2020/06/tag-plugin-note/)。

## 内容折叠插件

通过内容折叠插件折叠文章内任一内容片段。

```yaml
fold: 
  enable: true
  summary:   # 默认摘要
  motion: 
```

如果将 `motion` 设置为 `true`，则内容折叠框在折叠/展开时会添加纵向滑动动画。

在文章中使用本插件：

```
{% fold 折叠摘要 %}

自定义正文

{% endfold %}
```

如果你希望某一折叠框默认展开：

```
{% fold open, 折叠摘要 %}

自定义正文

{% endfold %}
```

## fancybox

图片点击放大插件，可以前往 Demo 中的图片测试页面查看效果。由于「Cards」定制了自己的 Lazyload 功能，所以即便开启图片懒加载也能很好地兼容 fancybox。此插件依赖 jQuery。

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

## 返回顶部

返回顶部按钮。

```yaml
back_to_top: true
```

## 暗色模式

暗色模式，通过访问者终端 `prefers-color-scheme` 参数控制，亦添加手动切换按钮。

```yaml
darkmode: true
```
