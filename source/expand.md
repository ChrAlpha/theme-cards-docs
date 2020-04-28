---
title: 拓展插件
type: docs
permalink: expand/
date: 2020-04-24 10:30:20
---



以简洁、速度为重的「Cards」仍内置了一些拓展插件，可以在主题配置文件内的 `optimize` 下调整。

## Lazyload

「Cards」自带图片 Lazyload 的 helper，你无需再安装其他插件。至于启用，你需要将 `optimize` 下的 `lazyload` 条目复制粘贴到站点配置文件中并对应修改即可。

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

由于此插件依赖 jQuery，如需使用请务必确保已经开启 jQuery。

```yaml
fancybox: 
  enable: true
  auto: false
```

设置 `enable: true` 开启fancybox。默认不应用到所有图片，请在需要使用 fancybox 的包裹在 `<fancybox>` 标记内，例如：

```
<fancybox>
![](https://...)
</fancybox>
```

 而如果将 `auto: true` 开启，则自动应用到所有图片，无需包裹在 `<fancybox>` 内。

fancybox CSS 及 fancybox JS 默认采用 jsDelivr 公共 CDN 加载，可以前往主题配置文件 CDN 设置处修改。