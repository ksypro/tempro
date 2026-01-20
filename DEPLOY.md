# GitHub Pages 部署指南

## 📋 前置準備

### 1. 確保所有檔案完整

您的專案需要包含以下檔案：
- ✅ `index.html` - 主頁面
- ✅ `manifest.webmanifest` - PWA 設定檔
- ✅ `sw.js` - Service Worker（離線支援）
- ⚠️ `icons/` 資料夾（如果 manifest 中有引用）

**注意**：如果您的 `manifest.webmanifest` 和 `sw.js` 中引用了 `icons/icon-192.svg` 和 `icons/icon-512.svg`，請確保這些檔案存在，否則 PWA 功能可能無法正常運作。

## 🚀 部署步驟

### 方法一：使用 GitHub 網頁介面（最簡單）

1. **建立 Repository**
   - 前往 [GitHub](https://github.com)
   - 點擊右上角 `+` → `New repository`
   - 輸入 Repository 名稱（例如：`rap-flow-coach`）
   - 選擇 `Public`（GitHub Pages 免費版需要 Public）
   - **不要**勾選 "Initialize this repository with a README"
   - 點擊 `Create repository`

2. **上傳檔案**
   - 在新建的 repository 頁面，點擊 `uploading an existing file`
   - 將專案資料夾中的所有檔案拖曳到頁面
   - 在下方輸入 Commit message（例如：`Initial commit`）
   - 點擊 `Commit changes`

3. **啟用 GitHub Pages**
   - 在 repository 頁面，點擊 `Settings`（設定）
   - 在左側選單找到 `Pages`
   - 在 `Source` 區塊：
     - 選擇 `Deploy from a branch`
     - Branch 選擇 `main`（或 `master`）
     - Folder 選擇 `/ (root)`
   - 點擊 `Save`
   - 等待幾分鐘，GitHub 會顯示您的網站網址

4. **訪問您的網站**
   - 網址格式：`https://[您的用戶名].github.io/[repository名稱]`
   - 例如：`https://yourusername.github.io/rap-flow-coach`

### 方法二：使用 Git 命令列（進階）

1. **初始化 Git**
   ```bash
   cd d:\cursor
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **連接到 GitHub**
   ```bash
   git remote add origin https://github.com/[您的用戶名]/[repository名稱].git
   git branch -M main
   git push -u origin main
   ```

3. **啟用 GitHub Pages**
   - 按照方法一的步驟 3 啟用 GitHub Pages

## ⚙️ 設定 HTTPS（重要）

GitHub Pages 預設使用 HTTPS，這對於 Service Worker 和 PWA 功能是必需的。確保：
- ✅ Repository 設定為 Public
- ✅ GitHub Pages 已啟用
- ✅ 使用 `https://` 開頭的網址訪問

## 🔧 疑難排解

### Service Worker 無法註冊
- 確保使用 HTTPS（GitHub Pages 預設提供）
- 檢查 `sw.js` 檔案路徑是否正確
- 檢查瀏覽器控制台是否有錯誤訊息

### 圖示無法顯示
- 確保 `icons/` 資料夾存在
- 檢查 `manifest.webmanifest` 中的圖示路徑是否正確
- 圖示檔案必須存在於 repository 中

### 更新後看不到變更
- GitHub Pages 更新可能需要幾分鐘
- 清除瀏覽器快取
- 在 Service Worker 中更新 `CACHE_VERSION`

## 📝 更新專案

每次修改後，重新上傳檔案或使用 Git push：

```bash
git add .
git commit -m "更新說明"
git push
```

GitHub Pages 會自動重新部署（通常需要 1-2 分鐘）。

## 🌐 自訂網域（選用）

如果您有自己的網域，可以在 GitHub Pages 設定中：
1. 前往 Settings > Pages
2. 在 `Custom domain` 區塊輸入您的網域
3. 按照指示設定 DNS 記錄

---

**祝您部署順利！** 🎉
