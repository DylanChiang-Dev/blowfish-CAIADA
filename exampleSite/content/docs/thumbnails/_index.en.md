---
title: "Thumbnails"
weight: 10
draft: false
description: "Configure thumbnails for your articles."
slug: "thumbnails"
tags: ["thumbnails", "configuration", "documentation"]
series: ["Deployment Tutorial"]
series_order: 6
---

## Thumbnails

Blowfish has enhanced visual support that allows you to easily add thumbnails to your articles. You simply need to place an image file starting with `feature*` (supports almost all formats, but `.png` or `.jpg` is more recommended) in the directory where the article is located, as shown below:

```shell
content
└── awesome_article
    ├── index.md
    └── featured.png
```

This will tell Blowfish that this article has a feature image, which can be used as a thumbnail on the website and also for <a target="_blank" href="https://oembed.com/">oEmbed</a> cards on social platforms.

## File Structure

If you are only using a single `.md` file as an article, the file structure looks like this:

```shell
content
└── awesome_article.md
```

If you want to add thumbnails, you need to put the single Markdown file in a folder. Create a directory with the same name as the article and create an `index.md` file in it. The file structure looks like this:

```shell
content
└── awesome_article
    └── index.md
```

Then you just need to add a feature image as before. If you want to see an example, you can refer to [this example]({{< ref "samples/thumbnail_sample" >}}).

## Hero Images

Thumbnails will be used as hero images for each article by default. To enable this feature, you can use the global `article.showHero` parameter to control all articles on the entire site, or the front matter parameter `showHero` to control individual articles. If you want to override the hero image style, you can create a file named `hero.html` in the `./layouts/partials/` folder, which will override the default partial in the theme.