---
title: Pages
type: docs
permalink: en/pages/
lang: en
date: 2020-04-24 10:30:12
---



## Article

To define a page as an article page, add the following content to the `front-matter` of the new page:

```yaml
---
layout: post
---
```

If this parametre is undefined or null, the page type will be determined based on the `default_layout` entry in the site configuration file (usually `post`).

Only on article pages, the cover will not be displayed.

## Tag Cloud

By default, we want the tag cloud path to be under `/tags/` (unless you have changed the `tag_dir` parameter in the theme configuration file), so create a new `index.md` in the `./source/tags/` folder using the following command:

```bash
hexo new page "tags"
```

To define this page as a tag page, add the following content to the `front-matter` of the new page:

```yaml
---
layout: tag
---
```

The tag page will display all tags included in all articles, and clicking on the corresponding tag will display all articles under that tag.

## Archive

By default, Hexo archives articles by publication date, under `/archives/`. In addition, Hexo will also archive articles by month and year. For example, an article published on April 30, 2020 will be archived under `/archives/`, `/archives/2020/`, and `/archives/2020/04/`.

## Friends Link

Create a file with a `.md` suffix under the site source folder, and the filename and path will determine the path after the friends link page is rendered.

> For example, creating `source/friends/index.md` will be rendered as `/friends/`; while `source/links.md` will be rendered as `/links.html`.

To define this page as a friends link page, add the following content to the `front-matter` of the new page:

```yaml
---
layout: links
---
```

The friend links data can be added to the `front-matter`. For example, to add ChrAlpha blog as a friend link:

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

- `name`: Name of the friend link
- `url`: URL of the friend link
- `avatar`: Avatar of the friend link
- `desc`: Introduction of the friend link
- `target`: Link opening method: `_blank` opens a new tab (default), `_self` opens in the current tab
- `backgroundColor`: Background color of the friend link card
- `textColor`: Text color of the friend link

Only `name` and `url` are required. Other parameters are optional.

In addition, you can also fill in the file path here to use an external JSON.

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

In this way, the friend link page will be generated on the client-side based on the external file every time the page is accessed, making it easy to update the friend link page without updating site.

## Search Page

"Cards" supports local search and requires a separate page to be created for it.

```bash
hexo new page "search"
```

Add the following content to the new page's `front-matter` to define it as the search page.

```yaml
---
layout: search
---
```

It is not recommended to use other paths, as this may require modification of the theme source code to make it work properly.

## Artitalk

「Cards」主题内置了 [Artitalk](https://github.com/ArtitalkJS/Artitalk) 组件，在新增页面 `front-matter` 中加入以下内容，即定义此页面为说说页面。
The "Cards" theme comes with the Artitalk component, and you can define a page as the Artitalk page by adding the following content to its `front-matter`.

```yaml
---
layout: artitalk
---
```

In addition, you need to fill in the [Artitalk configs](https://artitalk.js.org/settings.html) in `artitalk` of the page's `front-matter`.

```yaml
artitalk: 
  appId: xxx
  appKey: xxx
  serverURL: http://example.com
```

