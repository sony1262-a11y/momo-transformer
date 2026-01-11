# 🎯 MOMO 廣告圖修正器 v5.4

自動調整圖片尺寸、背景延伸、格式轉換的專業工具

**線上使用：** `https://sony1262-a11y.github.io/momo-transformer/`

---

## ✨ 主要功能

- 📐 **尺寸校正**：自動調整為 1000×1000
- 🎯 **智慧偵測**：自動判斷內容邊界
- 🎨 **背景處理**：智能延伸或保持純淨
- ⚙️ **格式轉換**：自動轉為 JPG
- 📦 **檔名清理**：移除中文、特殊符號
- 🔧 **手動微調**：即時預覽調整
- 💾 **批次處理**：支援多張圖片

---

## 🚀 GitHub Pages 首次設定（只需做一次）

### Step 1：創建 GitHub 帳號

1. 前往 [https://github.com](https://github.com)
2. 點擊右上角「Sign up」
3. 填寫 Email、密碼、用戶名
4. 驗證 Email 完成註冊

### Step 2：創建 Repository

1. 登入後點右上角「+」圖示
2. 選擇「New repository」
3. 填寫資訊：
   - **Repository name:** `momo-transformer`
   - **Description:** MOMO 廣告圖修正器
   - **Public/Private:** 選擇 `Public`
   - **勾選：** Add a README file
4. 點擊「Create repository」

### Step 3：上傳檔案

1. 進入剛創建的 Repository
2. 點擊「Add file」→「Upload files」
3. **重要：** 將 `momo_transformer_v5_3_FINAL.html` 重新命名為 `index.html`
4. 拖曳 `index.html` 到上傳區域
5. 在下方填寫 Commit message（例如：Initial upload）
6. 點擊「Commit changes」

### Step 4：啟用 GitHub Pages

1. 點擊 Repository 頂部的「Settings」
2. 左側選單找到「Pages」
3. 在 **Build and deployment** 區域：
   - **Source:** 選擇「Deploy from a branch」
   - **Branch:** 選擇「main」
   - **資料夾:** 選擇「/ (root)」
4. 點擊「Save」
5. 等待 1-2 分鐘，頁面會顯示網址
6. 網址格式：`https://yourusername.github.io/momo-transformer/`

### Step 5：測試與分享

1. 點擊顯示的網址測試是否能正常開啟
2. 複製網址分享給同事
3. 同事可將網址加入「我的最愛」方便使用

**✅ 首次設定完成！**

---

## 🔄 更新 Code 的步驟（以後每次修改）

### 方法 A：網頁直接編輯（推薦，最簡單）

1. 進入 GitHub Repository
2. 點擊 `index.html` 檔案
3. 點擊右上角的「鉛筆」圖示（Edit this file）
4. 修改 code
5. 捲到最下方填寫 Commit message（例如：Update v5.3.3）
6. 點擊「Commit changes」
7. 等待 1-2 分鐘自動部署
8. 通知同事重新整理網頁即可看到更新

### 方法 B：上傳新檔案覆蓋

1. 在本地修改 `index.html`
2. 進入 GitHub Repository
3. 點擊 `index.html` 檔案
4. 點擊右上角「垃圾桶」圖示刪除舊檔案
5. Commit 刪除操作
6. 回到主頁，點擊「Add file」→「Upload files」
7. 上傳修改後的 `index.html`
8. 點擊「Commit changes」
9. 等待 1-2 分鐘自動部署完成

### 檢查部署狀態

1. 進入 Repository 的「Actions」頁籤
2. 查看最新的 workflow 是否完成（綠色勾勾）
3. 完成後網站即更新

**⚠️ 注意：** 更新後同事需要「強制重新整理」網頁才能看到最新版本
- Windows: `Ctrl + F5` 或 `Ctrl + Shift + R`
- Mac: `Cmd + Shift + R`

---

## 📱 使用方式

### 基本流程

1. 點擊或拖曳上傳圖片
2. 點擊「🚀 開始處理」
3. 查看結果，下載修正後的圖片

### 背景處理模式

結果區會顯示「背景處理模式」控制區：

- **智能模式（預設）：** 自動判斷是否延伸背景
- **📐 強制延伸：** 適合有底色背景的圖檔（如 Pantene）
- **🚫 不延伸：** 適合背景出現延展有誤的圖檔（如 Ariel 促銷標籤）

### 手動微調

點擊「🔧 微調」按鈕可以調整：
- 內容縮放：70-200%
- 留白距離：70-200px
- 輸出品質：70-100%

---

## 🛠️ 技術細節

- **前端框架：** 純 HTML/CSS/JavaScript
- **圖片處理：** Canvas API
- **儲存方式：** localStorage（瀏覽器本地）
- **支援格式：** JPG, PNG, GIF
- **輸出格式：** JPG
- **目標尺寸：** 1000×1000px

---

## 📊 版本記錄

### v5.3.2 (2026-01-11)
- ⚡ 優化內容縮放順暢度（CSS transform 即時預覽）
- 🎨 緊湊化背景處理模式控制區
- 💾 改善記錄持久化機制

### v5.3.1 (2026-01-11)
- ⚡ 滑桿順暢度優化（RAF + 節流 + 硬體加速）

### v5.3 (2026-01-11)
- 🎨 新增背景處理模式控制
- 📐 強制延伸/不延伸功能
- 🎯 智能邊緣偵測

---

## ❓ 常見問題

### Q: 為什麼圖片處理後背景不自然？
A: 使用「背景處理模式」切換延伸方式。有底色的圖片選「強制延伸」，有促銷標籤的選「不延伸」。

### Q: 如何批次處理多張圖片？
A: 一次上傳多張，點擊「開始處理」即可批次處理，最後可點「全部下載」。

### Q: 處理後的圖片在哪裡？
A: 點擊「💾 下載」按鈕，圖片會下載到瀏覽器預設的下載資料夾。

### Q: 可以在手機上使用嗎？
A: 可以！使用 GitHub Pages 網址在手機瀏覽器開啟即可。

### Q: 資料會上傳到伺服器嗎？
A: 不會！所有處理都在瀏覽器本地完成，圖片不會上傳。

---

## 📞 聯絡方式

如有問題或建議，請聯絡：
- **負責人：** Alishia
- **公司：** Starcom
- **專案：** P&G EC Media Campaigns

---

## 📄 授權

此工具為內部使用，請勿外傳。

---

**Made with ❤️ by Alishia @ Starcom**
