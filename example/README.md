# 📂 Example 實作範例

> 本資料夾收錄各章節技術的**完整實戰範例**，結合真實網站進行資料爬取

---

## 🗂️ 範例總覽

| 檔案 | 使用技術 | 目標網站 | 說明 |
|:---|:---:|:---|:---|
| [2-0_requests_with_cookie.ipynb](./2-0_requests_with_cookie.ipynb) | Requests + BeautifulSoup | PTT 八卦版 | 示範如何夾帶 Cookie 通過年齡驗證並解析頁面 |
| [2-1_yahoo_stock.ipynb](./2-1_yahoo_stock.ipynb) | Requests + BeautifulSoup | Yahoo 股市 | 爬取個股即時股價與相關資訊 |
| [2-2_line_stickers.ipynb](./2-2_line_stickers.ipynb) | Requests + BeautifulSoup | LINE Store | 解析貼圖資料並批次下載貼圖圖片至本地資料夾 |
| [4-1_twse_stock.ipynb](./4-1_twse_stock.ipynb) | Selenium + Bokeh | 台灣證券交易所 | 操控瀏覽器查詢多檔股票歷史均價並繪製互動圖表 |
| [4-2_line_movie.ipynb](./4-2_line_movie.ipynb) | Selenium + webdriver-manager | LINE TODAY | 模擬無限滾動載入，爬取所有上映中電影清單 |

---

## 📦 所需套件

```bash
pip install -r requirements.txt
```

| 套件 | 用途 |
|:---|:---|
| `requests` | 發送 HTTP 請求 |
| `beautifulsoup4` + `lxml` | 解析 HTML 頁面 |
| `selenium` | 自動化瀏覽器操作 |
| `webdriver-manager` | 自動管理 ChromeDriver 版本 |
| `bokeh` | 互動式資料視覺化 |

---

## 📝 範例說明

### 2-0 — PTT 夾帶 Cookie

PTT 八卦版需要通過年齡確認才能瀏覽，示範如何在 `selenium` 中帶入 `cookies` 參數驗證。

### 2-1 — Yahoo 股市個股資訊

對 Yahoo 股市頁面發送請求，使用 BeautifulSoup 定位股票名稱、即時股價等元素，示範如何應對動態 class 名稱的問題。

### 2-2 — LINE 貼圖下載器

從 LINE Store 貼圖商品頁面解析 `data-preview` JSON 屬性取得圖片 URL，並批次下載所有貼圖至本地資料夾。

### 4-1 — 台灣證交所歷史股價

使用 Selenium 操作瀏覽器查詢多檔 ETF 的每月歷史均價，將資料整理後使用 Bokeh 繪製多線互動折線圖。

### 4-2 — LINE TODAY 電影清單

以 `webdriver-manager` 自動管理 ChromeDriver，模擬無限滾動直到頁面不再新增內容，完整爬取所有上映中電影。
