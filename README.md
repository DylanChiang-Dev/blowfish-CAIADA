# 中華AI應用發展協會官方網站

基於 Hugo Blowfish 主題建構的響應式官方網站，專為台灣AI產業發展協會提供專業的線上展示平台。

## ✨ 主要特色

- 🎨 **響應式設計** - 完美支援手機、平板、桌面全適配
- 🌙 **深色模式** - 預設深色主題，提供明暗切換
- 🔍 **全站搜索** - 由 Fuse.js 驅動的客戶端搜索
- 📱 **極簡導航** - 簡潔清晰的網站結構
- 🇨🇳 **中文優化** - 針對中文顯示優化字體和間距
- ⚡ **快速載入** - 經優化的靜態資源和全球 CDN

## 🚀 快速開始

### 環境需求

- **Hugo** 0.141.0 - 0.150.0+ (推薦 0.150.1+extended)
- **Node.js** 18+ (用於 CSS 構建)
- **Git** (用於版本控制)

### 本地開發

```bash
# 1. 安裝依賴
npm install

# 2. 構建 CSS
npm run build

# 3. 啟動開發伺服器
npm run example
```

訪問 http://localhost:1313 查看網站。

### 常用命令

```bash
# CSS 構建
npm run build      # 生產模式構建 CSS
npm run dev        # 開發模式監控文件變化

# Hugo 服務器
npm run example            # 開發模式（推薦）
npm run example:core       # 快速測試模式
npm run example:production # 生產模式預覽

# 工具
npm run lighthouse   # 執行效能測試
npm run assets       # 重新複製第三方庫
```

## 📁 專案結構

```
├── exampleSite/          # 示例網站內容
│   ├── config/          # Hugo 配置文件
│   ├── content/         # 網站內容（僅中文）
│   └── static/          # 靜態資源
├── assets/              # 主題資源
│   ├── css/            # 樣式文件
│   ├── js/             # JavaScript 文件
│   └── icons/          # SVG 圖標
├── layouts/             # Hugo 模板
├── i18n/               # 國際化（僅中文）
└── CLAUDE.md           # 開發指南
```

## 🌐 網站架構

### 內容管理

- **協會介紹**：`exampleSite/content/about/_index.zh-cn.md`
- **協會章程**：`exampleSite/content/about/charter.zh-cn.md`
- **協會新聞**：`exampleSite/content/news/_index.zh-cn.md`
- **首頁內容**：`exampleSite/content/_index.zh-cn.md`

### 導航結構

```
首頁 → 關於協會 → 協會章程 → 協會新聞 → 聯絡我們
```

### 單語言配置

- **語言**：僅使用繁體中文 (zh-cn)
- **編碼**：UTF-8
- **優化**：針對中文顯示特別優化

## 🚀 部署指南

### GitHub + Cloudflare Pages

1. **推送到 GitHub**
   ```bash
   git add .
   git commit -m "🚀 CAIADA 網站更新"
   git push origin main
   ```

2. **Cloudflare Pages 配置**
   - 連接 GitHub 倉庫
   - 構建命令：`hugo --minify --gc`
   - 構建輸出目錄：`public`
   - 根目錄：`exampleSite`
   - 環境變量：
     - `HUGO_VERSION`: `0.150.1`
     - `NODE_VERSION`: `18`

3. **性能優化**
   - 啟用 Auto Minify (HTML, CSS, JS)
   - 開啟 Brotli 壓縮
   - 使用 Cache Everything 規則
   - 啟用 HTTP/3 支援

## 🛠️ 技術棧

- **Hugo** - 靜態網站生成器
- **Blowfish** - Hugo 主題
- **Tailwind CSS** - CSS 框架
- **Fuse.js** - 客戶端搜索
- **Chart.js** - 圖表支援
- **Mermaid** - 圖表視覺化
- **KaTeX** - 數學公式

## 📝 開發指南

詳細的開發指南請參考 [CLAUDE.md](./CLAUDE.md) 文件。

## 🌐 Cloudflare Pages 部署

現在可以在 Cloudflare Pages 中連接此 GitHub 倉庫並配置自動部署：

### 1. Cloudflare Pages 設置
- **構建命令**：`hugo --minify --gc`
- **構建輸出目錄**：`public`
- **根目錄**：`exampleSite`
- **環境變量**：
  - `HUGO_VERSION`: `0.150.1`
  - `NODE_VERSION`: `18`

### 2. 部署後驗證
- [ ] 中文內容正確顯示
- [ ] 導航菜單功能正常
- [ ] 深色模式切換正常
- [ ] 移動端響應式適配

GitHub 倉庫現在已經完全準備好用於 Cloudflare Pages 部署。

## 🤝 貢獻指南

1. Fork 本專案
2. 創建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交變更 (`git commit -m '✨ Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 開啟 Pull Request

## 📄 授權

本專案基於 MIT 授權條款 - 詳見 [LICENSE](LICENSE) 文件。

## 🌟 支援

如果遇到問題或有建議，請：

- 查看 [CLAUDE.md](./CLAUDE.md) 開發指南
- 提交 Issue 到 GitHub Issues
- 聯絡開發團隊

---

**中華AI應用發展協會** - 推動台灣AI產業發展 🚀