---
title: 独立博客搭建——通过GitHub Pages与Jekyll——详细教程
author: Cary C
cover: true
categories: 教程
thumbnail: https://cdn.jsdelivr.net/gh/longlivewe/tuchuang/blog/img/picgo/20200502160609.jpg
tags:
  - 博客搭建
  - GitHub Pages
  - Jekyll
abbrlink: bdde
date: 2020-04-28 18:48:47
---

从 WordPress 到 Blogger，最后是 Jekyll，博客搭建之路我走的十分艰辛，这里把踩过的坑大体总结出来。希望对想建站的朋友们有所帮助



本项目是[GitHub Pages](https://pages.github.com/)托管的由[Jekyll](https://jekyllrb.com/)生成的静态博客，博客框架由[Hux](https://github.com/Huxpro)提供

本教程于 Windows 10 专业版 2004 系统下操作

PC 端效果

![](https://s1.ax1x.com/2020/04/28/J44BVK.md.jpg)

手机端效果

![](https://s1.ax1x.com/2020/04/28/J44pjI.md.jpg)



# 目录

* [1. 创建博客](#1-创建博客)
    * [1.1 Fork我的项目](#1-1-Fork我的项目)
    * [1.2 GitHub上的配置](#1-2-GitHub上的配置)
    * [1.3 基础设置](#1-3-基础设置)
    * [1.4 基本用法](#1-4-基本用法)
    * [1.5 域名配置](#1-5-域名配置)
    * [1.6 开始写作](#1-6-开始写作)
* [2. 本地博客预览](#2-本地博客预览)
    * [2.1 从GitHub官网上Clone仓库代码到本地](#2-1-从GitHub官网上Clone仓库代码到本地)
    * [2.2 环境准备与调试](#2-2-环境准备与调试)
    * [2.3 将本地修改同步至GitHub](#2-3-将本地修改同步至GitHub)
* [3. 问题](#3-问题)


# 1. 创建博客
## 1.1 Fork我的项目

首先申请一个[GitHub账户](https://github.com/join?source=header-home)

登录 GitHub 后打开我的[项目库](https://github.com/longlivewe/linshi.github.io)，点击Fork

![](https://s1.ax1x.com/2020/04/28/J4oIIK.md.png)


## 1.2 GitHub上的配置
完成上一步后会自动跳转到如下页面，填写 Repository name，务必与你的 GitHub 用户名一致，严格按照（你的 GitHub 用户名）.github.io 的形式来填写，Rename 确认修改，其它参数保持默认

![](https://s1.ax1x.com/2020/04/28/J4TbkV.md.png)

此时在浏览器打开刚才你配置的域名，就可以看到如下的网站，恭喜你，你已经完成了这项工程的大半

![](https://s1.ax1x.com/2020/04/28/J4HSgg.md.png)

如果此时出现了 404 页面，请确认所填写的 Repository name 是否与 GitHub 用户名完全一致


## 1.3 基础设置

这时你可以看到你的项目已经生成，在 GitHub 的文件基础功能介绍介绍如下，详细请参看 Jekyll 官方文档

| 文件 / 目录   | 描述                                                         |
| :------------ | :----------------------------------------------------------- |
| `_config.yml` | 保存博客配置数据。网站标题，评论设置等基础性配置在此完成     |
| `_includes`   | 你可以加载这些包含部分到你的布局或者文章中以方便重用。可以用这个标签 &#123;&#37; include file.ext &#37;&#125; 来把文件 `_includes/file.ext` 包含进来。 |
| `_layouts`    | layouts（布局）是包裹在文章外部的模板。布局可以在 YAML 头信息中根据不同文章进行选择。 这将在下一个部分进行介绍。标签 &#123;&#123; content &#125;&#125; 可以将content插入页面中。 |
| `_posts`      | 你所写的文章保存在这里。文件名必须为: `年-月-日-文章名.md`   |
| `img`         | 博客的部分图片保存在此并被调用                               |



在项目根目录下的 `_config.yml` 文件中进行基础的配置



![](https://s1.ax1x.com/2020/04/28/JIkuwt.png)



```
title:<博客标题>
SEOTitle:<也是标题，聪明的你一定能找出区别>
header-img:<播客主页题图，保存在img文件夹，可替换，替换后地址务必填写正确>
email:<你的联系邮箱>
description:<博客的介绍>
keyword:<博客的关键词>
url:<你的项目地址>

# SNS settings                                                                 
weibo_username:<填写你的社交媒体账号，下同>

# Disqus settings  #评论
disqus_username:<设置方法见下方> 

# Google Analytics
ga_track_id:<你的Google Analytics ID，用来统计页面访问数据，可忽略。>
ga_domain:<Google Analytics对应的域名>

# Featured Tags
featured-tags: true
featured-condition-size:<拥有相同标签的文章大于这个数字，将会在首页展示这个标签>

```



其中评论的设置比较复杂，操作步骤见下



- 注册[Disqus](https://disqus.com/profile/signup/?next=https%3A//disqus.com/profile/signup/intent/)，登陆后按照如下步骤操作



![](https://s1.ax1x.com/2020/04/28/JIm1f0.png)

- 按照提示填写

![](https://s1.ax1x.com/2020/04/28/JIKs10.png)

- 选择免费版

![](https://s1.ax1x.com/2020/04/28/JIKjNd.png)

- 选则 jekll

![](https://s1.ax1x.com/2020/04/28/JIKv4A.md.png)

- 下一步

![](https://s1.ax1x.com/2020/04/28/JIMFHg.md.png)



- 输入你的网站地址后进行下一步

![](https://s1.ax1x.com/2020/04/28/JIMV4s.md.png)

- 在[这里](https://s1.ax1x.com/2020/04/28/JIm1f0.png)选择你刚才创建的项目

![](https://s1.ax1x.com/2020/04/28/JIMuvV.png)

- 记下这个 ID，这就是填入`disqus_username`的 ID

![](https://s1.ax1x.com/2020/04/28/JIMG59.png)

- 将你的网址填入白名单

![](https://s1.ax1x.com/2020/04/28/JIMt81.md.png)

## 1.4 基本用法



about 页面的更改

![](https://s1.ax1x.com/2020/04/28/JIazdI.md.png)

网站 favicon（可以理解成网站的 Logo）更改

以相同文件名替换

![](https://s1.ax1x.com/2020/04/29/JoMHpR.png)

首页社交媒体图片超链接的增减

![](https://s1.ax1x.com/2020/04/28/JIdSot.md.png)

PWA 设置

![](https://s1.ax1x.com/2020/04/28/JIaxeA.md.png)

## 1.5 域名配置

在[NameSilo](https://www.namesilo.com/)购买域名。注意，购买域名的首年价格多比较便宜，但续费价格会大涨。推荐使用`.top`域名，价格低且稳定

Ping 出你的域名的 IP

![](https://s1.ax1x.com/2020/04/28/JIhv34.md.png)



添加 A 记录，将域名解析到 Ping 到的 IP



![](https://s1.ax1x.com/2020/04/28/JI4QVP.md.png)



在 GitHub 的项目里添加 CNAME



![](https://s1.ax1x.com/2020/04/28/JI4abq.md.png)



强制全站`HTTPS`

`Settings`页面向下拉

![](https://s1.ax1x.com/2020/04/28/JI5PMj.md.png)



勾选`HTTPS`模式

![](https://s1.ax1x.com/2020/04/28/JI59zQ.md.png)


## 1.6 开始写作

文章统一放在 `_posts` 的文件夹中

文件名严格按照`年-月-日-标题.md`

![](https://s1.ax1x.com/2020/04/28/JIBSoR.md.png)



```
---<三个减号不要少>
layout: post<调取模板，无需修改>
title:标题<文章标题>
subtitle: "副标题"<文章副标题>
author: "Cary C"<作者>            
#header-img: "img/home/bg-2019.jpg"<题图，像我这样设置可以让题图直接套用首页图片。自定义请确保图片在img文件夹内，并且引用正确>
header-mask: 0.3
mathjax: true
date: 2020-04-28 <这里将要影响你的博文在主页上的显示顺序>
tags: [Blog,GitHub Pages,Jekyll]<博客标签>                                       
catalog: true
---<三个减号不要少>

以下为博客正文请以markdown语言编写

Markdown WiKi：
Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档。
Markdown 语言在 2004 由约翰·格鲁伯（John Gruber）创建。
Markdown 编写的文档可以导出 HTML 、Word、图像、PDF、Epub 等多种格式的文档。
Markdown 编写的文档后缀为 .md, .markdown。
你一定能通过一个小时的学习熟练掌握这门语言
```



文章写好后，点击保存



![](https://s1.ax1x.com/2020/04/28/JI0zw9.png)

一两分钟后刷新你的网站首页，即可查看你的第一篇博客







# 2. 本地博客预览

## 2.1 从GitHub官网上Clone仓库代码到本地
详见GitHub官方[介绍](https://help.github.com/cn/desktop/contributing-to-projects/cloning-a-repository-from-github-to-github-desktop)


## 2.2 环境准备与调试

Atom 下载[地址](https://atom.io/)，安装

GitHub Desktop 下载[地址](https://desktop.github.com/)，安装

Ruby&DevKit 下载[地址](https://rubyinstaller.org/downloads/)

**Ruby&DevKit 安装**

下载适合系统版本的 Ruby&Devkit 包。安装，弹出的窗口选  3

![](https://s1.ax1x.com/2020/04/28/JI7xgO.md.png)



命令提示符窗口`gem -v` `ruby -v` 查看得到版本号就成功了




![](https://s1.ax1x.com/2020/04/28/JI7v8K.md.png)

**bundler安装**

命令提示符窗口继续`gem install bundler` 安装 bundler

`bundle -v` 查看版本 



![](https://s1.ax1x.com/2020/04/28/JI7LU1.md.png)



**安装 Jekyll**

命令提示符窗口继续`gem install jekyll` 安装 jekyll



![](https://s1.ax1x.com/2020/04/28/JI7O4x.md.png)



在你拉取到本地的项目文件夹目录里`Shift`+`鼠标右键`，选则运行`PowerShell窗口`

运行`jekyll server` 



![](https://s1.ax1x.com/2020/04/28/JI7jC6.png)



打开浏览器输入`127.0.0.1:4000`(下图地址与此相同，数字的更便于记忆)即可看到你的博客内容。如果是 Windows 用户，每次本地文件更新后都要执行一次`jekyll server` 之后才能再一次在本地打开博客



![](https://s1.ax1x.com/2020/04/28/JILGGt.md.png)



## 2.3 将本地修改同步至GitHub

你可以通过`Atom`更改本地代码，或者`Typora`编写博客，在本地文件的改动会被 GitHub Desktop 获取，这时候你只需按照要如下操作



![](https://s1.ax1x.com/2020/04/29/JIX13t.md.png)



最后一步



![](https://s1.ax1x.com/2020/04/29/JIjk5j.md.png)








# 3. 问题

- 文章上传后，需要等一两分钟，Github Pages 就会更新你的博客

- 安装的过程中可能会遇到问题，特别是在本地的操作中容易出现 Bug，将 Bug 代码复制 Google 一下，一定可以解决的

- Jekyll Talk[论坛](https://talk.jekyllrb.com/)

- GitHub Desktop [汉化工具](https://github.com/lkyero/GitHubDesktop_zh)

- Atom [汉化插件](https://www.aityp.com/atom%E7%BC%96%E8%BE%91%E5%99%A8-%E4%B8%AD%E6%96%87%E6%B1%89%E5%8C%96/)
