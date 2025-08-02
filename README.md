ETtoday AI 新聞小幫手
這是一個基於 Node.js (Express) 後端和 React 前端構建的 AI 新聞處理平台。它利用 Google Gemini API 和 YouTube Data API 提供多種新聞相關的 AI 功能。

功能列表
新聞網址 AI 改寫： 從給定網址抓取新聞內容並進行專業改寫，生成長短標題。

通稿改寫： 將用戶提供的原始通稿內容進行改寫，並生成新的長短標題。

外電新聞翻譯與改寫： 自動翻譯外電新聞內容為繁體中文，並進行專業改寫，生成長短標題。

訪問內容生成新聞稿： 根據訪問內容生成專業新聞稿，可自訂長度、段落和語氣。

名人社群文章轉新聞： 將名人社群貼文內容轉換為新聞稿，並生成標題。

YouTube 連結轉新聞： 從 YouTube 影片連結提取資訊（標題、描述、逐字稿），並生成新聞稿及標題。（此功能目前為「開發中請稍待」狀態）

錯字校正與語法檢查： 檢查文本中的錯字、語法和標點符號錯誤，並提供修正建議。

AI 聊天室： 與 AI 進行日常對話，獲取即時幫助或資訊（需要 Firebase Firestore 支援）。

環境要求
Node.js (建議 v18 或更高版本)

npm (Node Package Manager)

Google Gemini API 金鑰

Google YouTube Data API 金鑰 (如果需要 YouTube 相關功能)

Ngrok 執行檔 (用於本地測試和外部訪問)

安裝與啟動步驟
請按照以下步驟在本地環境中設置並運行專案：

1. 克隆或下載專案
如果您尚未下載專案，請先獲取專案檔案。

2. 配置環境變數
在專案的根目錄下，創建一個名為 .env 的檔案（如果它不存在）。
將您的 Google Gemini API 金鑰和 Google YouTube Data API 金鑰填入其中：

GEMINI_API_KEY=YOUR_GEMINI_API_KEY_HERE
YOUTUBE_API_KEY=YOUR_YOUTUBE_API_KEY_HERE

請將 YOUR_GEMINI_API_KEY_HERE 和 YOUR_YOUTUBE_API_KEY_HERE 替換為您真實的 API 金鑰。

3. 安裝 Node.js 依賴項 (非常重要！)
打開您的 VS Code 終端機，導航到專案的根目錄：

cd /Users/xuyiqun/Desktop/ai_news_platform # 替換為您實際的專案路徑

然後運行以下命令安裝所有必要的 Node.js 模組：

npm install

這一步會下載所有必要的函式庫，確保前端和後端程式碼都能正常運行。

4. 啟動後端伺服器
在同一個終端機分頁中，運行以下命令啟動後端服務：

npm start

您應該會看到類似以下訊息：

後端伺服器運行在 http://localhost:3000
現在可以打開 http://localhost:3000/ 來使用網頁。

請保持這個終端機分頁開啟，不要關閉它。

5. 啟動 Ngrok 隧道 (用於外部訪問)
如果您希望外部網路可以訪問您的本地網頁，請使用 Ngrok。

a. 下載 Ngrok 執行檔：
前往 https://ngrok.com/download 下載適合您作業系統的 Ngrok。
將下載的 ngrok 執行檔放在一個您容易找到的資料夾，例如 ~/Downloads。

b. 賦予 Ngrok 執行權限：
打開一個新的終端機分頁 (在 VS Code 終端機視窗上方點擊 + 號)。
導航到您存放 ngrok 執行檔的資料夾（例如 ~/Downloads）：

cd ~/Downloads

然後執行以下命令：

chmod +x ngrok

c. 配置 Ngrok Authtoken：
前往 https://dashboard.ngrok.com/get-started/your-authtoken 登入並複製您的 Authtoken 命令（例如 ngrok config add-authtoken <YOUR_AUTHTOKEN_HERE>）。
在同一個 Ngrok 終端機分頁中，執行以下命令（請替換為您的真實 Authtoken）：

./ngrok config add-authtoken YOUR_AUTHTOKEN_HERE

您應該會看到 Authtoken saved to configuration file:... 的訊息。

d. 啟動 Ngrok 隧道：
在同一個 Ngrok 終端機分頁中，執行以下命令：

./ngrok http 3000

您會看到 Ngrok 介面顯示一個 Forwarding 網址（例如 https://abcdef12345.ngrok-free.app）。

6. 訪問您的應用程式
本地訪問： 在您的瀏覽器中打開 http://localhost:3000/。您應該會看到新聞小幫手的前端介面。

外部訪問： 將 Ngrok 提供的 Forwarding 網址（例如 https://abcdef12345.ngrok-free.app）分享給您的同事。他們就可以透過這個網址訪問您的應用程式了。

注意事項
保持運行： 啟動後端伺服器和 Ngrok 的兩個終端機分頁都必須保持開啟，否則應用程式將無法訪問。

Ngrok 網址： 免費版 Ngrok 每次重新啟動都會生成新的 Forwarding 網址。

API 金鑰： 確保您的 .env 檔案中的 API 金鑰是正確且有效的。