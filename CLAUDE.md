# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 專案概述

這是一個基於 Blowfish Hugo 主題的中華AI應用發展協會（CAIADA）官方網站項目，為台灣AI產業發展協會提供專業的線上展示平台。

## 開發命令

### 快速啟動開發環境
```bash
# 1. 安裝依賴（首次執行）
npm install

# 2. 構建 CSS（生產模式）
npm run build

# 3. 啟動開發伺服器（推薦使用）
npm run example
# 或手動啟動：
# cd exampleSite
# hugo server -D -p 1313
```

### CSS 構建
- `npm run dev` - 開發模式構建 CSS（監控文件變化，實時重載）
- `npm run build` - 生產模式構建 CSS（優化壓縮）
- `npm run assets` - 清理並重新複製第三方庫資產

### Hugo 伺服器
- `npm run example` - 啟動開發伺服器（推薦，包含草稿和未來內容）
- `npm run example:core` - 快速測試模式（僅構建核心頁面）
- `npm run example:production` - 生產模式預覽（優化輸出）

### 其他工具
- `npm run lighthouse` - 執行 Lighthouse 效能測試
- `npm run build-hugo` - 構建文檔網站至 docs 目錄

## 架構結構

### 主題目錄
- `layouts/` - Hugo 模板文件
  - `_default/` - 預設頁面模板
  - `partials/` - 可重用組件
  - `shortcodes/` - 內容短代碼
- `assets/` - 靜態資源
  - `css/` - 樣式文件
  - `js/` - JavaScript 文件
  - `icons/` - SVG 圖標
- `exampleSite/` - 示例網站配置和內容

### 配置系統
- `config/_default/` - 主題配置文件
- `exampleSite/config/` - 示例配置
- 支援多語言配置（.en.toml, .zh-cn.toml, .ja.toml, .it.toml）

### 樣式系統
- `tailwind.config.js` - Tailwind CSS 配置
- `assets/css/schemes/` - 預設色彩主題
- `assets/css/components/` - 組件樣式

## 核心功能

### 響應式設計
- 使用 Tailwind CSS 斷點：sm (640px), md (853px), lg (1024px), xl (1280px), 2xl (1536px)
- 深色模式支援（基於 class 切換）

### 圖標系統
- FontAwesome 6 SVG 圖標
- 自定義社交媒體圖標
- 圖標位於 `assets/icons/` 目錄

### 第三方整合
- Chart.js - 圖表支援
- Mermaid - 圖表和視覺化
- KaTeX - 數學公式
- Fuse.js - 客戶端搜索
- TypeIt - 打字效果

## 開發指南

### 代碼規範
- 使用 2 空格縮進
- 在列表項之間留空格：`[1, 2, 3]`
- 在 Go 模板標籤內留空格：`{{< alert >}}`
- 使用相對路徑引用資產（不帶前導斜杠）
- 靜態文本必須使用 i18n 方法引用

### Git 工作流程
- 主要開發在 `main` 分支進行
- 使用 Gitmoji 在 PR 消息中提供上下文
- 提交消息使用祈使語氣，72 字符內摘要
- 引用相關的 GitHub 問題編號

### 本地開發設置
專案使用符號鏈接進行主題開發：
```bash
# 在主題根目錄
cd exampleSite
mkdir -p themes
ln -s ../.. themes/blowfish  # 創建符號鏈接
hugo server -D -p 1313
```

### 協會內容管理
- **協會介紹**：`exampleSite/content/about/_index.zh-cn.md`
- **協會章程**：`exampleSite/content/about/charter.zh-cn.md`
- **協會新聞**：`exampleSite/content/news/_index.zh-cn.md`
- **首頁內容**：`exampleSite/content/_index.zh-cn.md`

### 導航菜單配置
中文導航配置在 `config/_default/menus.zh-cn.toml`：
- 首頁、關於協會、協會章程、協會新聞、聯絡我們
- 平級導航結構，主要功能獨立展示
- 社交媒體連結配置

### 測試方法
- 使用 `npm run example` 啟動本地開發伺服器測試變更
- 訪問 http://localhost:1313 查看網站
- 支援熱重載，文件變更會自動重建

## 常見問題與解決方案

### Hugo 版本兼容性
- **當前版本**：Hugo 0.150.1+extended (推薦)
- **主題兼容性**：0.141.0 - 0.150.0+ (實際測試 0.150.1 運行良好)
- **版本警告說明**：`WARN Module "blowfish" is not compatible with this Hugo version` 為兼容性聲明滯後，可安全忽略，功能完全正常

### Shortcode 錯誤
- **現象**：`shortcode 'button' must be closed or self-closed`
- **解決**：使用直接 HTML 替代shortcode：`<a href="#" class="inline-block !rounded-md bg-primary-600 px-4 py-2">文字</a>`

### 圖標顯示問題
- **現象**：缺少 SVG 圖標文件
- **解決**：使用 emoji 字符替代，如 🧠、👥、🎓 等

### 內容本地化
- **現象**：英文內容顯示在中文頁面
- **解決**：設置 `defaultContentLanguage = "zh-cn"`，確保中文為預設語言

## 重要配置細節

### 主題核心配置
- `colorScheme = "blowfish"` - 預設色彩主題
- `defaultAppearance = "dark"` - 預設深色模式，支援自動切換
- `mainSections = []` - 禁用首頁文章顯示（協會網站特別配置）
- `enableSearch = true` - 啟用全站搜索功能
- `enableCodeCopy = true` - 啟用代碼複製功能
- `hasCJKLanguage = true` - 啟用中日韓文字支持
- `defaultContentLanguage = "zh-cn"` - 設置中文為預設語言

### 單語言架構
僅使用繁體中文（zh-cn），簡化網站結構：
- **配置文件**：`config/_default/languages.zh-cn.toml`
- **內容結構**：所有頁面使用 `.zh-cn.md` 文件
- **導航菜單**：`config/_default/menus.zh-cn.toml`
- **國際化**：僅保留 `i18n/zh-CN.yaml` 翻譯文件

### 第三方庫集成
自動構建系統會複製以下第三方庫至 `assets/lib/`：
- **Chart.js** - 圖表視覺化
- **Mermaid** - 流程圖和圖表
- **KaTeX** - 數學公式渲染
- **Fuse.js** - 客戶端搜索
- **TypeIt** - 打字動畫效果
- **jQuery** - DOM 操作（精簡版）

### 協會網站特別配置
- **首頁佈局**：custom 模式，不顯示文章列表，突出協會介紹
- **響應式設計**：支援手機、平板、桌面全適配
- **深色模式**：預設深色主題，提供明暗切換
- **中文優化**：針對中文顯示優化字體和間距
- **極簡導航**：移除活動項目和會員制度，保持網站結構最簡潔
- **單語言**：僅保留中文版本，移除多語言切換功能

## 部署指南

### Cloudflare Pages 部署（推薦）

**為什麼選擇 Cloudflare Pages：**
- 免費且高性能的全球 CDN
- 自動 HTTPS 和無限流量
- GitHub 整合，自動部署
- PR 預覽和一鍵回滾

**快速部署步驟：**

1. **推送到 GitHub**
   ```bash
   git add .
   git commit -m "🚀 CAIADA 網站更新"
   git push origin main
   ```

2. **Cloudflare Pages 配置**
   - 連接 GitHub 倉庫
   - **構建設置**：
     - 框架：Hugo
     - 構建命令：`hugo --minify --gc`
     - 構建輸出目錄：`public`
     - 根目錄：`exampleSite`
   - **環境變量**：
     - `HUGO_VERSION`: `0.150.1`
     - `NODE_VERSION`: `18`

**部署優化配置：**
- ✅ 啟用 Auto Minify (HTML, CSS, JS)
- ✅ 開啟 Brotli 壓縮
- ✅ 使用 Cache Everything 規則（靜態資源）
- ✅ 啟用 HTTP/3 支援
- ✅ 設置中文編碼標頭：`charset=utf-8`

**GitHub + Cloudflare Pages 優勢：**
- 無需複雜的 GitHub Actions 配置
- 自動從 GitHub 倉庫拉取代碼
- 構建失敗自動回滾
- 免費 SSL 證書和全球 CDN

**部署後驗證清單：**
- [ ] 中文內容正確顯示，無亂碼
- [ ] 導航菜單所有鏈接正常工作
- [ ] 多語言切換功能正常
- [ ] 搜索功能正常運作
- [ ] 深色模式切換正常
- [ ] 移動端響應式適配

