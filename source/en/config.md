---
title: Configuration
type: docs
permalink: en/config/
lang: en
date: 2022-02-23 10:30:08
---



Please use VS Code (or Notepad++, Vim, etc) editors to edit theme configuration file. For Windows users, it's NOT recommanded to open configuration files with Windows default notepad, since it may bring unexpected encoding errors.

## Head

The `<head>` section of HTML.

### favicon

```yaml
favicon:
  ico: 
  small: 
  medium: 
  apple_touch_icon: 
  safari_pinned_tab: 
```

- `ico`: The website's favicon in `.ico` format.
- `small`: The website's favicon in `.png` format, with a size of 16x16 pixels.
- `medium`: The website's favicon in `.png` format, with a size of 32x32 pixels.
- `apple_touch_icon`: The icon that will be displayed on iOS devices, in `.png` format with a size between 128px and 192px.
- `safari_pinned_tab`: The icon that will be displayed on Safari's pinned tabs and on the MacBook Pro's Touch Bar.

You can generate the required favicons [here](https://realfavicongenerator.net/). Leave the fields empty for configurations that are not needed.

### opengraph

Social sharing protocol that allows certain social media platforms (such as Twitter, Facebook, Telegram, etc.) to automatically generate sharing cards when the article link is sended. It also helps web crawlers to better understand your content.

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

You can add any information here, and it will be appended to the `<head>` section. For example, verification tags for search engines console or webmaster tools.

```yaml
custom_head: 
  - '<meta name="xxxx-site-verification" content="xxxxxxxxxxxxxxxx" />'
  - '<meta name="xxxx-site-verification" content="xxxxxxxxxxxxxxxx" />'
  ...
```

## NavBar

The navigation bar configuration. NavBar is displayed by default at the top of the page.

### sitename

The name displayed on the left side of the navigation bar. If left empty, it will default to the `title` of the site configuration file.

```yaml
sitename: [ name ]
```

### menu

The button menu on the right side of the navigation bar, usually used for internal navigation.

```yaml
menu: 
  - name: Home
    url: /
  - name: Tags
    url: /tags/
  - name: Archives
    url: /archives/
  - name: Friends
    url: /friends/
  - name: RSS
    url: /atom.xml
```

Each button has two parameters: `name` and `url`. The former defines the display text of the button, and the latter defines the link where the button will take the user to.

### sticky

Enabling this option will make the navigation bar always stay at the top of the screen and not move when the page is scrolled. This only takes effect when the screen width is at least 1080px.

```yaml
sticky: false
```

## Cover

The cover configuration that is displayed by default at the top of all pages **except for article pages**.

### sitename

The title displayed on the cover. If `avatar` has been set, `sitename` will not be displayed. If left empty, it will default to the `title` of the site configuration file.

```yaml
sitename: [ title ]
```

### avatar

Site logo (different from `favicon`), displayed as a circular icon with a diameter of `96px`. If an `avatar` has been set, the sitename will not be displayed. If both `avatar` and `sitename` are set, the `avatar` will be prioritized.

```yaml
avatar: [ url of your avatar image ]
```

### description

A signature displayed below the `sitename`/`avatar`.

```yaml
description: Hi, nice to meet you!
```

## Style

Used for customizing site styles.

### color

The main color style that controls the color of the navigation buttons, Table of Contents (ToC), and the underline color on the archive page when selected.

```yaml
color: 
  main_color: '#eb5757'

```

### radius

Sets the rounding radius and controls the rounding radius of the card.

```yaml
radius: 
  main_radius: 5px
```

### space

The baseline spacing that prevents the panels from being too close together.

```yaml
space: 
  main_space: 3.5rem
  sm_space: 1.5rem	# Enabled when the screen width is less than 650px
```

### highlight / hljs / prismjs

Refer to "Expansion Plugin - Code Highlighting" for more details.

## Meta

The Meta settings control information such as the default article title, date format, article summary, footer copyright statement, and custom footer formats.

### title

The default article title, which is automatically displayed if an article has no title.

```yaml
title: no-title
```

### author

The default author, mainly used for copyright statements. The ability to display the author of an article will be considered in the future, which will be helpful for multi-author sites.

```yaml
author:
  name: ChrAlpha
  url: https://chralpha.com
```

This setting can be overridden in the `front-matter` of an article.

### date

The date the article was created, usually displayed below the article summary on the home page and under the article title on the article page.

```yaml
date:
  title: ''
  format: 'YYYY-MM-DD'
```

- `title`: the text to display before the date
- `format`: the date format to use, as specified in the [Moment.js documentation](https://momentjs.com/docs/)


### updated

The date the article was last updated, usually displayed at the bottom of the article section.

```yaml
updated:
  title: ''
  format: 'YYYY-MM-DD'
```

- `title`: the text to display before the updated date
- `format`: the date format to use, as specified in the [Moment.js documentation](https://momentjs.com/docs/)

### thumbnail

The thumbnail image for the article. `thumbnail` can be set in the `front-matter` of an article. If no `thumbnail` is set, the `default` will be used.

If the [asset folder](https://hexo.io/docs/asset-folders) has been set up, set `relative` to `true` to ensure that the thumbnail image can be obtained correctly on the home page and other pages.

```yaml
thumbnail: 
  enable: true
  relative: 
  default:
```

### expire

Automatically adds a warning message to articles that have been published for a certain period of time.

```yaml
expire: 
  enable: true
  duration: 120
```

The `duration` is in days. If an article is older than this value, a warning message will be added.

### auto_excerpt

The default article summary. You can (and are recommended to) use the `<!--more-->` tag to specify the portion of the article to be used as the summary.

If you do not set the `<!--more-->` tag and do not specify the description, then the `auto_excerpt` will determine whether intercept a summary of the specified number of words (`length`).

```yaml
auto_excerpt: 
  enable: true
  length: 150
```

### toc

The table of contents for the article, displayed in the sidebar of the article page. Supports headings h2 to h5 (but not h1).

```yaml
toc: 
  enable: true
  list_number: false
```

- `list_number`: automatically numbers the items in the table of contents

After turning on this global switch, you can also turn off the ToC display in specific pages in the [Front-matter](/write/#Front-matter) of those pages.

> It is not recommended to have multiple h1 titles on one page for SEO or for the hierarchy of the article. The article title is already an h1 title.

### copyright

Displays a copyright statement at the bottom of the article.

```yaml
copyright: 
  enable: true
  
  # 在作者声明和永久链接之后，可以多行，支持 markdown
  # Multiple lines of text are allowed after the author statement and permanent link, supporting markdown format
  custom_text:
    - '文章默认使用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh) 协议进行许可，使用时请注意遵守协议。'
```

- `custom_text`: The text to be displayed after the author statement and permanent link. Multiple lines of text are allowed and the text supports markdown format.

To disable the copyright display for a specific page, add the following content to the `front-matter`.

```yaml
copyright: false
```

## Footer

Displays the website footer at the bottom of the web page.

### copyright_since

Specifies the website start time for the copyright display.

For example, if set to `2018`, the footer will display `© 2018 - 2020` (2020 is the last time the page was generated).

If left empty, the footer will display `© 2020` (2020 is the last time the page was generated).

If you don't want to display any content, set this to `false`.

```yaml
copyright_since:
```

### statistics

Displays website statistics, and currently supports two systems: LeanCloud and Busuanzi. Choose the system using the `use`.

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

- use: Choose the statistics system (currently supports LeanCloud and Busuanzi).
- leancloud: Additional configuration items required for using LeanCloud.
- site_uv/site_pv: Unique viewers and page views for the entire website.
  - before_text: Text to be displayed before the data, in HTML format.
  - after_text: Text to be displayed after the data, in HTML format.
  - divider: Separator, in HTML format.
- page_pv: Page views for a single page.
  - before_text: Text to be displayed before the data, in HTML format.
  - after_text: Text to be displayed after the data, in HTML format.

### custom_text

Customizes the website footer, supporting markdown format.

```yaml
custom_text: 
  # - ''
  # - ''
```

