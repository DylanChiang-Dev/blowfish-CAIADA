# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个基于 Blowfish Hugo 主题的中华AI应用发展协会（CAIADA）官方网站项目，为台湾AI产业发展协会提供专业的线上展示平台。

# Blowfish CAIADA 項目開發記錄

## 項目概述
基於 Hugo Blowfish 主題開發的中華AI應用發展協會官方網站。

## 版本記錄

### v0.1.0 (2024-12-19)
**完成繁體字轉簡體字轉換**

#### 主要更改：
1. **配置文件轉換**
   - `i18n/zh-CN.yaml`: 轉換所有界面文字為簡體中文
   - `exampleSite/config/_default/languages.zh-cn.toml`: 更新語言配置
   - `exampleSite/config/_default/menus.zh-cn.toml`: 轉換導航菜單文字
   - `exampleSite/config/_default/hugo.toml`: 設置默認語言為簡體中文

2. **內容文件轉換**
   - 批量轉換所有 `.zh-cn.md` 文件中的繁體字為簡體字
   - 特別修復協會章程頁面 (`about/charter.zh-cn.md`) 的繁體字問題
   - 轉換常見繁體字：會→会、協會→协会、應用→应用、發展→发展等

3. **文件清理**
   - 移除所有英文版本文件 (`.en.md`)
   - 專注於中文版本的維護

4. **技術細節**
   - 使用 `sed` 命令進行批量字符轉換
   - 重新生成網站以更新 public 目錄
   - 確保所有頁面正確顯示簡體中文

#### 解決的問題：
- ✅ 網站界面完全轉換為簡體中文
- ✅ 導航菜單顯示簡體中文
- ✅ 協會章程頁面繁體字問題
- ✅ 所有內容頁面的繁體字轉換

#### 技術方案：
使用高效的 `sed` 批量轉換方法，避免逐個文件處理的複雜性。

---

## 開發環境
- Hugo v0.150.1+extended
- Node.js 環境
- Blowfish 主題

## 部署信息
- 本地開發服務器：http://localhost:1314
- GitHub 倉庫：https://github.com/DylanChiang-Dev/blowfish-CAIADA.git

## 开发命令

### 快速启动开发环境
```bash
# 1. 安装依赖（首次执行）
npm install

# 2. 构建 CSS（生产模式）
npm run build

# 3. 启动开发服务器（推荐使用）
npm run example
# 或手动启动：
# cd exampleSite
# hugo server -D -p 1313
```

### CSS 构建
- `npm run dev` - 开发模式构建 CSS（监控文件变化，实时重载）
- `npm run build` - 生产模式构建 CSS（优化压缩）
- `npm run assets` - 清理并重新复制第三方库资产

### Hugo 服务器
- `npm run example` - 启动开发服务器（推荐，包含草稿和未来内容）
- `npm run example:core` - 快速测试模式（仅构建核心页面）
- `npm run example:production` - 生产模式预览（优化输出）

### 其他工具
- `npm run lighthouse` - 执行 Lighthouse 性能测试
- `npm run build-hugo` - 构建文档网站至 docs 目录

## 架构结构

### 主题目录
- `layouts/` - Hugo 模板文件
  - `_default/` - 默认页面模板
  - `partials/` - 可重用组件
  - `shortcodes/` - 内容短代码
- `assets/` - 静态资源
  - `css/` - 样式文件
  - `js/` - JavaScript 文件
  - `icons/` - SVG 图标
- `exampleSite/` - 示例网站配置和内容

### 配置系统
- `config/_default/` - 主题配置文件
- `exampleSite/config/` - 示例配置
- 支持多语言配置（.en.toml, .zh-cn.toml, .ja.toml, .it.toml）

### 样式系统
- `tailwind.config.js` - Tailwind CSS 配置
- `assets/css/schemes/` - 默认色彩主题
- `assets/css/components/` - 组件样式

## 核心功能

### 响应式设计
- 使用 Tailwind CSS 断点：sm (640px), md (853px), lg (1024px), xl (1280px), 2xl (1536px)
- 深色模式支持（基于 class 切换）

### 图标系统
- FontAwesome 6 SVG 图标
- 自定义社交媒体图标
- 图标位于 `assets/icons/` 目录

### 第三方集成
- Chart.js - 图表支持
- Mermaid - 图表和可视化
- KaTeX - 数学公式
- Fuse.js - 客户端搜索
- TypeIt - 打字效果

## 开发指南

### 代码规范
- 使用 2 空格缩进
- 在列表项之间留空格：`[1, 2, 3]`
- 在 Go 模板标签内留空格：`{{< alert >}}`
- 使用相对路径引用资产（不带前导斜杠）
- 静态文本必须使用 i18n 方法引用

### Git 工作流程
- 主要开发在 `main` 分支进行
- 使用 Gitmoji 在 PR 消息中提供上下文
- 提交消息使用祈使语气，72 字符内摘要
- 引用相关的 GitHub 问题编号

### 本地开发设置
项目使用符号链接进行主题开发：
```bash
# 在主题根目录
cd exampleSite
mkdir -p themes
ln -s ../.. themes/blowfish  # 创建符号链接
hugo server -D -p 1313
```

### 协会内容管理
- **协会介绍**：`exampleSite/content/about/_index.zh-cn.md`
- **协会章程**：`exampleSite/content/about/charter.zh-cn.md`
- **协会新闻**：`exampleSite/content/news/_index.zh-cn.md`
- **首页内容**：`exampleSite/content/_index.zh-cn.md`

### 导航菜单配置
中文导航配置在 `config/_default/menus.zh-cn.toml`：
- 首页、关于协会、协会章程、协会新闻、联系我们
- 平级导航结构，主要功能独立展示
- 社交媒体链接配置

### 测试方法
- 使用 `npm run example` 启动本地开发服务器测试变更
- 访问 http://localhost:1313 查看网站
- 支持热重载，文件变更会自动重建

## 常见问题与解决方案

### Hugo 版本兼容性
- **当前版本**：Hugo 0.150.1+extended (推荐)
- **主题兼容性**：0.141.0 - 0.150.0+ (实际测试 0.150.1 运行良好)
- **版本警告说明**：`WARN Module "blowfish" is not compatible with this Hugo version` 为兼容性声明滞后，可安全忽略，功能完全正常

### Shortcode 错误
- **现象**：`shortcode 'button' must be closed or self-closed`
- **解决**：使用直接 HTML 替代shortcode：`<a href="#" class="inline-block !rounded-md bg-primary-600 px-4 py-2">文字</a>`

### 图标显示问题
- **现象**：缺少 SVG 图标文件
- **解决**：使用 emoji 字符替代，如 🧠、👥、🎓 等

### 内容本地化
- **现象**：英文内容显示在中文页面
- **解决**：设置 `defaultContentLanguage = "zh-cn"`，确保中文为默认语言

## 重要配置细节

### 主题核心配置
- `colorScheme = "blowfish"` - 默认色彩主题
- `defaultAppearance = "dark"` - 默认深色模式，支持自动切换
- `mainSections = []` - 禁用首页文章显示（协会网站特别配置）
- `enableSearch = true` - 启用全站搜索功能
- `enableCodeCopy = true` - 启用代码复制功能
- `hasCJKLanguage = true` - 启用中日韩文字支持
- `defaultContentLanguage = "zh-cn"` - 设置中文为默认语言

### 单语言架构
仅使用简体中文（zh-cn），简化网站结构：
- **配置文件**：`config/_default/languages.zh-cn.toml`
- **内容结构**：所有页面使用 `.zh-cn.md` 文件
- **导航菜单**：`config/_default/menus.zh-cn.toml`
- **国际化**：仅保留 `i18n/zh-CN.yaml` 翻译文件

### 第三方库集成
自动构建系统会复制以下第三方库至 `assets/lib/`：
- **Chart.js** - 图表可视化
- **Mermaid** - 流程图和图表
- **KaTeX** - 数学公式渲染
- **Fuse.js** - 客户端搜索
- **TypeIt** - 打字动画效果
- **jQuery** - DOM 操作（精简版）

### 协会网站特别配置
- **首页布局**：custom 模式，不显示文章列表，突出协会介绍
- **响应式设计**：支持手机、平板、桌面全适配
- **深色模式**：默认深色主题，提供明暗切换
- **中文优化**：针对中文显示优化字体和间距
- **极简导航**：移除活动项目和会员制度，保持网站结构最简洁
- **单语言**：仅保留中文版本，移除多语言切换功能

## 部署指南

### Cloudflare Pages 部署（推荐）

**为什么选择 Cloudflare Pages：**
- 免费且高性能的全球 CDN
- 自动 HTTPS 和无限流量
- GitHub 集成，自动部署
- PR 预览和一键回滚

**快速部署步骤：**

1. **推送到 GitHub**
   ```bash
   git add .
   git commit -m "🚀 CAIADA 网站更新"
   git push origin main
   ```

2. **Cloudflare Pages 配置**
   - 连接 GitHub 仓库
   - **构建设置**：
     - 框架：Hugo
     - 构建命令：`hugo --minify --gc`
     - 构建输出目录：`public`
     - 根目录：`exampleSite`
   - **环境变量**：
     - `HUGO_VERSION`: `0.150.1`
     - `NODE_VERSION`: `18`

**部署优化配置：**
- ✅ 启用 Auto Minify (HTML, CSS, JS)
- ✅ 开启 Brotli 压缩
- ✅ 使用 Cache Everything 规则（静态资源）
- ✅ 启用 HTTP/3 支持
- ✅ 设置中文编码标头：`charset=utf-8`

**GitHub + Cloudflare Pages 优势：**
- 无需复杂的 GitHub Actions 配置
- 自动从 GitHub 仓库拉取代码
- 构建失败自动回滚
- 免费 SSL 证书和全球 CDN

**部署后验证清单：**
- [ ] 中文内容正确显示，无乱码
- [ ] 导航菜单所有链接正常工作
- [ ] 多语言切换功能正常
- [ ] 搜索功能正常运作
- [ ] 深色模式切换正常
- [ ] 移动端响应式适配

