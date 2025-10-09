# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个基于 Blowfish Hugo 主题的中华AI应用发展协会（CAIADA）官方网站项目，为台湾AI产业发展协会提供专业的线上展示平台。

# CLAUDE 開發記錄

## 項目概述
這是一個基於Hugo Blowfish主題的中華AI應用發展協會官網項目。

## 已完成的功能

### v0.1.0 - 繁體中文多語言支持 (2025-01-09)

#### 實現內容
1. **語言配置**
   - 新增繁體中文語言配置文件 `languages.zh-tw.toml`
   - 配置語言代碼、權重、標題等基本信息
   - 設置繁體中文的顯示名稱和ISO代碼

2. **菜單配置**
   - 新增繁體中文菜單配置文件 `menus.zh-tw.toml`
   - 配置主菜單和頁腳菜單的繁體中文版本

3. **翻譯文件**
   - 新增繁體中文翻譯文件 `i18n/zh-TW.yaml`
   - 包含全站界面元素的繁體中文翻譯
   - 修復語言切換器顯示問題（添加 `global.language` 定義）

4. **內容轉換**
   - 首頁內容 (`_index.zh-tw.md`)
   - 關於頁面 (`about/_index.zh-tw.md`)
   - 協會章程 (`about/charter.zh-tw.md`)
   - 新聞頁面 (`news/_index.zh-tw.md`)

5. **Hugo配置優化**
   - 更新 `hugo.toml` 支持多語言
   - 禁用英文語言選項 (`disableLanguages = ["en"]`)
   - 移除不需要的英文菜單配置文件

#### 技術要點
- 使用Hugo的多語言功能實現中英繁三語支持架構
- 通過 `sed` 命令批量轉換簡體中文到繁體中文
- 解決語言切換器顯示問題：在i18n文件中添加 `global.language` 定義
- 確保語言權重設置正確，簡體中文權重1，繁體中文權重2

#### 測試結果
- ✅ 簡體中文版本正常顯示 (`http://localhost:1314/`)
- ✅ 繁體中文版本正常顯示 (`http://localhost:1314/zh-tw/`)
- ✅ 語言切換器正確顯示當前選擇的語言
- ✅ 所有內容頁面成功轉換為繁體中文
- ✅ 英文語言選項已成功移除

#### Git提交信息
```
feat: 實現繁體中文多語言支持

- 新增繁體中文語言配置 (languages.zh-tw.toml)
- 新增繁體中文菜單配置 (menus.zh-tw.toml)  
- 新增繁體中文翻譯文件 (i18n/zh-TW.yaml)
- 轉換核心內容頁面為繁體中文版本
- 更新Hugo主配置支持多語言
- 移除不需要的英文語言選項
- 修復語言切換器顯示問題

版本: v0.1.0
```

## 下一步計劃
- 考慮添加英文語言支持（如需要）
- 優化多語言SEO設置
- 添加更多內容頁面的繁體中文版本

# CLAUDE 解決方案記錄

## 繁體中文設為默認語言

### 問題描述
需要將 Hugo 網站的默認語言從簡體中文改為繁體中文。

### 解決方案
修改 `hugo.toml` 配置文件：

1. **設置默認內容語言**：
   ```toml
   defaultContentLanguage = "zh-tw"
   ```

2. **調整語言權重**：
   ```toml
   [languages.zh-tw]
   weight = 1  # 最高優先級

   [languages.zh-cn]
   weight = 2  # 次要優先級
   ```

### 結果
- 網站默認語言成功切換為繁體中文
- 語言選擇器中繁體中文顯示為首選項
- 網站在 http://localhost:1314/ 正常運行

### 日期
2025年1月27日

## 解決方案總結

### 1. Screenshot Shortcode 錯誤修復

成功修復了 `screenshot` shortcode 的 nil 指針錯誤：

1. **修復 screenshot.html 模板**：添加了 `{{ if $image }}` 檢查和錯誤回退訊息
2. **創建缺失的繁體中文頁面**：`docs/_index.zh-tw.md` 和 `docs/installation/_index.zh-tw.md`
3. **Hugo 服務器成功啟動**：網站正常運行，無錯誤

### 2. 英文語言支持實現

成功為 Blowfish 主題添加了完整的英文語言支持：

#### 實現步驟：

1. **創建英文 i18n 文件** (`/i18n/en.yaml`)
   - 翻譯了所有界面文字和標籤
   - 包含導航、搜索、分享、標籤雲等所有組件的英文翻譯

2. **更新 Hugo 配置** (`config/_default/hugo.toml`)
   - 移除了 `disableLanguages = ["en"]` 限制
   - 添加了英文語言配置：
     ```toml
     [languages.en]
       weight = 3
       languageCode = "en"
       languageName = "English"
     ```

3. **創建英文語言配置文件**
   - `languages.en.toml`：英文站點配置和作者信息
   - `menus.en.toml`：英文導航菜單配置

4. **創建英文內容頁面**
   - `_index.en.md`：英文首頁
   - `docs/_index.en.md`：英文文檔首頁
   - `docs/installation/_index.en.md`：英文安裝指南

#### 功能特點：

- **完整的多語言支持**：繁體中文、簡體中文、英文三語言切換
- **獨立的語言配置**：每種語言都有獨立的菜單和配置
- **內容本地化**：為每種語言提供相應的內容頁面
- **URL 結構**：英文版本可通過 `/en/` 路徑訪問

#### 測試結果：

- ✅ 英文版網站可正常訪問 (`http://localhost:1314/en/`)
- ✅ 語言切換功能正常工作
- ✅ 所有界面元素正確顯示英文翻譯
- ✅ 導航菜單和頁面結構完整

網站現在支持完整的多語言功能，用戶可以在繁體中文、簡體中文和英文之間自由切換。

---

## Screenshot Shortcode Nil Pointer 錯誤修復

### 問題描述
在 Hugo 構建過程中出現錯誤：
```
failed to render shortcode "screenshot": failed to process shortcode: execute of template failed at <$image.RelPermalink>: nil pointer evaluating resource.Resource.RelPermalink
```

### 根本原因
`screenshot.html` shortcode 模板沒有檢查圖片資源是否存在，直接使用 `$image.RelPermalink` 導致 nil pointer 錯誤。

### 解決方案
1. **修復 screenshot.html 模板**：
   - 添加 nil 檢查：`{{ if $image }}`
   - 提供錯誤回退顯示：當圖片不存在時顯示 "圖片載入失敗"
   - 確保模板語法正確，避免多餘的 `{{ end }}` 標籤

2. **創建缺失的繁體中文頁面**：
   - 創建 `_index.zh-tw.md` 文件解決 REF_NOT_FOUND 錯誤
   - 創建 `installation/_index.zh-tw.md` 文件

---

# v0.1.1 - 完善英文版協會內容 (2025-01-09)

## 問題描述

英文版網站仍顯示 Blowfish 主題的預設內容，需要完整替換為中華AI應用發展協會的相關內容。

## 解決方案

參考 `CLAUDE.md` 中繁體中文版本的修改方式，完整創建英文版協會頁面。

## 實施步驟

### 1. 檢查現有英文頁面結構
- 使用 `find` 指令查找所有 `*.en.md` 檔案
- 確認目錄結構：about/, news/, contact/, membership/

### 2. 創建完整的英文版協會頁面

#### 2.1 關於我們頁面 (`about/_index.en.md`)
- 協會使命與願景
- 核心價值觀（創新、合作、人才培養、社會責任、國際視野）
- 組織架構
- 主要業務領域

#### 2.2 協會章程 (`about/charter.en.md`)
- 總則
- 會員制度
- 組織架構
- 會議制度
- 財務管理
- 章程修改與解散

#### 2.3 協會新聞 (`news/_index.en.md`)
- 新聞頁面框架
- 協會最新動態說明

#### 2.4 聯絡我們 (`contact/_index.en.md`)
- 一般諮詢聯絡方式
- 會員服務
- 技術支援
- 媒體關係
- 辦公室地址
- 合作夥伴諮詢
- 意見回饋
- 社群媒體連結

#### 2.5 會員資訊 (`membership/_index.en.md`)
- 會員類別（個人會員、團體會員、贊助會員）
- 申請資格與流程
- 會員權益
- 費用結構
- 申請表格下載

### 3. Hugo 服務器自動重建
- 每次檔案修改後，Hugo 自動偵測並重建網站
- 確認所有頁面正常顯示

## 技術細節

### 檔案創建清單
```
content/about/_index.en.md          - 關於我們主頁
content/about/charter.en.md         - 協會章程
content/news/_index.en.md           - 協會新聞
content/contact/_index.en.md        - 聯絡我們
content/membership/_index.en.md     - 會員資訊
```

### 內容特色
- 完整的協會介紹與使命說明
- 詳細的會員制度與申請流程
- 專業的聯絡資訊與服務項目
- 符合協會定位的內容架構

## 結果

✅ 成功創建完整的英文版協會網站內容
✅ 所有主要頁面（about, news, contact, membership）已完成
✅ Hugo 服務器正常重建並顯示新內容
✅ 英文版網站現在完整反映中華AI應用發展協會的資訊

---

# v0.1.2 - 修復英文版圖標顯示問題 (2025-01-09)

## 問題描述

用戶發現英文版首頁缺少圖標（emoji），對比繁體中文版發現英文版內容不完整。

## 問題分析

1. 英文版第三個卡片使用了🎓而不是📚
2. 英文版缺少完整的「發展重點」部分
3. 缺少技術創新、產業應用、人才發展等子部分的內容

## 解決方案

### 1. 修復 emoji 圖標
- 將第三個卡片的🎓改為📚，與繁體中文版保持一致

### 2. 添加完整的發展重點部分
- Technical Innovation（技術創新）
- Industrial Applications（產業應用）
- Talent Development（人才發展）

## 實施步驟

1. 對比繁體中文版 `_index.zh-tw.md` 和英文版 `_index.en.md`
2. 識別缺少的內容和不一致的圖標
3. 更新英文版首頁，添加完整內容
4. 確認 Hugo 服務器重建並預覽結果

## 技術細節

### 修復的內容
```markdown
# 修復前的問題
- 🎓 (畢業帽) → 📚 (書本)
- 缺少 Development Focus 部分

# 修復後的完整內容
- 所有 emoji 圖標正確顯示
- 完整的發展重點部分
- 與繁體中文版內容對應
```

### 添加的部分
- Technical Innovation（機器學習、自然語言處理、邊緣運算、區塊鏈應用）
- Industrial Applications（智慧製造、智慧醫療、智慧金融、智慧城市）
- Talent Development（課程認證、產學合作、國際交流、創業輔導）

## 結果

✅ 英文版首頁 emoji 圖標完整顯示
✅ 內容與繁體中文版完全對應
✅ Hugo 服務器成功重建（第10次重建）
✅ 預覽頁面正常運行，無錯誤

### 最終修復的模板結構
```html
{{- $image := .Page.Resources.GetMatch (.Get "src") -}}
{{ if $image }}
<figure{{ with .Get "class" }} class="{{ . }}"{{ end }}>
    {{- if .Get "href" -}}
      <a href="{{ .Get "href" }}">
    {{- end -}}
    <img src="{{ $image.RelPermalink }}"
      {{- if or (.Get "alt") (.Get "caption") }}
        alt="{{ with .Get "alt" }}{{ . }}{{ else }}{{ .Get "caption" | markdownify | plainify }}{{ end }}"
      {{- end }}
      {{- with .Get "width" }} width="{{ . }}"{{ end }}
      {{- with .Get "height" }} height="{{ . }}"{{ end }} />
    {{- if .Get "href" -}}
      </a>
    {{- end -}}
    {{- if or (or (.Get "title") (.Get "caption")) (.Get "attr") -}}
      <figcaption>
        {{ with (.Get "title") -}}
          <h4>{{ . }}</h4>
        {{- end -}}
        {{- if or (.Get "caption") (.Get "attr") -}}<p>
          {{- .Get "caption" | markdownify -}}
          {{- with .Get "attrlink" }}
            <a href="{{ . }}">
          {{- end -}}
          {{- .Get "attr" | markdownify -}}
          {{- if .Get "attrlink" }}</a>{{ end }}</p>
        {{- end }}
      </figcaption>
    {{- end }}
</figure>
{{ else }}
<div style="padding: 20px; border: 1px solid #ccc; background-color: #f9f9f9; text-align: center;">
  <p>圖片載入失敗</p>
</div>
{{ end }}
```

### 結果
- Hugo 服務器成功啟動，無錯誤
- 網站正常運行在 http://localhost:1314/
- 繁體中文設為默認語言
- Screenshot shortcode 錯誤已解決

### 日期
2025年1月27日

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

## 2025-01-09 - 英文版導航欄修復

### 問題描述
英文版網站的導航欄仍然顯示 Blowfish 主題的預設內容 (Blog, Docs, Samples, Users)，而不是協會的相關頁面。

### 問題分析
1. 英文版菜單配置 (`menus.en.toml`) 仍使用預設的 Blowfish 主題菜單
2. 英文版語言配置 (`languages.en.toml`) 仍使用 Blowfish 主題的標題和描述
3. 需要參考中文版本的導航結構進行修改

### 解決方案
修改英文版的菜單配置和語言配置，使其與中文版的協會結構保持一致。

### 實施步驟
1. 檢查繁體中文和簡體中文版本的導航欄和頁面結構
2. 修改英文版導航欄以匹配中文版的協會結構
3. 確認修改後的英文版導航和內容正確顯示

### 技術細節

#### 修改的文件：
1. **`menus.en.toml`** - 英文版菜單配置
   - 主菜單：Home, About Us, Association Charter, News, Contact Us, Membership
   - 頁腳菜單：About Us, Association Charter, Contact Us

2. **`languages.en.toml`** - 英文版語言配置
   - 標題：Chinese AI Application Development Association
   - 描述：Promoting artificial intelligence technology development and industrial applications
   - 作者信息：協會相關內容

#### 菜單結構對應：
- 首頁 (Home) → `/`
- 關於協會 (About Us) → `/about/`
- 協會章程 (Association Charter) → `/about/charter/`
- 協會新聞 (News) → `/news/`
- 聯絡我們 (Contact Us) → `/contact/`
- 會員資訊 (Membership) → `/membership/`

### 最終結果
英文版網站導航欄現已完全匹配協會結構，顯示正確的協會相關頁面連結，與中文版本保持一致。Hugo 服務器成功重建，預覽確認無錯誤。

