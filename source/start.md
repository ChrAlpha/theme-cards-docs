---
title: 开始使用
type: docs
permalink: start/
date: 2020-04-24 10:30:04
---



Hexo 是一款基于 [Node.js](https://nodejs.org/) 的静态页面生成框架，你可以前往 [Hexo 官方文档](https://hexo.io/zh-cn/docs/) 学习如何安装及初始化 Hexo。本文档专注于主题相关的配置，Hexo 方面将不再赘述。

{% note danger %}

在接下来的篇幅中，我们假定你已经**配置好 Hexo 并用其创建了一个站点**。

{% endnote %}

在 Hexo 站点及主题目录各有一个 `_config.yml` 文件用于存放相关配置，请勿混淆。下文为描述方便，我们将位于 **站点根目录** 的 `_config.yml` 称为「站点配置文件」，将位于主题目录内的 `_config.yml` 称为「主题配置文件」。

在使用 Theme Cards 前，建议先完成站点配置文件的基本配置，如标题、介绍、作者、语言、永久链接等。

## 获取「Cards」

你可以前往 [Release 页面](https://github.com/ChrAlpha/hexo-theme-cards/releases) 下载，选择你需要的版本，在该页面中扎到 Assets 区域，下载 Source Code（zip）到本地。

![](/assets/img/download-theme-cards-release.png)

然后将压缩包解压到站点的 `themes` 文件夹内，并更名为 `cards`。

---

你也可以使用 Git 拉取「Cards」，以后还可以使用 `git pull` 直接更新「Cards」。在站点根目录打开终端，并执行：

```bash
git clone https://github.com/ChrAlpha/hexo-theme-cards.git themes/cards
```

## 启用「Cards」

在站点配置文件中，将 `theme` 的值改为 `cards`。

>   如果获取「Cards」时你将文件夹重命名为其他名字，请将 `cards` 对应为你重命名文件夹的名字。

```yaml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: cards
```

## 运行「Cards」

在站点根目录执行下述命令，启动 Hexo Server 本地预览。

```bash
hexo s --debug
```

初次运行建议添加 `--debug` 参数，在遇到错误时也可通过错误日志让他人更快地了解问题所在。

当有如下输出时，便意味着 Hexo 正在监听本机 4000 端口，使用浏览器访问 [localhost:4000](http://localhost:4000) 预览效果。

{% note warning %}

如果你在使用的时候有任何问题，欢迎在 GitHub 上提交 [issue](https://github.com/ChrAlpha/hexo-theme-cards/issues)，当然最好在充分阅读过文档的前提下仍有疑问时再考虑新建 issue。

{% endnote %}