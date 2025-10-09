---
title: "Configuration"
weight: 4
draft: false
description: "Learn about all the configuration variables available in Blowfish."
slug: "configuration"
tags: ["configuration", "docs"]
series: ["Deployment Tutorial"]
series_order: 4
---

Blowfish is a highly customizable theme that uses some of the latest Hugo features to simplify how it's configured.

The theme ships with a default configuration that gets you up and running with a basic blog or static website.

{{< alert "fire" >}}
We've just released a CLI tool to help you get started with Blowfish quickly. It will help you with installation and configuration. You can install the CLI tool globally using the following command:

```bash
npx blowfish-tools
```

{{< /alert >}}

> Configuration files are based on the TOML format, which is Hugo's default syntax. You can also convert the configuration to YAML or JSON format if you prefer.

By default, all available theme parameters are defined in each file, so you can freely adjust the settings to meet your needs.

{{< alert >}}
As mentioned in the [installation instructions]({{< ref "/docs/installation#set-up-theme-configuration-files" >}}), if you want to adjust the theme configuration, you can modify the files in the `config/_default/` folder of your Hugo project and delete the `config.toml` file in the project root directory.
{{< /alert >}}

## Site Configuration

The Blowfish theme supports all standard configuration variables defined in the Hugo framework. However, for the best experience, some specific configurations need to be set.

Site configuration is managed through the `config/_default/config.toml` file. The table below shows all the settings available in Blowfish.

Note that the variable names provided in the table can use dot notation to simplify the TOML data structure, for example, `outputs.home` refers to `[outputs] home`.

<!-- prettier-ignore-start -->
| Name                     | Default                   | Description                                                                                                                                                                                                                                                                                          |
| ------------------------ | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `theme`                  | `"blowfish"`              | When using Hugo modules for installation, this configuration item should be removed. For Git submodule or local file copy installation methods, it must be set to blowfish to work properly.                                                                                                        |
| `baseURL`                | None                      | The root URL of the website.                                                                                                                                                                                                                                                                         |
| `defaultContentLanguage` | `"en"`                    | This value determines the default language used by theme components and content. Refer to the [Languages and i18n](#languages-and-i18n) section to learn about all language codes supported by Blowfish.                                                                                          |
| `enableRobotsTXT`        | `true`                    | When enabled, a `robots.txt` file will be created in the site root directory, allowing search engines to crawl the entire website. If you want to provide your own `robots.txt`, set this value to `false` and place your file in the `static` directory. For complete control, you may need to provide a [custom layout]({{< ref "content-examples#custom-layouts" >}}) to generate this file. |
| `pagination.pagerSize`   | `10`                      | Defines the number of articles displayed per page in article lists.                                                                                                                                                                                                                                  |
| `summaryLength`          | `0`                       | When no article summary is provided in the [front matter parameters]({{< ref "docs/front-matter" >}}), this parameter defines the number of words for automatically generated article summaries. If the value is `0`, the first sentence is used as the summary by default. This value has no effect when summaries are hidden. |
| `outputs.home`           | `["HTML", "RSS", "JSON"]` | Output formats automatically generated for the site. Blowfish requires HTML, RSS, and JSON to ensure theme components work properly.                                                                                                                                                                 |

## Theme Configuration

Blowfish provides extensive customization options through various configuration files. The main theme configuration is handled through several files in the `config/_default/` directory:

### Languages Configuration

The theme supports multiple languages and can be configured through language-specific files. Each language can have its own configuration, menus, and content.

### Menu Configuration

Navigation menus can be customized through the `menus.toml` file or language-specific menu files like `menus.en.toml`.

### Parameters Configuration

Additional theme parameters can be configured through the `params.toml` file, allowing you to customize colors, fonts, layout options, and more.

## Getting Started

To get started with configuration:

1. Copy the example configuration files from the theme
2. Modify the settings in `config/_default/` to match your needs
3. Test your changes by running `hugo server`
4. Deploy your site when you're satisfied with the configuration

For detailed configuration options and examples, refer to the specific configuration sections in this documentation.