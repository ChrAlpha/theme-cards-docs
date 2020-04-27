---
title: 开始创作
type: docs
permalink: write/
date: 2020-04-24 10:30:23
---



## 创建文章

建议使用命令行创建文章，这样便无需在意许多细节。

```bash
hexo new "[ title ]"
```

这样便会在站点目录下 `source/_posts` 目录新建 `.md` 文件。

当然你也可以在相应位置手动创建，不过此时你需要手动配置 `front-matter` 。

## Front-matter

建议先阅读 [Hexo 官方文档 - Front-Matter](https://hexo.io/zh-cn/docs/front-matter.html) ，「Cards」在其基础上新增了：

| 参数      | 描述            | 默认值 | 是否必要 |
| --------- | --------------- | ------ | -------- |
| thumbnail | 文章缩略图地址  | 无     | 非必要   |
| robots    | 爬虫声明（SEO） | 无     | 非必要   |

## 编辑/发布

新建一篇文章后，前往 `source/_posts/` 找到该文件，编辑好内容先 `hexo s` 本地预览，修改妥当后 `hexo d` 部署到远程仓库中。你可以参考 [Hexo 官方文档 - 一键部署](https://hexo.io/zh-cn/docs/one-command-deployment.html) 了解更多。

---

## 尾声

至此主题相关配置便告一段落了。主题配置妥帖之后你需要注意，就像「Cards」一直试图表达的，专注于内容输出而非沉溺在无尽的折腾中。我们迫不及待地想与你借助「Cards」建立的站点相遇！