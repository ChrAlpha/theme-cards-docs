---
title: 独立页面
type: docs
permalink: pages/
date: 2020-04-24 10:30:12
---



## 文章页面

在新增文件 `front-matter` 中添加以下内容，即定义此页面为文章页面。

```yaml
---
layout: post
---
```

若无此条目，则根据站点配置文件中 `default_layout` 决定页面种类（一般为 `post`）。

在文章页面中，你不会看到 cover（封面），取而代之的是「返回首页」按钮展示在顶部。也只有文章页面会渲染后续 markdown 内容，其他页面均不会渲染正文内容。

## 标签云

一般情况下，我们希望标签云路径在 `/tags/` 下（除非你更改过主题配置文件中 `tag_dir` 参数），所以使用下述命令新建页面。

```bash
hexo new page "tags"
```

在新增文件 `front-matter` 中添加以下内容，即定义此页面为标签页面。

```yaml
---
layout: tags
---
```

在标签页面将展示所有文章包含的所有标签，点击对应标签会展示该标签下所有文章。

## 分类览

一般情况下，我们希望分类页面路径在 `/categories/` 下（除非你更改过主题配置文件中 `category_dir` 参数），所以使用下述命令新建页面。

```bash
hexo new page "categories"
```

在新增文件 `front-matter` 中添加以下内容，即定义此页面为标签页面。

```yaml
---
layout: categories
---
```

在分类页面将展示所有文章归属的所有分类，点击对应分类会展示该分类下所有文章。

## 文章归档

一般情况下，我们希望分类页面路径在 `/archives/` 下（除非你更改过主题配置文件中 `archive_dir` 参数），所以使用下述命令新建页面。

```bash
hexo new page "archives"
```

在新增文件 `front-matter` 中添加以下内容，即定义此页面为标签页面。

```yaml
---
layout: archives
---
```

在该归档页面会显示所有文章，按发布时间排序整理为时间轴。

>   除此以外，Hexo 还会默认将文章 **按月归档**。例如一篇 2020 年 4 月 30 号发布的文章将归档至 `/archives/2020/04/` 页面下。

## 友情链接

在站点 `source` 文件夹下创建一个 `.md` 文件，文件名与路径随意，这会决定友链页面渲染后的路径。

>   例如创建 `source/friends/index.md` 则渲染后路径为 `/friends/` ；而 `source/links.md` 则会渲染至 `/links.html` 。

在 `front-matter` 中添加以下内容，将该页面定义为友链页面。

```yaml
---
layout: links
---
```

友链数据需在 `front-matter` 中添加，假如你想添加 ChrAlpha 博客作为友链。

```
links: 
  - name: ChrAlpha Blog
    url: https://chralpha.com
    avatar: https://cdn.jsdelivr.net/npm/chrdnx@1.0.10/img/head-round.png
    backgroundColor: '#fff'
    textColor: '#444'
```

其中背景颜色（backgroundColor）与文字颜色（textColor）可选。