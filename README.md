# 劉昭佑 LINE 電子名片

資料夾內容
- index.html：LINE 傳名片頁面（用 LIFF 選好友，送出名片圖卡）
- card.html：點「看電子名片」會開的互動名片（開門動畫、翻面、QR Code）
- photo.jpg：名片圖卡上的照片
- qrcode.js：card.html 背面 QR Code 用的程式庫

## 設定步驟

1. 部署：把整個資料夾部署到 Vercel，在資料夾裡執行 `vercel --prod`，記下網址，例如 https://liu-card.vercel.app
2. 建 LINE Login channel：到 https://developers.line.biz/console/
   - 建一個 Provider，名字隨意，例如「劉昭佑」
   - Create a new channel → 選 LINE Login
   - App types 勾 Web app；Region 選台灣
   - Channel name 不能有「LINE」字樣，例如「劉昭佑電子名片」
3. 加 LIFF：進入這個 channel → LIFF 分頁 → Add
   - Size：Full
   - Endpoint URL：第 1 步的網址（https://…vercel.app/）
   - Scopes：勾 profile、openid
   - Add friend option：Off
   - 建好後打開 shareTargetPicker 開關（要先同意條款）
   - 記下 LIFF ID，長得像 2001234567-AbCdEfGh
4. 填 LIFF ID：打開 index.html，找到這一行，換成你的 LIFF ID，再執行一次 `vercel --prod`
       const LIFF_ID = '請填入LIFF_ID';
5. 發布 channel：channel 名稱旁的「Developing」→ 點 Publish，改成 Published
   還在 Developing 時只有你自己能用，客人按「轉傳這張名片」會失敗
6. 使用：在手機 LINE 打開 https://liff.line.me/你的LIFF_ID → 選好友 → 送出
   建議把這個連結傳到自己的 Keep 筆記或釘選起來，以後一點就能發

## 想改名片內容
- 圖卡文字、按鈕：index.html 裡的 card() 那一段
- 互動名片：card.html
