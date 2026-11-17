# 兆豐產物 資訊公開資料查詢

單檔網頁（`index.html`），不需要安裝或建置。內容：

- **業務概況**：各險別保費、自留、賠款、再保、準備金、損失率（112–114 年度），可選項目、折線圖、下載 Word / Excel
- **財務概況**：財務業務指標、資本適足性、115 年第 3 季指標
- **近三年概況**：整體業務概況 112–114 年度逐年比較

## 用 GitHub Pages 發布

1. 在 GitHub 建立新的 repository（例如 `megabank-insurance-viewer`）
2. 把 `index.html` 與 `README.md` 上傳到 repository 根目錄
3. 到 **Settings → Pages**，Source 選 **Deploy from a branch**，Branch 選 `main`、資料夾選 `/ (root)`，按 Save
4. 約 1–2 分鐘後，網址為 `https://<你的帳號>.github.io/<repository 名稱>/`

## 注意事項

- 網頁需要連網載入 JSZip、SheetJS（cdnjs），用來產生 Word / Excel 檔。
- 資料來源為金融監督管理委員會保險局「保險業公開資訊觀測站」。依該網站聲明，引用時請註明資料來源、確保資料完整、不得商業使用。
- GitHub Pages 發布後預設是公開網址；若資料只供內部組員使用，請改用私人 repository 搭配支援私人 Pages 的方案，或改以其他內部方式分享。

## 安全設計

- 頁面內建內容安全政策（CSP）：只允許頁面自己的程式與 cdnjs 的 JSZip、SheetJS 兩個函式庫，禁止其他來源的程式與任何對外連線。
- 若你修改 `index.html` 裡的 `<script>` 內容，需要重新計算 CSP 裡的 `sha256-…` 雜湊值，否則頁面會被瀏覽器擋住。
- 建議為兩個 cdnjs 函式庫加上 SRI（`integrity` 屬性）：到 cdnjs 網站複製該版本的 SRI 值，貼進對應的 `<script>` 標籤並加上 `crossorigin="anonymous"`。
