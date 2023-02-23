---
title: Start Writing
type: docs
permalink: en/write/
lang: en
date: 2023-02-23 10:30:23
---



## Creating a New Post

It is recommended to use the command line to create a new post, which frees you from worrying about many details.

```bash
hexo new "[ title ]"
```

This will create a new `.md` file in the `source/_posts/` directory of your site.

Of course, you can also create the file manually, but then you will need to manually configure the `front-matter`.

## Front-matter

It is recommended to first read the [Hexo Official Document - Front-Matter](https://hexo.io/docs/front-matter.html). "Cards" support the following parameters:

| Key      | Description           | Default | Required |
| --------- | --------------- | ------ | -------- |
| thumbnail | Post thumbnail URL  | none     | Optional   |
| robots    | Spider directive (SEO)	 | none     | Optional   |
| toc       | Show table of contents	    | true   | Optional   |

## Editing/Publishing

After creating a new post, find the file in `source/_posts/`, edit the content, preview it locally with `hexo s`, and deploy it to the remote repository with `hexo d` after making appropriate modifications. You can refer to the [Hexo Official Document - One Command Deployment](https://hexo.io/docs/one-command-deployment.html) for more information.

---

## Finale

That's it for configuring the theme. After you have configured it properly, you should remember to focus on outputting content rather than getting lost in endless tinkering, as "Cards" has always tried to convey. We can't wait to see the site you build with "Cards"!
