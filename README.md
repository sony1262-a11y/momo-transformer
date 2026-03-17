# MOMO 廣告圖修正器 v6.3 更新記錄

## 版本資訊
- **版本**：v6.3
- **更新日期**：2026-03-17
- **基於版本**：v6.2

---

## UI 設計重構

### Header
- 背景從黑底改為暖白底（`#FFF8F0`），脫離深色風格
- STARCOM label 改為橘黃色，與整體暖色調一致
- 標題「修正器」改為紅色點綴
- 版本 badge 改為方形＋黑色陰影風格
- 右側副標文字顏色跟隨暖色調調整

### Feature Strip（功能圖示列）
- 圖示改為手繪 SVG 風格，取代原有 emoji
- 排版從橫排改為垂直排列（圖示在上、文字在下）
- 黃底條帶改為置中卡片（不貼滿瀏覽器邊緣），加圓角＋黑色邊框＋陰影
- 上下加入黑線邊界，與 header 和主內容區產生層次

### Footer
- 從黑底改為暖白底，與 header 呼應
- 文字顏色跟隨整體色調調整

### 處理選項區（Task Grid）
- Checkbox 選中狀態統一：黑框＋淡黃底（所有選項一致）
- 格式轉換格底色與其他選項統一（米白），不再特殊標示

### 結果卡片
- 新增「已執行項目」橫排清單，位置在變身前後對比圖和縮放數據之間
- 每個項目兩字換行（尺寸／校正），格式整齊
- 左側黑框方形（✓ 黃字 / — 灰色），右側項目名稱

---

## 功能新增

### 格式轉換（真正可控）
- 輸入支援擴充：JPG、PNG、GIF、WebP、BMP 等
- 格式轉換 checkbox 現在真正接上處理邏輯
  - **勾選**：輸出 JPG，檔名附 `.jpg`
  - **不勾選**：保留原始格式輸出（PNG），檔名保留原副檔名
- 廣告圖（`taskFormat`）與專推圖（`promoTaskFormat`）各自獨立控制

### 背景處理模式與微調的條件顯示
- 只在勾選「尺寸校正」或「內容修正」其中之一時才顯示
- 兩者都未勾選時隱藏，下載按鈕撐滿全寬並置中

### 防呆機制
- 已執行項目清單依實際 checkbox 狀態顯示（✓ / —），不再寫死
- 格式轉換項目同步反映勾選狀態

---

## Bug 修復

### 強制延伸 / 不延伸按鈕無反應
- **根本原因**：iframe 環境下 `confirm()` / `prompt()` 被瀏覽器靜默封鎖
- **修復**：全站移除 `confirm()` / `prompt()`，改為直接執行並以按鈕狀態（「⏳ 處理中...」）提供回饋
- 同步移除：`removeResult`、`downloadAll`、`reportSuccess` 的 confirm

### 失敗回報改為 inline 輸入
- 原本使用 `prompt()` 輸入失敗原因，同樣會被 iframe 封鎖
- 改為在卡片內展開 inline 輸入框，點送出後顯示記錄確認

### 尺寸校正模式強制延伸無效
- **根本原因**：只勾尺寸校正時走 `content === false` 快速路徑，`forceEdgeExtension` 沒被讀取
- **修復**：快速路徑加入判斷，當 `forceEdgeExtension` 有值時改走完整延伸路徑

### content===false 路徑缺少必要欄位
- 補上 `originalImage`、`beforeDataUrl`、`beforeSize`，確保強制延伸能正確存取原始圖片

---

## 技術細節

### sanitizeFilename 更新
```javascript
// 新增 toJpg 參數，不轉格式時保留原副檔名
function sanitizeFilename(filename, toJpg = true)
```

### forceJpgExt helper
```javascript
// 新增：僅轉換副檔名，不做其他處理
function forceJpgExt(filename)
```

### transformImage / processPromoImage
- 所有 `toDataURL` 改為依 `params.format` 決定 `image/jpeg` 或 `image/png`

### result.tasks 結構
```javascript
// 廣告圖
{ resize, filename, content, compress, format }

// 專推圖
{ resize, filename, compress, format }
```
