# 部署到 Cloudflare Pages（手機預覽測試）

要發佈的內容＝`prototype/` 資料夾（純靜態：`index.html` + `assets/` + `獎項一覽表.csv`）。
唯一外部連線是 Google Fonts，手機有網路即可正常顯示。

---

## 方法 A：儀表板拖拉上傳（最簡單，不用安裝任何東西）

1. 登入 https://dash.cloudflare.com
2. 左側 **Workers & Pages** → **Create** → 選 **Pages** 分頁 → **Upload assets**
3. 專案名稱填 `intercoins-lite`（或任意）
4. 把 **`prototype` 資料夾裡的內容**（index.html、assets、csv）拖進上傳區
   —— 重點：要讓 `index.html` 在**根目錄**（不是再包一層 prototype）
5. 按 **Deploy** → 得到網址 `https://intercoins-lite.pages.dev`
6. 手機瀏覽器（或 LINE）開這個網址即可測試

之後要更新：同專案再 **Create new deployment** 重新上傳即可，網址不變。

---

## 方法 B：指令部署（wrangler，更新最快）

```bash
cd /Users/jamietsai/Desktop/20260713_洲遊幣Lite
npx wrangler login          # 開瀏覽器授權你的 Cloudflare 帳號（只需一次）
npx wrangler pages deploy prototype --project-name=intercoins-lite
```

- 完成後終端機會印出 `https://intercoins-lite.pages.dev`
- 之後每次更新只要再跑最後一行，URL 不變

---

## 想讓我直接幫你部署？

在這台終端機先 `npx wrangler login` 登入好，或設定有 Pages 編輯權限的 token：

```bash
export CLOUDFLARE_API_TOKEN=你的token
```

設定好後跟我說一聲，我就能直接執行 `npx wrangler pages deploy prototype ...` 幫你發佈。

---

## LINE LIFF 用途提醒
- 目前金幣已改為純 CSS 3D（無 WebGL、無 CDN 依賴），LIFF／各種手機都穩定。
- 若要正式放進 LINE LIFF，於 LINE Developers 建 LIFF app，Endpoint URL 填上面的 Pages 網址即可。
