# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 專案概述

這是一個基於 Blowfish Hugo 主題的中華AI應用發展協會（CAIADA）官方網站項目，為台灣AI產業發展協會提供專業的線上展示平台。

## 開發命令

### 快速啟動開發環境
```bash
# 1. 安裝依賴（首次執行）
npm install

# 2. 構建 CSS
npm run build

# 3. 啟動開發伺服器
cd exampleSite
hugo server -D -p 1313
```

### CSS 構建
- `npm run dev` - 開發模式構建 CSS（監控文件變化）
- `npm run build` - 生產模式構建 CSS
- `npm run assets` - 清理並重新複製供應商資產

### Hugo 伺服器
- `npm run example` - 啟動示例網站（開發模式，包含未來和過期內容）
- `npm run example:core` - 僅構建核心功能（用於快速測試）
- `npm run example:production` - 生產模式示例

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
- **會員制度**：`exampleSite/content/membership/_index.zh-cn.md`
- **活動項目**：`exampleSite/content/activities/_index.zh-cn.md`
- **協會新聞**：`exampleSite/content/news/_index.zh-cn.md`
- **首頁內容**：`exampleSite/content/_index.zh-cn.md`

### 導航菜單配置
中文導航配置在 `config/_default/menus.zh-cn.toml`：
- 首頁、關於協會、會員制度、活動項目、協會新聞
- 支援嵌套菜單結構
- 社交媒體連結配置

### 測試方法
- 使用 `npm run example` 啟動本地開發伺服器測試變更
- 訪問 http://localhost:1313 查看網站
- 支援熱重載，文件變更會自動重建

## 常見問題與解決方案

### Hugo 版本警告
- **現象**：`WARN Module "blowfish" is not compatible with this Hugo version`
- **原因**：當前使用 Hugo 0.150.1，主題聲明兼容 0.141.0-0.150.0
- **解決**：可忽略警告，功能完全正常，或等待主題更新兼容性聲明

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

### 主題配置
- `colorScheme = "blowfish"` - 預設色彩主題
- `defaultAppearance = "dark"` - 預設深色模式
- `mainSections = []` - 禁用首頁文章顯示（專案特別配置）
- `enableSearch = true` - 啟用搜索功能
- `enableCodeCopy = true` - 啟用代碼複製

### 多語言支援
主要語言為繁體中文（zh-cn），支援英文切換：
- `config/_default/languages.zh-cn.toml` - 中文語言配置
- `config/_default/languages.en.toml` - 英文語言配置
- 內容對應 `content/_index.zh-cn.md` 和 `_index.en.md`

### 版本兼容性
- Hugo: 0.141.0 - 0.150.0+ (當前使用 0.150.1)
- 版本警告不影響功能，是兼容性聲明滯後導致
- Node.js: 用於 Tailwind CSS 構建

### 協會網站特別配置
- **首頁設置**：採用 custom 布局，禁用文章列表顯示
- **導航結構**：包含首頁、關於協會、會員制度、活動項目、協會新聞等
- **協會新聞頁面**：使用 list 布局，顯示 docs 區段的技術文檔
- **語言偏好**：設置中文為預設語言 (`defaultContentLanguage = "zh-cn"`)

## 部署指南

### Cloudflare Pages 部署（推薦）

**為什麼選擇 Cloudflare Pages：**
- 免費且高性能的全球 CDN
- 自動 HTTPS 和無限流量
- GitHub 整合，自動部署
- PR 預覽和一鍵回滾

**部署步驟：**

1. **準備生產配置**
   ```bash
   # 創建生產環境配置
   mkdir -p exampleSite/config/production
   cat > exampleSite/config/production/hugo.toml << 'EOF'
   baseURL = "https://your-domain.pages.dev"
   EOF
   ```

2. **推送到 GitHub**
   ```bash
   git add .
   git commit -m "🚀 準備 CF Pages 部署"
   git push origin main
   ```

3. **Cloudflare Pages 設置**
   - 登錄 Cloudflare Dashboard
   - Pages > 創建項目 > 連接 GitHub
   - 構建配置：
     ```
     框架預設: Hugo
     構建命令: hugo --minify --gc
     構建輸出目錄: public
     根目錄: exampleSite
     環境變量: HUGO_VERSION=0.150.1
     ```

4. **部署配置**
   ```bash
   # 可選：添加 _redirects 文件處理單頁應用
   echo "/*    /index.html   200" > exampleSite/static/_redirects
   ```

**環境變量設置：**
- `HUGO_VERSION`: `0.150.1`
- `NODE_VERSION`: `18` (如需構建 CSS)

**性能優化：**
- 啟用 Auto Minify (HTML, CSS, JS)
- 開啟 Brotli 壓縮
- 使用 Cache Everything 規則
- 啟用 HTTP/3 支援

**協會網站部署注意事項：**
- 確保中文內容正確顯示
- 驗證導航菜單所有鏈接正常工作
- 測試多語言切換功能
- 檢查表單和聯絡方式

### 其他部署選項

**GitHub Pages：**
- 免費但僅限公開倉庫
- 無需第三方服務
- 需要手動設置 GitHub Actions

**Netlify：**
- 優秀的 CI/CD 整合
- 免費額度限制較小
- 表單和函數支援