# 🌐 Requests

> 使用 Python 發送 HTTP 請求、呼叫 API 並處理伺服器回應

---

## 📦 安裝套件

```bash
pip install requests
```

---

## 📋 Requests 參數

| 常用 | 參數 | 功能 |
|:---:|:---------:|:-----|
| ✅ | `url` | 請求的 URL |
| ✅ | `params` | URL 查詢參數，通常是一個字典 |
| ✅ | `data` | POST 請求的數據，通常是一個字典 |
| ✅ | `json` | JSON 格式的請求數據 |
| ✅ | `headers` | HTTP 標頭，通常是一個字典 |
| | `cookies` | 要發送的 Cookie |
| | `auth` | 認證信息，通常是元組（用戶名, 密碼）|
| | `timeout` | 等待服務器響應的時間，單位是秒 |
| | `allow_redirects` | 是否允許重定向（默認為 True）|
| | `proxies` | 字典，指定代理伺服器 |
| | `files` | 文件上傳，通常是字典 |
| | `stream` | 是否流式傳輸響應內容（默認為 False）|
| | `verify` | 是否驗證服務器的 SSL 證書（默認為 True）|
| | `cert` | 客戶端證書檔案的路徑 |

---

## 📨 Response 屬性

| 常用 | Response 屬性 | 說明 |
|:---:|:-------------:|:-----|
| ✅ | `json()` | 直接將回傳內容轉成 Python 字典（若是 JSON）|
| ✅ | `status_code` | 伺服器回傳的 HTTP 狀態碼 |
| ✅ | `text` | 回傳內容的文字（自動解碼）|
| | `content` | 回傳的原始二進位資料（bytes）|
| | `headers` | 回傳的 HTTP 標頭（為字典格式）|
| | `cookies` | 伺服器設置的 cookie |
| | `url` | 最終的請求 URL（可能經過重導向）|
| | `encoding` | 文字解碼使用的編碼（可自行修改）|
| | `reason` | 狀態碼的文字描述（如 OK、Not Found）|
| | `elapsed` | 請求花費的時間（`datetime.timedelta`）|

---
