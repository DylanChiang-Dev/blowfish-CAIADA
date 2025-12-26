# Blowfish 开发指南

> 本文档整合了 CAIADA 协会网站开发所需的所有 Blowfish 主题参考资料。

## 项目概述

基于 Hugo Blowfish 主题的中华AI应用发展协会（CAIADA）官方网站。

**技术栈**: Hugo 0.150+ | Blowfish 主题 | Tailwind CSS 4.x | Fuse.js 搜索

---

## 开发命令

```bash
# 安装依赖
npm install

# 构建 CSS（生产模式）
npm run build

# 启动开发服务器（推荐）
npm run example

# CSS 热更新监控
npm run dev

# 快速测试模式
npm run example:core
```

**本地预览**: http://localhost:1313

---

## 项目架构

```
blowfish-CAIADA/
├── .agent/                    # AI 开发参考文档
├── assets/                    # 主题资源 (CSS, JS, Icons)
├── config/                    # 主题默认配置
├── exampleSite/               # 网站内容
│   ├── config/_default/       # 站点配置
│   │   ├── hugo.toml          # Hugo 主配置
│   │   ├── params.toml        # 主题参数
│   │   ├── languages.*.toml   # 语言配置
│   │   └── menus.*.toml       # 菜单配置
│   └── content/               # 内容文件
│       ├── _index.*.md        # 首页
│       ├── about/             # 关于协会
│       └── news/              # 协会新闻
├── i18n/                      # 翻译文件
├── layouts/                   # Hugo 模板
│   ├── _default/              # 默认模板
│   ├── partials/              # 组件
│   └── shortcodes/            # 简码
└── tailwind.config.js         # Tailwind 配置
```

---

## 配置参考

### hugo.toml 关键参数

| 参数 | 说明 |
|------|------|
| `defaultContentLanguage` | 默认语言代码，如 `zh-tw` |
| `hasCJKLanguage` | 启用中日韩文字支持 |
| `enableRobotsTXT` | 生成 robots.txt |
| `pagination.pagerSize` | 每页文章数量 |

### params.toml 主题参数

| 参数 | 说明 |
|------|------|
| `colorScheme` | 色彩主题：blowfish, ocean, forest 等 |
| `defaultAppearance` | 默认外观：light / dark |
| `enableSearch` | 启用全站搜索 |
| `mainSections` | 首页显示的内容区域 |
| `homepage.layout` | 首页布局：profile, page, hero, card, background, custom |
| `homepage.showRecent` | 显示最近文章 |
| `article.showTableOfContents` | 显示目录 |
| `article.showReadingTime` | 显示阅读时间 |

### 语言配置 (languages.*.toml)

```toml
[languages.zh-tw]
  weight = 1
  languageCode = "zh-tw"
  languageName = "繁體中文"

[params]
  displayName = "繁體中文"
  dateFormat = "2006年1月2日"

[params.author]
  name = "中華AI應用發展協會"
```

### 菜单配置 (menus.*.toml)

```toml
[[main]]
  name = "首頁"
  pageRef = "/"
  weight = 10

[[footer]]
  name = "關於我們"
  pageRef = "/about/"
  weight = 10
```

---

## 常用 Shortcodes

### Alert 警告框
```md
{{< alert >}}
**警告！**此操作具有破坏性！
{{< /alert >}}

{{< alert icon="fire" cardColor="#e63946" >}}
自定义颜色和图标
{{< /alert >}}
```

### Badge 徽章
```md
{{< badge >}}New!{{< /badge >}}
```

### Button 按钮
```md
{{< button href="/about/" >}}了解更多{{< /button >}}
```

### List 文章列表
```md
{{< list limit=5 cardView=true >}}
{{< list where="Section" value="news" limit=10 >}}
```

### Figure 图片
```md
{{< figure src="image.jpg" alt="描述" caption="标题" >}}
```

### Mermaid 图表
```md
{{< mermaid >}}
graph LR;
A[开始]-->B[结束]
{{< /mermaid >}}
```

### Chart 图表
```md
{{< chart >}}
type: 'bar',
data: {
  labels: ['A', 'B', 'C'],
  datasets: [{ data: [10, 20, 30] }]
}
{{< /chart >}}
```

### GitHub 卡片
```md
{{< github repo="nunocoracao/blowfish" >}}
```

### Timeline 时间线
```md
{{< timeline >}}
{{< timelineItem icon="star" header="里程碑" badge="2024" >}}
内容描述
{{< /timelineItem >}}
{{< /timeline >}}
```

### Gallery 图库
```md
{{< gallery >}}
<img src="01.jpg" class="grid-w33" />
<img src="02.jpg" class="grid-w33" />
{{< /gallery >}}
```

---

## 首页布局选项

| 布局 | 说明 |
|------|------|
| `profile` | 作者资料居中，适合个人博客 |
| `page` | 纯 Markdown 内容，灵活性最高 |
| `hero` | 大图背景 + 作者信息 |
| `card` | 卡片式展示 + 图片 |
| `background` | 背景图平滑过渡 |
| `custom` | 完全自定义，需创建 `layouts/partials/home/custom.html` |

设置方法: `params.toml` 中的 `homepage.layout`

---

## Front Matter 参数

```yaml
---
title: "文章标题"
description: "SEO 描述"
date: 2024-01-01
draft: false
tags: ["标签1", "标签2"]
categories: ["分类"]
showTableOfContents: true
showReadingTime: true
showAuthor: true
showHero: true
heroStyle: "big"  # basic, big, background, thumbAndBackground
---
```

| 参数 | 说明 |
|------|------|
| `externalUrl` | 外部链接（跳转到第三方网站） |
| `showBreadcrumbs` | 显示面包屑导航 |
| `showPagination` | 显示上/下一篇链接 |
| `showComments` | 显示评论区 |
| `build.list` | 设为 `never` 可隐藏于列表 |

---

## 内容管理

### 多语言文件命名

```
_index.zh-tw.md   # 繁体中文
_index.zh-cn.md   # 简体中文
_index.en.md      # 英文
_index.vi.md      # 越南文
```

### 协会页面路径

| 页面 | 路径 |
|------|------|
| 首页 | `content/_index.zh-tw.md` |
| 关于 | `content/about/_index.zh-tw.md` |
| 章程 | `content/about/charter.zh-tw.md` |
| 新闻 | `content/news/_index.zh-tw.md` |

---

## 部署指南 (Cloudflare Pages)

### 构建配置

| 设置 | 值 |
|------|-----|
| 构建命令 | `hugo --minify --gc` |
| 输出目录 | `public` |
| 根目录 | `exampleSite` |

### 环境变量

```
HUGO_VERSION=0.150.1
NODE_VERSION=18
```

### 优化建议

- ✅ 启用 Auto Minify (HTML, CSS, JS)
- ✅ 开启 Brotli 压缩
- ✅ 启用 HTTP/3

---

## 常见问题

### Hugo 版本警告

```
WARN Module "blowfish" is not compatible with this Hugo version
```
**说明**: 兼容性声明滞后，功能正常，可忽略。

### Shortcode 错误

```
shortcode 'button' must be closed or self-closed
```
**解决**: 使用 HTML 替代：
```html
<a href="#" class="inline-block !rounded-md bg-primary-600 px-4 py-2 !text-neutral">按钮</a>
```

### 图标显示问题

**解决**: 使用 Emoji 替代 SVG 图标，如 🧠、👥、📚

---

## 开发历史要点

- **v0.1.0**: 繁体中文多语言支持
- **v0.1.1**: 英文版协会内容完善
- **v0.1.2**: 首页 Emoji 图标修复
- **当前**: 默认语言为繁体中文 (zh-tw)
