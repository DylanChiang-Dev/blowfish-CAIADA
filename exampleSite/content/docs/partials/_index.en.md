---
title: "Partials"
weight: 9
draft: false
description: "All configurable Partials in Blowfish"
slug: "partials"
tags: ["partials", "analytics", "privacy", "comments", "favicons", "icons", "documentation"]
series: ["Deployment Guide"]
series_order: 9
---

## Site Analytics

Blowfish supports Fathom, Google, and Umami analytics. Fathom and Umami are both open-source, simple, and privacy-focused site analytics services that serve as excellent alternatives to Google Analytics. Both Fathom and Umami offer paid cloud versions, or you can self-host the open-source versions.

### Fathom

To enable Fathom Analytics support, simply provide your Fathom site code in the `config/_default/params.toml` file. If you're also using Fathom's custom domain feature and want to serve the script from your domain, you can additionally provide the `domain` configuration value. If no `domain` value is provided, the script will be served directly from Fathom's cloud service address (cdn.usefathom.com).

```toml
# config/_default/params.toml

[fathomAnalytics]
  site = "ABC12345"
  domain = "llama.yoursite.com"
```

### Google

Hugo partial already supports Google Analytics. Simply add the `googleAnalytics` parameter in the `config/_default/config.toml` file, and the tracking script will be automatically added.

Both version 3 (analytics.js) and version 4 (gtag.js) are supported, as shown in the following examples:

```toml
# config/_default/config.toml

# Version 3
googleAnalytics = "UA-PROPERTY_ID"
# Version 4
googleAnalytics = "G-MEASUREMENT_ID"
```

### Umami

Simply provide your [Umami tracking code](https://umami.is/docs/collect-data) in the `config/_default/params.toml` file to quickly enable Umami site analytics.
If you want to use a custom domain to fetch the tracking script, you need to provide the `domain` parameter, otherwise it will fetch the script from Umami's cloud service address (analytics.umami.is).
If you only want to use the tracker functionality on specific domains, you need to provide the `dataDomains` parameter. Otherwise, the Umami script will execute on any website that matches the `websiteid` and `domain` parameter values. If the environment variable `TRACKER_SCRIPT_NAME` is configured, you can fill in the custom script name `scriptName`, otherwise comment it out or fill in the default `script.js`.

{{< alert >}}
**Note:** After enabling Umami website analytics, Blowfish will automatically support [Umami event tracking](https://umami.is/docs/track-events). If you don't want to support this feature, you need to set the parameter `enableTrackEvent` to `false`.
{{< /alert >}}

```toml
# config/_default/params.toml

[umamiAnalytics]
  websiteid = "ABC12345"
  domain = "llama.yoursite.com"
  dataDomains = "yoursite.com,yoursite2.com"
  scriptName = "TRACKER_SCRIPT_NAME"
  enableTrackEvent = true
```

### Seline

Simply provide your [Seline token](https://seline.so/docs/install-seline) in the `config/_default/params.toml` file to quickly enable Seline site analytics.

{{< alert >}}
**Note:** After enabling Seline website analytics, Blowfish will automatically support [Seline event tracking](https://seline.so/docs/custom-events). If you don't want to support this feature, you need to set the parameter `enableTrackEvent` to `false`.
{{< /alert >}}

```toml
# config/_default/params.toml

[selineAnalytics]
  token = "XXXXXX"
  enableTrackEvent = true
```

### Custom Site Analytics

If you want to provide other site analytics on your website, you can provide your own script and override the built-in partial in the Blowfish theme.
Simply create a `layouts/partials/extend-head.html` file and provide the script in the content. The Blowfish theme will automatically add the content from `extend-head.html` to the `<head>` of the entire site.

## Comments

Blowfish supports adding a comment feature at the bottom of each article. Simply provide a `layouts/partials/comments.html` file and add the code to display comments in it.

You can use Hugo's built-in Disqus template or provide custom code. For more content and details, refer to the [Hugo documentation](https://gohugo.io/content-management/comments/).

Once you provide the comments partial, you can use `showComments` to control the visibility of comments more precisely. This parameter can be set globally in the `params.toml` [configuration file]({{< ref "docs/configuration#theme-parameters" >}}) or individually for specific articles in each article's [front matter]({{< ref "docs/front-matter" >}}). This parameter defaults to `false`, so it needs to be set to `true` in either of the above two locations to display comments.

## Favicons

Blowfish provides a set of blank favicons for quick setup, but you can provide your own resources to override them. The easiest way to get new favicon resources is to use a third-party provider like [favicon.io](https://favicon.io).

Favicon resources are located in the `static/` folder and must be named according to the following naming convention. If you use [favicon.io](https://favicon.io), the downloaded file names will match the example below exactly; you can also provide them through other means, just remember to rename them.

```shell
static/
├─ android-chrome-192x192.png
├─ android-chrome-512x512.png
├─ apple-touch-icon.png
├─ favicon-16x16.png
├─ favicon-32x32.png
├─ favicon.ico
└─ site.webmanifest
```

Alternatively, you can completely override the default favicon behavior by providing your own favicon HTML tags and resources. Simply provide a `layouts/partials/favicons.html` file in your project, which will be included in the site's `<head>` and replace the default resources.

## Icons

Similar to the [icon shortcode]({{< ref "docs/shortcodes#icon" >}}), you can also include icons in your own templates and partials by using Blowfish's `icon.html` partial. This partial takes one parameter, which is the name of the icon to include.

**Example:**

```go
  {{ partial "icon.html" "github" }}
```

Icons are populated using Hugo pipelines, making them very flexible. Blowfish comes with a large number of built-in icons for social, linking, and other purposes. Check the [Icons Examples]({{< ref "samples/icons" >}}) page to see the complete list of supported icons.

Custom icons can be added by providing your own icon resources in the project's `assets/icons/` directory. Icons can then be referenced in partials by using the SVG filename (without the `.svg` extension).

Icons can also be used in article content by calling the [icon shortcode]({{< ref "docs/shortcodes#icon" >}}).

## Extensions

Blowfish also provides many extension partials that can extend basic functionality.

### Article Links

If you want to insert additional code after article links, create a `layouts/partials/extend-article-link.html` file. This feature is particularly powerful when combined with the [`badge`]({{< ref "docs/shortcodes#badge" >}}) shortcode to highlight metadata for certain articles.

### Head and Footer

This theme allows direct insertion of additional code into the `<head>` and `<footer>` sections of templates. This code can be used to provide scripts or other logic that don't belong to the theme.

Simply create `layouts/partials/extend-head.html` or `layouts/partials/extend-footer.html`, and these partials will be automatically included in the site build. Both partials will be injected as the last item in `<head>` and `<footer>`, so they can be used to override theme defaults.

### Non-cached Head Extension

`extend-head.html` is [cached](https://gohugo.io/functions/partials/includecached/), and Blowfish also supports a non-cached head extension method for **conditionally** inserting scripts or metadata based on page properties. To use this feature, create a `layouts/partials/extend-head-uncached.html` file in your project, which will be inserted into the `<head>` tag.

This feature is suitable for dynamically adding scripts or metadata based on shortcodes, front matter tags, or other page-specific data, avoiding content being cached at build time.

For example, you can use the [HasShortcode](https://gohugo.io/methods/page/hasshortcode/#article) method in `extend-head-uncached.html` to dynamically load CDN JavaScript files based on whether a shortcode exists.