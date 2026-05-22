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

- **Hugo** 0.161.1+extended
- **Git** (用於版本控制)

### 本地開發

```bash
hugo server
```

訪問 http://localhost:1313 查看網站。

### 常用命令

```bash
hugo server        # 本地開發
hugo --minify --gc # 生產建置
```

## 📁 專案結構

```
├── content/             # 網站內容
├── assets/img/          # 協會自有圖片
├── config/_default/     # Hugo 與多語言配置
├── layouts/             # 官網自定義模板覆寫
├── themes/blowfish/     # 已 vendor 的 Blowfish 主題源碼
├── plans/               # 技術計劃
├── AGENTS.md            # Agent 協作入口
├── RULES.md             # 倉庫規則
└── MEMORY.md            # 協作記憶
```

## 🌐 網站架構

### 內容管理

- **首頁內容**：`content/_index.zh-tw.md`
- **協會介紹**：`content/about/_index.zh-tw.md`
- **協會新聞**：`content/news/_index.zh-tw.md`

### 導航結構

```
首页 → 关于协会 → 协会新闻 → 联络我们
```

### 多語言配置

- **預設語言**：繁體中文 (`zh-tw`)
- **其他語言**：簡體中文、英文、越南文
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
   - 根目錄：`/`
   - 環境變量：
     - `HUGO_VERSION`: `0.161.1`

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

詳細的開發指南請參考 [AGENTS.md](./AGENTS.md)、[RULES.md](./RULES.md) 與 [MEMORY.md](./MEMORY.md)。

## 🌐 Cloudflare Pages 部署

現在可以在 Cloudflare Pages 中連接此 GitHub 倉庫並配置自動部署：

### 1. Cloudflare Pages 設置
- **構建命令**：`hugo --minify --gc`
- **構建輸出目錄**：`public`
- **根目錄**：`/`
- **環境變量**：
  - `HUGO_VERSION`: `0.161.1`

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

- 查看 [AGENTS.md](./AGENTS.md) 開發指南
- 提交 Issue 到 GitHub Issues
- 聯絡開發團隊

---

**中華AI應用發展協會** - 推動台灣AI產業發展 🚀
