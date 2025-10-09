---
title: "Front Matter"
weight: 7
draft: false
description: "Learn about all the Front Matter parameters available in Blowfish for customizing individual pages."
slug: "front-matter"
tags: ["front matter", "configuration", "docs"]
series: ["Deployment Tutorial"]
series_order: 7
---

In addition to the [default front matter in Hugo](https://gohugo.io/content-management/front-matter/#front-matter-variables), Blowfish adds a large number of parameter options to customize how individual pages are displayed. All available front matter parameters are listed below.

The default values for front matter parameters are inherited from the [basic configuration]({{< ref "docs/configuration" >}}), so you only need to specify these parameters on the current page when you want to override the default values.

<!-- prettier-ignore-start -->
| Name                          | Default Value                                                                                                   | Description                                                                                                                                                                                  |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `title`                       | None                                                                                                            | Article title.                                                                                                                                                                               |
| `description`                 | None                                                                                                            | Article description, which will be added to the HTML `<meta>` metadata.                                                                                                                     |
| `externalUrl`                 | None                                                                                                            | If the article is published on a third-party website, provide the URL pointing to the corresponding article. Providing a URL will prevent generating a content page, and any reference to this article will redirect directly to the third-party website URL. |
| `editURL`                     | `article.editURL`                                                                                               | When the `showEdit` parameter is activated, this parameter is used to set the URL for editing the article.                                                                                  |
| `editAppendPath`              | `article.editAppendPath`                                                                                        | When the `showEdit` parameter is activated, this parameter specifies whether to append the current article path to the URL set by `editURL`.                                               |
| `groupByYear`                 | `list.groupByYear`                                                                                              | Whether to group articles by year on list pages.                                                                                                                                            |
| `menu`                        | None                                                                                                            | When this value is set, a link to this content will appear in the menu. Valid values are `main` or `footer`.                                                                               |
| `robots`                      | None                                                                                                            | How search engine crawlers should handle this article. If this value is set, it will be output in the page header. For more information, see [Google documentation](https://developers.google.com/search/docs/advanced/robots/robots_meta_tag#directives). |
| `sharingLinks`                | `article.sharingLinks`                                                                                          | Specifies which sharing links to display at the end of the article. If not set or set to `false`, no sharing links will be displayed.                                                      |
| `showAuthor`                  | `article.showAuthor`                                                                                            | Whether to display the author box in the footer.                                                                                                                                            |
| `showAuthorBottom`            | `article.showAuthorBottom`                                                                                      | Display the author box at the bottom of each page instead of the top.                                                                                                                       |
| `authors`                     | None                                                                                                            | Array for displaying multiple authors. If set, it will override the `showAuthor` setting. This uses the multi-author feature. See [this page]({{< ref "multi-author" >}}) for more information. |
| `showAuthorsBadges`           | `article.showAuthorsBadges`                                                                                     | Whether to display `authors` author categories on article and list pages. For this to work, you need to enable `multiple authors` and `authors` categories. See [this page]({{< ref "multi-author" >}}) for more information. |
| `featureimage`                | None                                                                                                            | Feature image link based on external URL.                                                                                                                                                   |
| `featureimagecaption`         | None                                                                                                            | Feature image caption, only displayed in the `big` style of hero layout.                                                                                                                    |
| `showHero`                    | `article.showHero`                                                                                              | Whether to display the featured image as a hero image within the article page.                                                                                                              |
| `heroStyle`                   | `article.heroStyle`                                                                                             | Hero image style. Valid values are: `basic`, `big`, `background`, `thumbAndBackground`.                                                                                                     |
| `showBreadcrumbs`             | `article.showBreadcrumbs` or `list.showBreadcrumbs`                                                             | Whether to display breadcrumb navigation on article or list pages.                                                                                                                          |
| `showDate`                    | `article.showDate`                                                                                              | Whether to display the article date. The specific date is set using the `date` parameter.                                                                                                   |
| `showDateUpdated`             | `article.showDateUpdated`                                                                                       | Whether to display the article update date. The specific date is set using the `lastmod` parameter.                                                                                         |
| `showEdit`                    | `article.showEdit`                                                                                              | Whether to display a link to edit the article content.                                                                                                                                      |
| `showHeadingAnchors`          | `article.showHeadingAnchors`                                                                                    | Whether to display anchor links next to article headings.                                                                                                                                   |
| `showPagination`              | `article.showPagination`                                                                                        | Whether to display next/previous links in the article footer.                                                                                                                               |
| `invertPagination`            | `article.invertPagination`                                                                                      | Whether to invert the direction of next/previous links.                                                                                                                                      |
| `showReadingTime`             | `article.showReadingTime`                                                                                       | Whether to display the estimated reading time for the article.                                                                                                                              |
| `showTaxonomies`              | `article.showTaxonomies`                                                                                        | Whether to display categories/tags associated with the article.                                                                                                                              |
| `showTableOfContents`         | `article.showTableOfContents`                                                                                   | Whether to display the article table of contents.                                                                                                                                           |
| `showWordCount`               | `article.showWordCount`                                                                                         | Whether to display article word count. If your language belongs to CJK languages, you need to enable the `hasCJKLanguage` parameter in `config.toml`.                                     |
| `showComments`                | `article.showComments`                                                                                          | Whether to display the [comments section]({{< ref "docs/partials#comments" >}}) in the article footer.                                                                                          |
| `showSummary`                 | `list.showSummary`                                                                                              | Whether to display summaries on article or list pages.                                                                                                                                      |
| `showViews`                   | `article.showViews`                                                                                             | Whether to display view counts on article and list pages. This requires Firebase integration. See [this page]({{< ref "docs/firebase-views" >}}) to learn how to integrate Firebase in Blowfish. |
| `showLikes`                   | `article.showLikes`                                                                                             | Whether to display like counts on article and list pages. This requires Firebase integration. See [this page]({{< ref "docs/firebase-views" >}}) to learn how to integrate Firebase in Blowfish. |
<!-- prettier-ignore-end -->

## Usage Examples

### Basic Article Configuration

```yaml
---
title: "My First Post"
description: "This is my first blog post using Blowfish theme"
date: 2024-01-01
draft: false
tags: ["blog", "hugo", "blowfish"]
showTableOfContents: true
showReadingTime: true
showWordCount: true
---
```

### Hero Image Configuration

```yaml
---
title: "Featured Article"
showHero: true
heroStyle: "big"
featureimage: "https://example.com/hero-image.jpg"
featureimagecaption: "Beautiful landscape photo"
---
```

### Multi-Author Configuration

```yaml
---
title: "Collaborative Post"
authors: ["john-doe", "jane-smith"]
showAuthorsBadges: true
showAuthorBottom: true
---
```

### External Article Configuration

```yaml
---
title: "Article on Medium"
externalUrl: "https://medium.com/@author/article-title"
description: "This article was originally published on Medium"
---
```

## Best Practices

1. **Use descriptive titles and descriptions** for better SEO
2. **Set appropriate tags and categories** to organize content
3. **Configure hero images** for featured articles
4. **Enable table of contents** for long articles
5. **Use external URLs** for cross-posted content
6. **Test different hero styles** to find what works best for your content

For more information about configuring your site, see the [Configuration]({{< ref "docs/configuration" >}}) documentation.