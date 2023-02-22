---
title: Expansion Plugins
type: docs
permalink: en/expand/
date: 2023-02-22 20:30:20
---



## Code Highlight

Hexo comes with two built-in code highlighting plugins - highlight.js and prismjs. highlight.js is further divided into customized highlight.js for "Cards" and the original highlight.js. This corresponds to three versions: customized highlight.js for "Cards" (`highlight`), original highlight.js (`hljs`), and prismjs (`prismjs`).

### highlight

Configure the [highlight](https://hexo.io/docs/syntax-highlight#config-yml) in the **site configuration file**. Make sure that `enable` is set to `true`, `hljs` is set to `false`, and `prismjs.enable` is set to `false`.

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

Customized highlight.js for Hexo cannot be used directly with highlight.js themes. Therefore, "Cards" has customized code highlighting themes to fit better with the overall style.

Since the readability of many code highlighting themes varies greatly between light/dark mode, the code highlighting theme used in each mode can be set separately under the `style` in the **theme configuration file**.

```yaml
style: 
  
  highlight: 
    default: 
    darkmode: 
```

- `default`: default code highlighting theme
- `darkmode`: code highlighting theme used in dark mode

Only the name of the highlight theme needs to be filled in here, and no need to include the path or suffix. "Cards" will automatically complete it when requested. The vendor for highlight themes can be configured in `vendors.highlight`.

### hljs

Configure the [highlight](https://hexo.io/docs/syntax-highlight#config-yml) in the **site configuration file**. Make sure that `enable` and `hljs` are both set to true, `line_number` and `wrap` are both set to `false`, and `prismjs.enable` is set to `false`.

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

Original highlight.js can use [themes](https://github.com/highlightjs/highlight.js/tree/master/src/styles) provided by highlight.js directly. Similarly, in the theme configuration file, the highlight theme used in each mode can be set separately under the `style.hljs`. The vendor for highlight themes can be configured in `vendors.hljs`.

### prismjs

Configure the [prismjs](https://hexo.io/docs/syntax-highlight#PrismJS) in the **site configuration file**. Make sure that `enable` and `preprocess` are both set to `true`, and `highlight.enable` is set to `false`.

```yaml
highlight:
  enable: false
  line_number: false
  auto_detect: false
  tab_replace: ''
  wrap: false
  hljs: true
prismjs:
  enable: true
  preprocess: true
  line_number: false
  tab_replace: ''
```

prismjs supports using themes provided by itself directly. In the **theme configuration file**, the highlight theme used in each mode can be set separately under the `style.prismjs`.

```yaml
style: 
  
  prismjs: 
    default: 
    darkmode: 
```

- `default`: default code highlighting theme
- `darkmode`: code highlighting theme used in dark mode

Similarly, only the name of the highlight theme needs to be filled in here, without the need to specify the path or suffix. "Cards" will automatically complete it when making the request. The vendor for highlight themes can be configured in `vendors.prismjs`.

## MathJax

Add the following `front-matter` to any article that requires mathematical formula rendering:

```yaml
---
mathjax: true
---
```

> If you have changed the renderer, adjust according to your actual situation.

## Image Lazyload

"Cards" comes with a Lazyload plugin for images. To avoid conflicts, do not install other plugins.

Starting from "Cards" v1.1.0, you do NOT need to move the lazyload configuration to the **site configuration file**. You can directly modify the **theme configuration file** to make the relevant configuration effective.

```yaml
lazyload:
  enable: true
  onlypost: false
  loadingImage: 
```

- `onlypost`: Enable image lazyload only on article pages
- `loadingImage`: Placeholder image for lazyload

## Local Search

"Cards" has a built-in site search function. To avoid conflicts, do not install other plugins. Before enabling it, you need to [generate a separate page](/pages/#Search) for it.

Starting from "Cards" v1.1.0, you do NOT need to move the search configuration to the **site configuration file**. You can directly modify the **theme configuration file** to make the relevant configuration effective.

```yaml
search:
  enable: true
  path: search.json
  field: All
```

- `path`: Path to the generated website database
- `field`: Data acquisition range (Page | Post | All)

## Tag Plugin

The Tag plugin enriches the style of quote block.

```
note: true
```

To use this plugin in an article:

```
{% note [ type ] Title %}

Main content

{% endnote %}
```

`[ type ]` is optional and can be filled with `info`, `important`, `tip`, `caution`, or `warning`, corresponding to five different styles. You can go to the [theme demo](/demo/2020/06/tag-plugin-note/) to see the style preview.

## Content Folding

Use the Content Folding plugin to fold any content section within an article.

```yaml
fold: 
  enable: true
  summary: 
  motion: 
```

- `summary`: default folding title
- `motion`: adds a vertical slide animation when folding/unfolding

To use this plugin in an article:

```
{% fold Summary %}

Content

{% endfold %}
```

If you want a folding box to be expanded by default:

```
{% fold open, Summary %}

Content

{% endfold %}
```

## fancyBox

fancyBox is a jQuery lightbox script for displaying images, videos and more when touched. You can go to the Demo page for images to test its effect. Since "Cards" has customized its own Lazyload function, even if you enable image lazyload, Fancybox can still be well compatible with it.

```yaml
fancybox: 
  enable: true
  auto: false
```

Setting `enable: true` enables fancyBox. By default, it is not applied to all images. To apply fancyBox to a specific image, wrap it with the `<fancybox>` tag, for example:

```
<fancybox>
![](path/to/image)
</fancybox>
```

If you set `auto: true`, it will be automatically applied to all images without the need to wrap them in the `<fancybox>` tag.

## Back to Top

The Back to Top button.

```yaml
back_to_top: true
```

## Dark Mode

Dark mode, controlled by the visitor's terminal `prefers-color-scheme` parameter, also adds a manual switch button.

```yaml
darkmode: true
```
