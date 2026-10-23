# Volley 3D Mobile — 手機單機 2v2 AI 排球原型

## 手機遊玩方式

這是手機瀏覽器 3D 遊戲原型，不是 App Store 安裝檔。建議使用 iPhone Safari 或 Android Chrome，**把手機橫向拿**；直向畫面也可使用，但球場較小。

`index.html` 是遊戲網頁。要在手機穩定開啟，請**先將它發布到 HTTPS 靜態網站**（GitHub Pages、Cloudflare Pages 或類似服務），再用手機瀏覽器開啟發布網址。從 iPhone「檔案」直接預覽 HTML 不一定會執行 JavaScript / WebGL。

### 只用手機發布：GitHub Pages 範例

1. 從聊天下載 ZIP，在 iPhone「檔案」App 解壓縮。
2. 用 Safari 登入 GitHub，建立新的公開 repository（如 `volley-mobile`）。
3. 透過 GitHub 網站的 **Add file → Upload files** 上傳解壓縮後的 `index.html`，放在 repository 根目錄；若手機版選單找不到，可在 Safari 要求桌面版網站。
4. 進入 repository **Settings → Pages**，在 **Build and deployment** 選 **Deploy from a branch**，選 `main` / `(root)` 後儲存。
5. 等 GitHub Pages 部署完成，以 Pages 顯示的公開網址在手機 Safari 開啟，並將手機轉橫向。

需要網路連線，遊戲的 Three.js 3D 引擎會由固定版本的 CDN 載入。遊戲本身在瀏覽器執行，不需要多人配對伺服器、登入或資料庫。

## 觸控操作

- 左下虛擬搖桿：自由移動
- 右下「接球」：接球或傳球
- 右下「托球」：托球給隊友
- 右下「扣殺」：**按住蓄力，放開擊球**
- 右下「跳躍」：跳躍 / 嘗試攔網
- 動作按鈕上方滑桿：調整扣球目標方向
- 頂部「暫停」、「重來」：暫停與重設比分
- 接球輔助：距球夠近時幫忙微調站位，適合雙指觸控；建議動作會有黃色外框

## 遊戲內容

- 第三人稱 3D 球場、球網、4 名簡化卡通角色和排球
- 玩家 1 名 + AI 隊友 1 名，對陣 2 名 AI
- 球體重力、擊球拋物線、碰網、落地得分、簡化的每隊最多三次觸球規則
- AI 預測球體落點，嘗試接球、托球、扣殺、攔網
- 先得 11 分且領先至少 2 分獲勝

## 開發者本地預覽（非手機必須）

```bash
python -m http.server 8000
```

之後使用瀏覽器開啟 `http://localhost:8000`。

## 目前限制

- 這是 **V1 玩法原型**，不是完成的商業遊戲；角色模型、動畫、碰撞與 AI 都是簡化版。
- 無多人即時連線、後端伺服器、帳號或資料庫。
- 尚未在實體 iPhone / Android 裝置上完成完整 WebGL 畫面與效能測試；已完成 JS 語法檢查、模擬觸控與橫直向介面流程測試。
- Three.js 由 CDN 載入；因此這個 ZIP 不是完全離線的獨立遊戲。
