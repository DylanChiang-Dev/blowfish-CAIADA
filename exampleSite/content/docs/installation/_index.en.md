---
title: "Installation"
description: "How to install and set up Blowfish theme for Hugo."
date: 2024-01-01
draft: false
slug: "installation"
tags: ["installation", "setup", "guide"]
series: ["Documentation"]
series_order: 2
showEdit: true
showSummary: true
---

{{< lead >}}
Learn how to install and set up Blowfish theme for your Hugo website.
{{< /lead >}}

## Prerequisites

Before installing Blowfish, make sure you have:

- Hugo Extended version 0.87.0 or later
- Git (for theme installation)
- A text editor

## Installation Methods

### Method 1: Hugo Modules (Recommended)

1. Initialize your Hugo site as a module:
   ```bash
   hugo mod init github.com/username/my-website
   ```

2. Add Blowfish to your `hugo.toml`:
   ```toml
   [module]
     [[module.imports]]
       path = "github.com/nunocoracao/blowfish"
   ```

### Method 2: Git Submodule

1. Add Blowfish as a submodule:
   ```bash
   git submodule add -b main https://github.com/nunocoracao/blowfish.git themes/blowfish
   ```

2. Add the theme to your `hugo.toml`:
   ```toml
   theme = "blowfish"
   ```

## Configuration

After installation, copy the configuration files from the theme to your site:

```bash
cp -r themes/blowfish/config/_default/* config/_default/
```

## Next Steps

Once installed, you can:

1. [Configure your site]({{< ref "docs/configuration" >}})
2. [Create your first content]({{< ref "docs/getting-started" >}})
3. [Customize the theme]({{< ref "docs/advanced-customisation" >}})