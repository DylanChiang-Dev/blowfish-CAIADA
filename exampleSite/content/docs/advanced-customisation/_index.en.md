---
title: "Advanced Customisation"
weight: 13
draft: false
description: "Learn how to manually build and customize Blowfish."
slug: "advanced-customisation"
tags: ["advanced", "CSS", "docs"]
series: ["Deployment Tutorial"]
series_order: 13
---

You can customize Blowfish in many advanced ways. Read below to learn more about what can be customized and the best way to achieve the desired results.

If you need more guidance, please ask questions on [GitHub Discussions](https://github.com/nunocoracao/blowfish/discussions).

## Hugo Project Structure

Before we start discussing customization, let's briefly cover the [Hugo project structure](https://gohugo.io/getting-started/directory-structure/) and the best way to manage content and theme customization.

{{< alert >}}
**Summary:** Never edit theme files directly. Always make customizations only in subdirectories of your Hugo project, not in the theme directory.
{{< /alert >}}

Blowfish is designed to take advantage of all standard Hugo parameter operations. It's designed to allow customization and override of all aspects of the theme without changing any core theme files. This also provides you with a seamless upgrade experience while giving you complete control over the look and feel of your website.

To achieve this, you should never manually change any theme core files directly. Whether you install using Hugo modules, as a git submodule, or manually install the theme in the `themes/` directory, you should always keep these theme files unchanged.

The correct way to adjust theme behavior is by overriding files using Hugo's powerful [file lookup order](https://gohugo.io/templates/lookup-order/). In summary, the lookup order ensures that files contained in your project directory take precedence over theme files.

For example, if you want to override the main article template in Blowfish, you can create your own `layouts/_default/single.html` file and place it in the root directory of your project. This file will then override the `single.html` in the theme files without making any changes to the theme files themselves. This applies to any theme file: HTML templates, partials, shortcodes, config files, data, assets, etc.

As long as you follow this approach, you will always be able to seamlessly update the theme (or test different theme versions) without worrying about losing any custom changes.

## Modifying Image Optimization Settings

Hugo has various built-in methods to resize, crop, and optimize images.

For example, if in `layouts/partials/article-link/card.html`, you have the following code:

```go
{{ with .Resize "600x" }}
<div class="w-full thumbnail_card nozoom" style="background-image:url({{ .RelPermalink }});"></div>
{{ end }}
```

Hugo will default to resizing the image to 600px while maintaining the aspect ratio.

It's worth noting that default image settings like [anchor](https://gohugo.io/content-management/image-processing/#anchor) can also be modified in your [site configuration](https://gohugo.io/content-management/image-processing/#processing-options), just like modifying templates.

For more information, please refer to the [Hugo documentation on image processing](https://gohugo.io/content-management/image-processing/#image-processing-methods).

## CSS Customization

Blowfish uses Tailwind CSS for styling. You can customize the appearance by:

1. **Override CSS Variables**: Create custom CSS files in your project's `assets/css/` directory
2. **Custom Tailwind Configuration**: Modify Tailwind settings through configuration files
3. **Additional Stylesheets**: Add your own CSS files to extend or override existing styles

## Layout Customization

You can customize layouts by creating files in your project's `layouts/` directory:

- **Page Templates**: Override `layouts/_default/single.html` for individual pages
- **List Templates**: Override `layouts/_default/list.html` for listing pages
- **Partial Templates**: Create custom partials in `layouts/partials/`
- **Shortcodes**: Add custom shortcodes in `layouts/shortcodes/`

## Configuration Customization

Advanced configuration options include:

- **Theme Parameters**: Modify `config/_default/params.toml`
- **Menu Configuration**: Customize navigation in `config/_default/menus.toml`
- **Language Settings**: Configure multilingual support
- **SEO Settings**: Optimize search engine visibility

## Best Practices

1. **Always use the file lookup order** - Never modify theme files directly
2. **Test changes locally** - Use `hugo server` to preview modifications
3. **Version control** - Keep your customizations in version control
4. **Document changes** - Maintain notes about your customizations
5. **Stay updated** - Regularly update the theme while preserving customizations

## Getting Help

If you encounter issues with customization:

- Check the [official documentation]({{< ref "docs" >}})
- Search [GitHub Issues](https://github.com/nunocoracao/blowfish/issues)
- Ask questions on [GitHub Discussions](https://github.com/nunocoracao/blowfish/discussions)
- Review the [configuration guide]({{< ref "docs/configuration" >}})