---
title: "Homepage Layout"
weight: 5
draft: false
description: "Setting up homepage layouts in the Blowfish theme."
slug: "homepage-layout"
tags: ["homepage", "layout", "documentation"]
series: ["Deployment Guide"]
series_order: 5
---

Blowfish provides a completely flexible homepage layout. You can choose from two main templates and additional parameters to help adjust the design. Of course, you can also provide your own template for complete control over homepage content.

The homepage layout is controlled by the `homepage.layout` parameter in the `params.toml` configuration file. Additionally, all layouts include [Recent Articles](#recent-articles) by default.

## Profile Layout

The default layout is the profile layout, which is perfect for personal websites and blogs. It centers the author's details with an avatar and social platform links.

{{< figure src="img/home-profile.png" class="thumbnailshadow" >}}

Author information is provided in the language configuration file. For specific parameter details, refer to [Getting Started]({{< ref "docs/getting-started" >}}) and [Language Configuration]({{< ref "docs/configuration##language-and-i18n" >}}).

Additionally, any Markdown provided in the homepage content will be displayed below the author profile. This provides more flexibility for displaying introductions or other custom homepage content using shortcodes.

To enable the profile layout, set `homepage.layout = "profile"` in the `params.toml` configuration file.

## Page Layout

The page layout simply displays your Markdown content, which is perfect for static websites and provides great flexibility.

{{< figure src="img/home-page.png" class="thumbnailshadow" >}}

To enable the page layout, set `homepage.layout = "page"` in the `params.toml` configuration file.

## Hero Layout

The hero layout combines the profile layout and card layout. It not only displays the website author's personal information but also loads your markdown content below the profile.

{{< figure src="img/home-hero.png" class="thumbnailshadow" >}}

To enable the hero layout, set `homepage.layout = "hero"` in the `params.toml` configuration file.

## Background Layout

The background layout is smoother compared to the hero layout. Similar to the hero layout, it also displays the website author's information and loads markdown content below it.

{{< figure src="img/home-background.png" class="thumbnailshadow" >}}

To enable the background layout, set `homepage.layout = "background"` and `homepage.homepageImage` in the `params.toml` configuration file.

## Card Layout

The card template is an extension of the page layout that also provides flexibility. While displaying your markdown content, it shows an image in a card component.

{{< figure src="img/home-card.png" class="thumbnailshadow" >}}

To enable the card layout, set `homepage.layout = "card"` and `homepage.homepageImage` in the `params.toml` configuration file.

## Custom Layout

If the above layouts don't meet your needs, you can create your own custom layout. This gives you complete control over page content based on a blank canvas.

To enable the custom layout, set `homepage.layout = "custom"` in the `params.toml` configuration file.

After configuring the parameters, create a `custom.html` file in the `layouts/partials/home` directory. Any content defined in the `custom.html` file will be placed in the content area of the website homepage. You can use HTML, Tailwind, or Hugo template functions to define your layout.

If you want to add [Recent Articles](#recent-articles) to your custom layout, use the content from `recent-articles/main.html`.

If you want to use a custom layout on the website [homepage]({{< ref "/" >}}) to switch between profile and page layouts, there's an example in this [GitHub repository](https://github.com/nunocoracao/blowfish/blob/main/exampleSite/layouts/partials/home/custom.html) for reference.

## Recent Articles

All homepage layouts can display recent articles below the main content. To enable this feature, simply set the `homepage.showRecent` parameter to `true` in the `params.toml` configuration file.

{{< figure src="img/home-list.png" class="thumbnailshadow" >}}

This section will list articles from the sections you set in the `mainSections` parameter, which allows you to use any content type on your website. For example, if you want to display articles from both _posts_ and _projects_ content in recent articles, you can set this value to `["posts", "projects"]`, and all articles from both sections will populate the recent articles list. The Blowfish theme expects this parameter to be an array, so if you only want to set all articles from one section, you can set it to `["blog"]`.

## Thumbnails

Blowfish provides visual support for your articles. If you're familiar with Hugo's article structure, simply place an image file starting with `feature*` in your article's corresponding folder. The image type supports almost all formats, with `.png` or `.jpg` being more recommended. This way, Blowfish will use that image as a thumbnail on your website and in <a target="_blank" href="https://oembed.com/">oEmbed</a> cards on social media platforms.

[Here]({{< ref "docs/thumbnails" >}}) is more detailed content, with an easy-to-understand [example]({{< ref "thumbnail_sample" >}}).

## Card Gallery

Blowfish supports displaying standard article lists as card galleries. You can configure this option in the recent articles on the homepage and article lists on the website.
- For the homepage, use the `homepage.cardView` and `homepage.cardViewScreenWidth` parameters
- For list pages, use the `list.cardView` and `list.cardViewScreenWidth` parameters
Please check the [Configuration]({{< ref "docs/configuration" >}}) for more information.