---
title: 拓展插件
type: docs
permalink: expand/
date: 2020-04-24 10:30:20
---



以简洁、速度为重的「Cards」仍内置了一些服务，可以在主题配置文件内的 `optimize` 下调整。

## 图片 Lazyload

「Cards」自带图片 Lazyload 的 helper，你无需再安装其他插件，如果你执意安装可能带来难以预计的错误。至于启用，你需要将 `optimize` 下的 `lazyload` 条目复制粘贴到站点配置文件中并对应修改即可。

```yaml
lazyload:
  enable: true
  js: https://cdn.jsdelivr.net/npm/vanilla-lazyload@15.1.1/dist/lazyload.min.js
  onlypost: false
  loadingImage: 
```

默认调用 [Vanilla lazyload](https://github.com/verlok/lazyload)。

## jQuery

事实上「Cards」在制作时一直避免依赖于 jQuery 而更倾向原生 JavaScript 实现，但是还是有部分组件必须调用 jQuery，例如后面提到的 fancybox。

你可以在主题配置文件中「`optimize` - `jquery`」直接修改相关配置。

```yaml
jquery: 
  enable: true
  js: https://cdn.jsdelivr.net/npm/jquery@3.4.1/dist/jquery.min.js
```

## fancybox

图片点击放大插件，可以前往 Demo 中的图片测试页面查看效果。由于「Cards」定制了自己的 Lazyload 功能，所以即便开启图片懒加载也能很好地兼容 fancybox。

由于此插件依赖 jQuery，如需使用请务必确保已经开启 jQuery。

```yaml
fancybox: 
  enable: true
  auto: false
  css: https://cdn.jsdelivr.net/npm/@fancyapps/fancybox@3.5.7/dist/jquery.fancybox.min.css
  js: https://cdn.jsdelivr.net/gh/fancyapps/fancybox@3.5.7/dist/jquery.fancybox.min.js
```

设置 `enable: true` 开启fancybox。默认不应用到所有图片，请在需要使用 fancybox 的包裹在 `<fancybox>` 标记内，例如：

```
<fancybox>
![](https://...)
</fancybox>
```

 而如果将 `auto: true` 开启，则自动应用到所有图片，无需包裹在 `<fancybox>` 内。