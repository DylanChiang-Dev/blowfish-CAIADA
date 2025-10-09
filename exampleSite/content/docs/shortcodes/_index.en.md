---
title: "Shortcodes"
weight: 6
draft: false
description: "All available shortcodes in Blowfish"
slug: "shortcodes"
tags: ["shortcodes", "mermaid", "icons", "lead", "docs"]
series: ["Deployment Tutorial"]
series_order: 8
---

In addition to all the [default Hugo shortcodes](https://gohugo.io/content-management/shortcodes/), Blowfish adds several additional features.

## Alert

The `alert` shortcode outputs its content as a stylized message box within your article. It's useful for drawing attention to important information that you don't want readers to miss.

<!-- prettier-ignore-start -->
| Parameter   | Function                                                                                                                         |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `icon`      | **Optional** Icon to display on the left side.<br>**Default:** `exclamation triangle icon` (See [Icon shortcode](#icon) for more details on using icons.) |
| `iconColor` | **Optional** Icon color in basic CSS style.<br>Can be a hex value (`#FFFFFF`) or color name (`white`)<br>Determined by current color scheme by default. |
| `cardColor` | **Optional** Card background color in basic CSS style.<br>Can be a hex value (`#FFFFFF`) or color name (`white`)<br>Determined by current color scheme by default. |
| `textColor` | **Optional** Text color in basic CSS style.<br>Can be a hex value (`#FFFFFF`) or color name (`white`)<br>Determined by current color scheme by default. |
<!-- prettier-ignore-end -->

The input content is written in Markdown, so you can format it as needed.

**Example 1:** No parameters

```md
{{</* alert */>}}
**Warning!** This action is destructive!
{{</* /alert */>}}
```

{{< alert >}}
**Warning!** This action is destructive!
{{< /alert >}}

**Example 2:** Unnamed parameter

```md
{{</* alert "twitter" */>}}
Don't forget to [follow me](https://twitter.com/nunocoracao) on Twitter.
{{</* /alert */>}}
```

{{< alert "twitter" >}}
Don't forget to [follow me](https://twitter.com/nunocoracao) on Twitter.
{{< /alert >}}

**Example 3:** Named parameters

```md
{{</* alert icon="fire" cardColor="#e63946" iconColor="#1d3557" textColor="#f1faee" */>}}
This is an error!
{{</* /alert */>}}
```

{{< alert icon="fire" cardColor="#e63946" iconColor="#1d3557" textColor="#f1faee" >}}
This is an error!
{{< /alert >}}

## Article

The `Article` shortcode embeds an article into a markdown file. The `link` parameter should be the `.RelPermalink` of the file to be embedded. Note that if the shortcode references its parent file, it will not display anything. *Note: If you're running your site in a subfolder like Blowfish (i.e., /blowfish/), include that path in the link.*

<!-- prettier-ignore-start -->
| Parameter   | Function                                  |
| ----------- | ----------------------------------------- |
| `link`      | **Required** `.RelPermalink` of the article to embed |
| `showSummary` | **Optional** Boolean indicating whether to show article summary. If not set, site's default configuration will be used. |
| `compactSummary` | **Optional** Boolean indicating whether to show summary in compact mode. Defaults to false. |
<!-- prettier-ignore-end -->

**Example:**

```md
{{</* article link="/posts/welcome-to-blowfish/" */>}}
```

## Badge

The `badge` shortcode can be used to display small badges and labels within your content.

**Example:**

```md
{{</* badge */>}}
New article!
{{</* /badge */>}}
```

{{< badge >}}
New article!
{{< /badge >}}

## Button

The `button` shortcode generates a styled button that can link to other pages or external URLs.

<!-- prettier-ignore-start -->
| Parameter | Function                                    |
| --------- | ------------------------------------------- |
| `href`    | **Required** URL or path to link to        |
| `target`  | **Optional** Link target (e.g., `_blank`)  |
<!-- prettier-ignore-end -->

**Example:**

```md
{{</* button href="https://github.com/nunocoracao/blowfish" target="_blank" */>}}
Download Blowfish
{{</* /button */>}}
```

{{< button href="https://github.com/nunocoracao/blowfish" target="_blank" >}}
Download Blowfish
{{< /button >}}

## Chart

The `chart` shortcode uses Chart.js library to embed charts into articles using simple structured data.

**Example:**

```md
{{</* chart */>}}
type: 'bar',
data: {
  labels: ['Tomatoes', 'Blueberries', 'Bananas', 'Cherries', 'Apples', 'Grapes', 'Oranges'],
  datasets: [{
    label: '# of votes',
    data: [12, 19, 3, 5, 3, 8, 1],
  }]
}
{{</* /chart */>}}
```

## Figure

The `figure` shortcode replaces the default Hugo `figure` shortcode and provides additional functionality for displaying images with captions.

<!-- prettier-ignore-start -->
| Parameter | Function                                    |
| --------- | ------------------------------------------- |
| `src`     | **Required** Image source URL or path      |
| `alt`     | **Optional** Alternative text for the image |
| `caption` | **Optional** Image caption                  |
| `class`   | **Optional** CSS class for styling         |
| `href`    | **Optional** Link URL for the image        |
| `default` | **Optional** Use default Hugo figure behavior |
<!-- prettier-ignore-end -->

**Example:**

```md
{{</* figure src="image.jpg" alt="Description" caption="Image caption" */>}}
```

## Gallery

The `gallery` shortcode creates an image gallery from a directory of images.

**Example:**

```md
{{</* gallery */>}}
<img src="gallery/01.jpg" class="grid-w33" />
<img src="gallery/02.jpg" class="grid-w33" />
<img src="gallery/03.jpg" class="grid-w33" />
{{</* /gallery */>}}
```

## Icon

The `icon` shortcode displays icons from various icon libraries.

<!-- prettier-ignore-start -->
| Parameter | Function                                    |
| --------- | ------------------------------------------- |
| Icon name | **Required** Name of the icon to display   |
<!-- prettier-ignore-end -->

**Example:**

```md
{{</* icon "github" */>}}
```

{{< icon "github" >}}

## Katex

The `katex` shortcode renders mathematical expressions using KaTeX.

**Example:**

```md
{{</* katex */>}}
\\(f(a,b,c) = (a^2+b^2+c^2)^3\\)
{{</* /katex */>}}
```

## Lead

The `lead` shortcode creates a lead paragraph that stands out from regular text.

**Example:**

```md
{{</* lead */>}}
This is a lead paragraph that introduces the main content.
{{</* /lead */>}}
```

{{< lead >}}
This is a lead paragraph that introduces the main content.
{{< /lead >}}

## Mermaid

The `mermaid` shortcode allows you to draw detailed diagrams and flowcharts using Mermaid syntax.

**Example:**

```md
{{</* mermaid */>}}
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
{{</* /mermaid */>}}
```

## TypeIt

The `typeit` shortcode uses the TypeIt library to create typewriter-style animations.

**Example:**

```md
{{</* typeit */>}}
This text will be typed out character by character.
{{</* /typeit */>}}
```

## Best Practices

1. **Use alerts sparingly** - Too many alerts can overwhelm readers
2. **Choose appropriate icons** - Icons should be relevant to the content
3. **Test shortcodes** - Always preview your content to ensure shortcodes render correctly
4. **Keep it simple** - Don't overuse shortcodes in a single article
5. **Consider accessibility** - Ensure your shortcodes work well with screen readers

For more information about Hugo shortcodes, see the [Hugo documentation](https://gohugo.io/content-management/shortcodes/).