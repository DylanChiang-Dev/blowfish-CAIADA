---
title: "Getting Started"
weight: 3
draft: false
description: "All the preparation work before you start building your website with the Blowfish theme"
slug: "getting-started"
tags: ["installation", "docs"]
series: ["Deployment Tutorial"]
series_order: 3
---

{{< alert >}}
This section assumes you have already read [Installing Blowfish Theme]({{< ref "docs/installation" >}}).
{{< /alert >}}

</br>
{{< alert "fire" >}}
We've just released a CLI tool to help you get started with Blowfish quickly. It will help you install and configure the Blowfish theme. You can install the CLI tool globally using the following command:
```bash
npx blowfish-tools
```
{{< /alert >}}

The configuration files in Blowfish contain all possible setting options that the theme needs. However, by default, most settings are commented out, and you only need to uncomment them to activate or modify the setting options.

## Basic Setup

After installation and before creating content, there are several settings that need attention. Starting with `hugo.toml`, set the `baseURL` and `languageCode` parameters. The `languageCode` parameter is used to specify the primary language for your content creation.

```toml
# config/_default/hugo.toml

baseURL = "https://your_domain.com/"
languageCode = "en"
```

The next step is to set up the language. Although Blowfish supports multiple languages, `hugo.toml` can only configure one primary language.

Find `languages.en.toml` in the `config/_default` folder. If your primary language is English, you can use this file directly. Otherwise, you need to rename it to the corresponding filename for your primary language. For example, if the primary language is French, you need to name the file `languages.fr.toml`.

{{< alert >}}
Note: The language code in the language configuration filename must match the `languageCode` in `hugo.toml`.
{{< /alert >}}

```toml
# config/_default/languages.en.toml

title = "My awesome website"
```

## Site Configuration

After setting up the basic language configuration, you'll need to configure your site's basic information:

### Site Title and Description

Set your site's title and description in the language configuration file:

```toml
# config/_default/languages.en.toml

title = "My Website"
description = "A brief description of your website"
```

### Author Information

Configure author information for your site:

```toml
# config/_default/languages.en.toml

[author]
  name = "Your Name"
  image = "img/author.jpg"
  headline = "Your headline or tagline"
  bio = "A brief bio about yourself"
  links = [
    { email = "mailto:hello@your_domain.com" },
    { github = "https://github.com/username" },
    { twitter = "https://twitter.com/username" }
  ]
```

## Menu Configuration

Configure your site's navigation menus by editing the menu configuration file:

```toml
# config/_default/menus.en.toml

[[main]]
  name = "Blog"
  pageRef = "posts"
  weight = 10

[[main]]
  name = "About"
  pageRef = "about"
  weight = 20

[[main]]
  name = "Contact"
  pageRef = "contact"
  weight = 30
```

## Theme Parameters

Customize the theme's appearance and behavior through the parameters configuration:

```toml
# config/_default/params.toml

colorScheme = "blowfish"
defaultAppearance = "light"
autoSwitchAppearance = true

[homepage]
  layout = "page"
  homepageImage = "img/homepage.jpg"
  showRecent = true
  showRecentItems = 5
```

## Creating Content

Once your basic configuration is complete, you can start creating content:

### Creating Your First Post

```bash
hugo new posts/my-first-post.md
```

### Creating Pages

```bash
hugo new about.md
hugo new contact.md
```

## Testing Your Site

Run the Hugo development server to test your site:

```bash
hugo server
```

Your site will be available at `http://localhost:1313`.

## Next Steps

- Explore [Configuration]({{< ref "docs/configuration" >}}) for advanced settings
- Learn about [Front Matter]({{< ref "docs/front-matter" >}}) for content customization
- Check out [Shortcodes]({{< ref "docs/shortcodes" >}}) for enhanced content features
- Review [Advanced Customisation]({{< ref "docs/advanced-customisation" >}}) options for theme personalization