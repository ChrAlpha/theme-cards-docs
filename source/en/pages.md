---
title: 独立页面
type: docs
permalink: pages/
lang: en
date: 2020-04-24 10:30:12
---



## 文章页面

在新增页面 `front-matter` 中添加以下内容，即定义此页面为文章页面。

```yaml
---
layout: post
---
```

若无此条目，则根据站点配置文件中 `default_layout` 决定页面种类（一般为 `post`）。

仅在文章页面中，你不会看到 Cover 封面。

## 标签云

一般情况下，我们希望标签云路径在 `/tags/` 下（除非你更改过主题配置文件中 `tag_dir` 参数），所以要在 `./source/tags/` 文件夹中新建 `index.md`。使用以下命令即可：

```bash
hexo new page "tags"
```

在新增页面 `front-matter` 中添加以下内容，即定义此页面为标签页面。

```yaml
---
layout: tag
---
```

在标签页面将展示所有文章包含的所有标签，点击对应标签会展示该标签下所有文章。

## 分类一览

一般情况下，我们希望分类页面路径在 `/categories/` 下（除非你更改过主题配置文件中 `categories_dir` 参数），所以要在 `./source/categories/` 文件夹中新建 `index.md`。使用以下命令即可：

```bash
hexo new page "categories"
```

在新增页面 `front-matter` 中添加以下内容，即定义此页面为分类页面。

```yaml
---
layout: category
---
```

在分类页面将展示所有文章归属的所有分类，点击对应分类会展示该分类下所有文章。

## 文章归档

一般情况下，Hexo 会默认讲文章按照发布日期归档，在 `/archives/` 下。除此以外，Hexo 还会默认将文章 **按月归档** 与 **按年归档**。例如一篇 2020 年 4 月 30 号发布的文章会同时被归档至`/archives/`、`/archives/2020/` 与 `/archives/2020/04/` 页面下。

## 友情链接

在站点 `source` 文件夹下创建一个以 `.md` 为后缀的文件，文件名与路径随意，这会决定友链页面渲染后的路径。

>   例如创建 `source/friends/index.md` 则渲染后路径为 `/friends/` ；而 `source/links.md` 则会渲染至 `/links.html` 。

在新增页面 `front-matter` 中添加以下内容，即定义此页面为友链页面。

```yaml
---
layout: links
---
```

友链数据可在 `front-matter` 中添加，假如你想添加 ChrAlpha 博客作为友链。

```
links: 
  - name: ChrAlpha Blog
    url: https://chralpha.com
    avatar: https://friends.ichr.me/img/ichr.me.png
    desc: 你必须拼尽全力，才能显得毫不费力
    target: _blank
    backgroundColor: '#fff'
    textColor: '#444'
```

- `name`: 友链名称
- `url`: 友链地址
- `avatar`: 友链头像
- `desc`: 友链介绍
- `target`: 链接打开方式——（默认）`_blank` 新建标签页打开；`_self` 当前标签页打开
- `backgroundColor`: 友链卡片背景颜色
- `textColor`: 友链文字颜色

以上仅 `name`、`url` 两个参数必填，其余参数选填。

此外，还可以在此填入文件路径以使用外置 JSON 加载方式。

```
links: https://example.com/links.yml
```

```yaml
# https://example.com/links.yml

- name: ChrAlpha Blog
  url: https://chralpha.com
  avatar: https://friends.ichr.me/img/ichr.me.png
  desc: 你必须拼尽全力，才能显得毫不费力
  target: _blank
  backgroundColor: '#fff'
  textColor: '#444'
```

这样每次访问页面时会根据外置文件在浏览器端生成友链页，方便在不修改站点文件的前提下更新友链页面。

## 搜索页面

「Cards」主题支持 [站内搜索](/expand/#站内搜索)，在此之前需要为它单独创建一个页面。

```bash
hexo new page "search"
```

在新增页面 `front-matter` 中添加以下内容，即定义此页面为搜索页面。

```yaml
---
layout: search
---
```

不建议使用其他路径，否则可能需要修改主题源代码才能使其工作。

## 说说页面

「Cards」主题内置了 [Artitalk](https://github.com/ArtitalkJS/Artitalk) 组件，在新增页面 `front-matter` 中加入以下内容，即定义此页面为说说页面。

```yaml
---
layout: artitalk
---
```

此外，你需要将 [Artitalk 配置项](https://artitalk.js.org/settings.html) 填入该页面 `front-matter` 的 `artitalk` 字段下。

```yaml
artitalk: 
  appId: xxx
  appKey: xxx
  serverURL: http://example.com
```

