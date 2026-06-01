# 中華AI應用發展協會官方網站 Memory

## Context Loading Policy

- This file is a progressive memory entrypoint, not a full-session transcript.
- Start by reading this policy and the latest entries only.
- Search this file with narrow keywords before opening older sections or linked artifacts.
- Record durable decisions, current environment facts, deployment notes, and repeated gotchas here.
- Do not record secrets or raw `.env` values.

## Current Repository Facts

- Owner: `DylanChiang-Dev`
- Repository: `blowfish-CAIADA`
- Origin: `https://github.com/DylanChiang-Dev/blowfish-CAIADA`
- Local path: `/Users/dc/Documents/github/DylanChiang-Dev/blowfish-CAIADA`
- Main branch: `main`
- Documentation standardized: 2026-05-18 02:24 CST

## Latest Entries

### 2026-06-02 首頁會員入口先以繁中定稿

- 使用者決定：首頁改版先以繁中內容為主，其他語言在繁中最終定稿前不要同步改寫。
- 當前繁中方向：首頁作為「協會會員入口」，第一屏只放 Facebook 粉絲專頁、X、微信公眾號三個 logo 按鈕；加入會員模塊保持簡短介紹與按鈕，不在首頁顯示費用。
- 新增繁中 `/join/` 會員權益頁，加入入口暫顯示「加入入口籌備中」，待外部知識星球連結確定後再替換。
- 公開首頁不介紹 Token/VPN 或私域內服務；產業交流活動區塊複用協會新聞。
- 實作注意：避免在簡中、英文、越南文首頁提前放入未定稿的會員平台文案。

### 2026-05-22 官網倉庫架構重整

- 決策：在原倉庫 `DylanChiang-Dev/blowfish-CAIADA` 原地重整，不新建倉庫。
- 架構：倉庫根目錄直接作為 Hugo 網站根；Blowfish 主題完整 vendor 到 `themes/blowfish`，作為普通 tracked source，不使用 Git submodule。
- 本地開發命令：`hugo server`。
- 生產建置命令：`hugo --minify --gc`。
- Cloudflare Pages 需要使用倉庫根目錄 `/`，輸出目錄 `public`，`HUGO_VERSION=0.161.1`。
- 相關計劃：`plans/2026-05-22-官网仓库架构重整计划-v0.0.2.md`；v0.0.1 的官方 submodule 方案已廢棄。

### 2026-05-18 02:24 CST Documentation entrypoint standardization

- Standardized root agent documents to `AGENTS.md`, `RULES.md`, and `MEMORY.md`.
- Migrated useful content from legacy agent/memory files into the standard files where present.
- Repository should now start from `AGENTS.md`, then `RULES.md`, then this file's policy and latest entries.
