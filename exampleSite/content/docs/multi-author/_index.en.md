---
title: "Multi-Author Mode"
weight: 8
draft: false
description: "Set up multiple authors for your articles."
slug: "multi-author"
tags: ["authors", "configuration", "docs"]
series: ["Deployment Tutorial"]
series_order: 10
showAuthor: true
authors:
  - "nunocoracao"
showAuthorsBadges: false 
---

A website may have multiple authors contributing content, so there's a need to use multiple authors by default across the entire site. For this scenario, Blowfish allows users to extend the author list using the multi-author feature.

To maintain backward compatibility, this feature only allows defining additional authors and does not modify previously added authors through configuration files in any way.

## Creating New Authors

The first step in creating new authors is to set up a `./data/authors` folder. Then, you can simply add new author `json` files inside it. The file name is the `key` you need to specify when referencing that author in articles.

For example, create a `nunocoracao.json` file in the `./data/authors` folder. The file content example is as follows. `name`, `image`, `bio`, and `social` are the 4 parameters currently supported by author files, similar to the default author configuration in your `languages.[language-code].toml` configuration file.

_Note: The `key` in social parameters will automatically get the theme's icon, though you can also set any icon in the `assets/icons` folder._

```json
{
    "name": "Nuno Coração",
    "image" : "img/nuno_avatar.jpg",
    "bio": "Theme Creator",
    "social": [
        { "linkedin": "https://linkedin.com/in/nunocoracao" },
        { "twitter": "https://twitter.com/nunocoracao" },
        { "instagram": "https://instagram.com/nunocoracao" },
        { "medium": "https://medium.com/@nunocoracao" },
        { "github": "https://github.com/nunocoracao" },
        { "goodreads": "http://goodreads.com/nunocoracao" },
        { "keybase": "https://keybase.io/nunocoracao" },
        { "reddit": "https://reddit.com/user/nunoheart" }
    ]
}
```

## Referencing Authors in Articles

Now that you've created new authors, the next step is to reference them in articles. In the example below, we use the author `key` created earlier to reference it.

Blowfish will use the data from the additional author's corresponding `json` file to help render this author in the article. This feature does not change the default author of the entire site configuration, so you can control them separately. Using the `showAuthor` parameter, you can configure whether to display the default author, which is suitable for single-author blogs. The `authors` parameter in the front matter allows you to define additional authors for articles, and these authors will be independent of the default author across the entire site.

```md
---
title: "Multi-Author"
date: 2020-08-10
draft: false
description: "Set up multiple authors for your articles."
slug: "multi-author"
tags: ["authors", "config", "docs"]
showAuthor: true
authors:
  - "nunocoracao"
showAuthorsBadges: false 
---
```

The example above, like this current page, will display both the default author and the new author. You can scroll through this page to see the actual effect.

## Creating Author Taxonomy

If you want to get lists of articles for each of your authors, you can configure the `authors` taxonomy, which opens up some more interesting configurations. This is an optional step in the multi-author mode process.

The first step is to configure the `authors` taxonomy in the `config.toml` file as shown below. Although `tag` and `category` are defined by Hugo by default, once you add a specific taxonomy, you need to explicitly add `tag` and `category`, otherwise based on Hugo's file loading order, the site will not process `tag` and `category`.

```toml
[taxonomies]
  tag = "tags"
  category = "categories"
  author = "authors"
```

This way, you'll have a page with a list of all authors, and each author will display a list of articles they've contributed to. If you want to display authors as badges in each article, there are two ways: add the `article.showAuthorsBadges` parameter in the global configuration file or configure the `showAuthorsBadges` parameter in each article's front matter.

Finally, you can add more detailed content to each author page to display bios, links, or any other information that suits your needs. To achieve this, you need to add a folder named with the author's `key` in the `./content/authors` folder and add an `_index.md` file in that folder. For the example above, we would get a `./content/authors/nunocoracao/_index.md` file. In this file, you can add the author's actual name and their personal information page. The authors in this documentation site are configured this way, and you can see the actual effect in the documentation site.

```md
---
title: "Nuno Coração"
---

Nuno's awesome dummy bio.
```

## Example

The example below demonstrates how to disable the site's default author and add multiple authors to articles.

{{< article link="/samples/multiple-authors/" >}}