---
title: Start
type: docs
permalink: en/start/
date: 2020-04-24 10:30:04
---



Hexo is a blog framework based on Node.js. You can go to the [Hexo official documentation](https://hexo.io/docs/) to learn how to install and initialize Hexo. This document focuses on theme-related configuration, and will not go into detail about Hexo itself.

{% note danger %}

In the following sections, we assume that you **have already** configured Hexo and created a site using it.

{% endnote %}

There is a `_config.yml` file for both the Hexo site and the theme, which are used to store related configuration. Please do not confuse the two. In the following descriptions, we will refer to the `_config.yml` file located in the **site root directory** as the "site configuration file" and the `_config.yml` file located in the theme directory as the "theme configuration file".

Before using Theme Cards, it is recommended that you first complete the basic configuration of the site configuration file, such as the title, description, author, language, and permanent links.

## Install "Cards"

You can go to the [Release page](https://github.com/ChrAlpha/hexo-theme-cards/releases) to download and select the version you need. In the Assets, download the Source Code (zip).

![](/assets/img/download-theme-cards-release.png)

Then, extract the compressed package to the `themes` folder of your site, and rename it to `cards`.

---

Alternatively, you can use Git to pull "Cards", and in the future, you can use `git pull` to update "Cards". Open the terminal in the site root directory and execute:

```bash
git clone https://github.com/ChrAlpha/hexo-theme-cards.git themes/cards
```

## Enable "Cards"

In the site configuration file, change the value of `theme` to `cards`.

> If you renamed the folder to something else when install "Cards", please change cards to the name of the renamed folder.

```yaml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: cards
```

## Start "Cards"

Execute the following command in the site root directory to start Hexo Server for local preview.

```bash
hexo s --debug
```

It is recommended to add the `--debug` parameter for the first run, and use the error log to identify issues if encountered.

When the following output appears, it means that Hexo is listening on port 4000 of the local machine. Visit [localhost:4000](localhost:4000) with a browser to preview the result.

{% note warning %}

If you encounter any issues when using the theme, try searching in this document and feel free to submit an [issue](https://github.com/ChrAlpha/hexo-theme-cards/issues) on GitHub.

{% endnote %}