---
title: "Thumbnails"
date: 2022-09-26
draft: false
description: "Enable thumbnails in your articles."
slug: "thumbnail_sample"
tags: ["thumbnails", "sample"]
summary: "A quick example showing how to start using thumbnails in your articles."
type: 'sample'
---

This is a quick example of using thumbnails in your articles.

If your article directory looks like this:

```shell
content
└── awesome_article.md
```

You need to change it from a single markdown file to a folder with the same name. Create a directory with the same name as the article and add an `index.md` file in this directory. The directory structure looks like this:

```shell
content
└── awesome_article
    └── featured.png
```

Inside the folder, you can add a feature image starting with `feature*` (supports almost all formats, but `.png` or `.jpg` is recommended). The directory structure looks like this:

```shell
content
└── awesome_article
    ├── index.md
    └── featured.png
```

This will tell Blowfish that this article has a feature image, which can be used as a thumbnail on the website and also for <a target="_blank" href="https://oembed.com/">oEmbed</a> cards on social platforms.
As an example, you can try copying and pasting the URL of this article to a platform that can display oEmbeds, such as Twitter, WhatsApp, Telegram, etc.