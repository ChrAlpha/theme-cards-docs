---
title: 基本配置
type: docs
permalink: config/
date: 2020-04-24 10:30:08
---

请使用 Notepad++，VS Code，Vim 等编辑器打开主题配置文件。对于 Windows 用户，**不建议** 使用自带记事本打开配置文件，因为可能会带来难以预测的编码错误。

## Head

生成 HTML 的头部信息 `<head>`。

### favicon

```yaml
favicon:
  ico: 
  small: 
  medium: 
  apple_touch_icon: 
  safari_pinned_tab: 
```

- `ico`: 网站的 favicon，要求是 ico 格式
- `small`: 网站的 favicon，要求是 png 格式、16x16 大小
- `medium`: 网站的 favicon，要求是 png 格式、32x32 大小
- `apple_touch_icon`: 将会显示在 iOS 上，要求是 png 格式，大小在 128px 到 192px 之间
- `safari_pinned_tab`: 将会显示在 Safari 固定标签页、MBP Touchbar 上

你可以在 [这里](https://realfavicongenerator.net/) 生成上述所需的 favicon。对于不需要的配置对应留空即可。

### opengraph

社交链接分享协议，开启后某些社交平台（如 Twitter、Facebook、Telegram 等）粘贴文章链接便能自动生成分享卡片。也有助于爬虫更好地理解你的内容。

```yaml
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

### custom_text

可以在此处随意添加信息，所有内容会被追加到 `<head>` 内，例如搜索引擎所有权验证等。

```yaml
custom_head: 
  - '<meta name="xxxx-site-verification" content="xxxxxxxxxxxxxxxx" />'
  - '<meta name="xxxx-site-verification" content="xxxxxxxxxxxxxxxx" />'
  ...
```

## NavBar

导航栏配置，默认显示在页面最上方。

### sitename

显示在导航栏左侧的名称。若此处留空将自动默认显示站点配置文件的 `title`。

```yaml
sitename: [ name ]
```

### menu

导航栏右侧的按钮菜单，通常用于站内导航。

```yaml
menu: 
  - name: 首页
    url: /
  - name: 标签
    url: /tags/
  - name: 归档
    url: /archives/
  - name: 友链
    url: /friends/
  - name: RSS
    url: /atom.xml
```

每个按钮包含两个参数：`name` 和 `url`。前者定义按钮的显示文字，后者定义点击按钮所跳转的链接。

### sticky

启用此项使导航栏永远置于屏幕顶端，不随页面滚动。仅当屏幕宽度不小于 1080px 时生效。

```yaml
sticky: false
```

## Cover

封面配置，默认显示在**除文章页以外**任何页面顶部。

### sitename

显示在封面的标题，如已设置 `avatar` 则不展示 `sitename` 。若此处留空将自动默认显示站点配置文件的 `title`。

```yaml
sitename: [ title ]
```

### avatar

站点徽标（注意此项与 `favicon` 不同），展示为以 `96px` 为直径的圆形图标。如已设置 `avatar` 则不展示 `sitename`，如果两项均设置将优先展示 `avatar`。

```yaml
avatar: [ url of your avatar image ]
```

### description

一句话介绍/个性签名，展示在 `sitename`/`avatar` 下方。

```yaml
description: Hi, nice to meet you!
```

## Style

用于个性化站点样式。

### color

主要颜色样式，控制导航按钮、ToC、归档页面选中下划线颜色。

```yaml
color: 
  main_color: '#eb5757'
```

### radius

圆角设置，控制卡片圆角半径。

```yaml
radius: 
  main_radius: 5px
```

### space

基准间距，防止板块相距过密。

```yaml
space: 
  main_space: 3.5rem
  sm_space: 1.5rem	# 当屏幕宽度小于 650px 时候启用
```

### highlight / hljs / prismjs

详见 [拓展插件 - 代码高亮](/expand/#%E4%BB%A3%E7%A0%81%E9%AB%98%E4%BA%AE)。

## Meta

设置譬如默认文章标题、日期格式、文章摘要、文章尾部版权声明、自定义 footer 等信息格式。

### title

默认文章标题，当一篇文章不含标题时自动展示此标题顶替。

```yaml
title: no-title
```

### author

默认作者，现暂主要用于 copyright 声明。日后会考虑添加展示文章作者的功能，方便多用户站点。

```yaml
author:
  name: ChrAlpha
  url: https://chralpha.com
```

此设置可在文章 `front-matter` 中覆盖。

### date

文章创建日期，通常展示在首页文章摘要下方与文章页标题下方。

```yaml
date:
  title: ''
  format: 'YYYY-MM-DD'
```

- `title`：展示在创建日期之前的内容
- `format`：展示创建日期所用的日期格式，参照 [Moment.js 文档](https://momentjs.com/docs/)

### updated

文章更新日期，通常展示在文章板块最下方。

```yaml
updated:
  title: ''
  format: 'YYYY-MM-DD'
```

- `title`：展示在更新日期之前的内容
- `format`：展示更新日期所用的日期格式，参照 [Moment.js 文档](https://momentjs.com/docs/)

### thumbnail

文章缩略图，可在页面 `front-matter` 中通过 `thumbnail` 字段请求缩略图。当页面未被设置 `thumbnail` 字段时将自动回退至默认缩略图（`default`）。

如果已使用 [资源文件夹](https://hexo.io/docs/asset-folders)，可将 `relative` 设为 `true` 保证文章缩略图在主页、其他页面也能正常获取。

```yaml
thumbnail: 
  enable: true
  relative: 
  default:
```

### expire

自动为距今超过一定时间的文章添加过时提醒。

```yaml
expire: 
  enable: true
  duration: 120
```

其中 duration 单位为「天」，超过该时长则会自动添加过时提醒。

### auto_excerpt

文章默认摘要，可以（且推荐）使用 `<!--more-->` 标记精确截取文章部分作为摘要。

如果你没有设置 `<!--more-->` 标记且没有设置页面 `description` 参数，则会根据 `auto_excerpt` 是否启用来决定截取指定字数（`length`）的摘要。

```yaml
auto_excerpt: 
  enable: true
  length: 150
```

### toc

文章目录，展示在文章页面侧边栏，支持 h2 ~ h5 级标题（不支持 h1）。

```yaml
toc: 
  enable: true
  list_number: false
```

- `list_number`：自动为目录添加编号

在开启此处全局开关后，也可在特定页面 [Front-matter](/write/#Front-matter) 中关闭 ToC 展示。

>   不支持 h1 是经过考量的。无论是为了 SEO 还是为了文章层次性，都不建议在一个页面中添加多个 h1 标题，而文章 title 已是一个 h1 标题。

### copyright

版权声明，若开启将默认文章板块最下方。

```yaml
copyright: 
  enable: true
  
  # 在作者声明和永久链接之后，可以多行，支持 markdown
  custom_text:
    - '文章默认使用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh) 协议进行许可，使用时请注意遵守协议。'
```

- `custom_text`：在作者声明和永久链接之后显示的内容，可以多行、支持 markdown

可在 `front-matter` 中添加以下内容以关闭指定页面的 copyright 组件展示。

```yaml
copyright: false
```

## Footer

网站页脚内容，展示在网页最下方。

### copyright_since

设置站点起始时间，用于底部 copyright 显示。

例如：将此设为 `2018`，那么页脚就会显示 `© 2018 - 2020`（2020 为最后一次页面生成时间）。

如果将此项留空，则单独显示 `© 2020`（2020 为最后一次页面生成时间）。

如果你不想显示任何内容，请将此项设为 `false`。

```yaml
copyright_since:
```

### statistics

网站计数，目前支持 LeanCloud 与不蒜子两种方案，通过 `use` 字段选择。

```yaml
statistics: 

  use: 

  leancloud: 
    appId: 
    appKey: 
    serverURL: 

  site_uv:
    enable: true
    before_text: '' 
    after_text: Viewers 
    divider: '&nbsp;&nbsp;&nbsp;|' 
  
  site_pv:
    enable: true
    before_text: '' 
    after_text: Views 
    divider: '' 
    
  # 页面 PV
  page_pv:
    enable: true
    before_text: ''
    after_text: Views 
```

- `use`：选择计数系统（目前支持 LeanCloud、不蒜子）
- `leancloud`：选择使用 LeanCloud 所需完善的配置项
- `site_uv`/`site_pv`：全站 Unique Viewers/Page Views
  - `before_text`：展示在数据前的内容，支持 HTML
  - `after_text`：展示在数据后的内容，支持 HTML
  - `divider`：分隔符，支持 HTML
- `page_pv`：单个页面访问数
  - `before_text`：展示在数据前的内容，支持 HTML
  - `after_text`：展示在数据后的内容，支持 HTML

### custom_text

自定义页脚，支持 markdown，可用于展示网站备案等。

```yaml
custom_text: 
  # - ''
  # - ''
```

