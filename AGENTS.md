# AGENTS.md - AI Toolbook 專案開發規範

## 1. 專案目的 (Project Purpose)
本專案是一個「個人 AI 工具實戰手冊」靜態網站，旨在用一致的版面與結構，記錄各種 AI 工具的核心功能、適用場景與實戰提示詞（Prompts）。
**核心目標**：讓未來的 AI 協作者能透過閱讀本文件，以完全一致的風格與結構，快速新增工具頁面並同步更新首頁目錄。

## 2. 技術棧與視覺風格 (Tech Stack & Design System)
- **技術限制**：僅使用純 HTML5、Vanilla JavaScript 與 Tailwind CSS（透過 CDN 引入：`<script src="https://cdn.tailwindcss.com"></script>`）。嚴禁引入 React、Vue 或需要 npm build 的框架，確保可直接部署於 GitHub Pages。
- **色彩規範**：
  - 背景色：極淺灰 `bg-slate-50`
  - 卡片背景：純白 `bg-white`，搭配細邊框 `border border-slate-200` 與圓角 `rounded-xl`
  - 主色調（強調色）：靛藍色 `indigo-600`（按鈕、標籤、重點標題）
  - 主要文字：`text-slate-800`；次要說明文字：`text-slate-600`
- **字體與排版**：使用系統預設無襯線字體，內文最大寬度限制為 `max-w-4xl mx-auto`，保持充足的留白（`p-6` 或 `p-8`）。

## 3. 檔案命名與目錄結構 (File Structure & Naming)
```text
/
├── AGENTS.md             # 本規範文件
├── README.md             # 專案說明文件
├── index.html            # 網站首頁（工具總覽列表）
└── tools/                # 所有子頁面必須放在此資料夾內
    └── [tool-slug].html  # 檔名全小寫，單字間用連字號連接（例如：claude-code.html）
```

## 4. 頁面結構與新增內容格式 (Page Templates & Content Rules)

### A. 工具內頁 (`tools/[tool-slug].html`) 必須包含以下 4 個區塊：
1. **頂部導覽列**：左側顯示網站名稱，右側必須有「← 返回工具列表」連結（指向 `../index.html`）。
2. **工具標頭區 (Hero)**：
   - 工具名稱（`<h1>`）
   - 一句話定位描述
   - 分類標籤（僅限使用：`寫作輔助`、`程式開發`、`圖像生成`、`效率工具` 這四種之一）
   - 官方網站外連按鈕
3. **核心功能與適用場景**：使用 2 欄式網格（`grid-cols-1 md:grid-cols-2 gap-4`）條列 3～4 個核心亮點。
4. **實戰 Prompt 範例區**：提供 1～2 個可直接複製的指令範例，必須使用深色背景區塊（`bg-slate-900 text-slate-100 p-4 rounded-lg font-mono text-sm`）呈現，方便閱讀。

### B. 首頁 (`index.html`) 卡片格式：
每當在 `tools/` 新增一個頁面時，必須同步在 `index.html` 的 `<main id="tool-grid">` 區塊內新增一張對應的卡片，卡片需包含：工具名稱、分類標籤、一句話簡介，以及連往 `tools/[tool-slug].html` 的超連結。

## 5. AI 協作與修改規則 (AI Workflow Rules)
1. **新增頁面時的標準作業程序 (SOP)**：
   - 步驟一：在 `tools/` 下建立符合命名規範的新 HTML 檔案，嚴格套用第 4 點的 4 個區塊結構與第 2 點的 Tailwind 樣式。
   - 步驟二：主動檢查並更新 `index.html`，將新工具的卡片加入列表中（新工具放在最前面）。
2. **修改限制**：
   - 除非使用者明確要求，否則**不可更動**現有頁面的 CSS 色彩系統與導覽列結構。
   - 確保所有相對路徑（如 `../index.html` 與 `tools/xxx.html`）在本地開啟與 GitHub Pages 環境下皆可正常跳轉。
   - 撰寫內容時，語氣需客觀、精煉，避免過度浮誇的行銷詞彙。
