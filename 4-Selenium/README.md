# Selenium
[Chrome Options](#Chrome-Options) | [Webdriver 屬性與方法](#webdriver-屬性與方法) | [Webdriver 定位方法](#webdriver-定位方法) | [CSS Selector](#css-selector) | [Explicit Wait](#explicit-waits) | [實用補充](#實用補充)

### 安裝套件
```
pip install selenium
```

### 常用的套件
```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By

options = webdriver.ChromeOptions()
options.add_argument("--start-maximized") # Chrome 瀏覽器在啟動時最大化視窗
options.add_argument("--incognito") # 無痕模式
options.add_argument("--disable-popup-blocking") # 停用 Chrome 的彈窗阻擋功能。

service = Service('./chromedriver.exe')  # 請根據實際路徑修改
driver = webdriver.Chrome(service=service, options=options)

# 開啟網頁
driver.get("網頁 URL")
```

### Chrome driver download
[Chrome webdriver Link](https://developer.chrome.com/docs/chromedriver/downloads?hl=zh-tw)  

windows 指令下載 (記得修改使用的 Chrome 版本)
```bash
curl -L -o chromedriver.zip "https://storage.googleapis.com/chrome-for-testing-public/<version>/win64/chromedriver-win64.zip"
```

### Chrome Options
| 設定                                       | 說明          |
| ------------------------------------------ | ----------- |
| `add_argument("--headless")`               | 無介面模式       |
| `add_argument("--start-maximized")`        | 最大化視窗       |
| `add_argument(--window-size=1920,1080)`    | 指定視窗大小    |
| `add_argument("--incognito")`              | 無痕模式        |
| `add_argument("--no-sandbox")`             | （Linux 必要）  |
| `add_argument("--disable-popup-blocking")` | 禁止彈跳視窗封鎖    |
| `add_argument("--disable-dev-shm-usage")`  | 避免記憶體共享不足問題 |



### Webdriver 屬性與方法
| webdriver 屬性      | 說明                     |
|---------------------------|--------------------------|
| `current_url`               | 取得目前頁面的 URL       |
| `window_handles`             | 取得所有視窗代號        |
| `title`                     | 取得目前頁面的標題       |
| `page_source`               | 取得完整 HTML 原始碼     |


| webdriver 方法        | 說明                     |
|---------------------------|--------------------------|
| `get(url)`                  | 開啟指定頁面                |
| `refresh()`                    | 刷新頁面 |
| `quit()`                    | 關閉整個瀏覽器與驅動程式 |
| `execute_script(script)`    | 執行 JavaScript 程式碼    |
| `switch_to.window(handle)`   | 切換到指定視窗         |
| `save_screenshot(path)`     | 擷取整頁截圖             |
| `get_cookies()`             | 取得所有 cookie          |
| `add_cookie(cookie_dict)`   | 新增一筆 cookie          |


### Webdriver 定位方法
| 定位方法 | 說明 |
|-----|-----|
| `find_element(By.ID, 'id')`      | 透過元素的 id 屬性來定位元素。    |
| `find_element(By.NAME, 'name')`      | 透過元素的 name 屬性來定位元素。        |
| `find_element(By.CLASS_NAME, 'class_name')` | 透過元素的 class 屬性來定位元素。       |
| `find_element(By.TAG_NAME, 'tag_name')` | 透過元素的 tag 名稱來定位元素，例如 div, span, a 等。   |
| `find_element(By.LINK_TEXT, 'link_text')`    | 透過完全匹配的超連結來定位 `<a>` 元素。      |
| `find_element(By.PARTIAL_LINK_TEXT, 'partial')` | 透過部分匹配的超連結來定位 `<a>` 元素。    |
| `find_element(By.XPATH, 'xpath')`   | 透過 XPath 表達式來定位元素。適用於複雜的定位需求。     |
| `find_element(By.CSS_SELECTOR, 'selector')`     | 透過 CSS 選擇器來定位元素。   |

### CSS Selector
| 說明 | 範例 HTML + CSS    | Selenium 使用 |
|-----|--------------------| -------------- |
| 按 tag 名稱選擇    | `<input>` | `driver.find_element(By.CSS_SELECTOR, "input")` |
| 按 class 選擇    | `<button class="btn-primary">` | `driver.find_element(By.CSS_SELECTOR, ".btn-primary")` |
| 按 id 選擇       | `<div id="loginButton">` | `driver.find_element(By.CSS_SELECTOR, "#loginButton")` |
| 同時具有多個 class  | `<button class="btn btn-large">` | `driver.find_element(By.CSS_SELECTOR, ".btn.btn-large")`    |
| 後代元素（不限層級）    | `<div><input></input></div>` | `driver.find_element(By.CSS_SELECTOR, "div input")`  |
| 子元素（直接子節點）    | `<ul><li></li></ul>`  | `driver.find_element(By.CSS_SELECTOR, "ul > li")`  |
| 屬性精準匹配        | `<input type="text">`  | `driver.find_element(By.CSS_SELECTOR, 'input[type="text"]')`  |
| 屬性開頭為某字串（^=）  | `<a href="https://google.com">`  | `driver.find_element(By.CSS_SELECTOR, 'a[href^="https://"]')`  |
| 屬性結尾為某字串（$=）  | `<img src="icon.png">`  | `driver.find_element(By.CSS_SELECTOR, 'img[src$=".png"]')`                    |
| 屬性包含字串（*=）    | `<div class="box-search-area">` | `driver.find_element(By.CSS_SELECTOR, 'div[class*="search"]')` |
| 第 n 個元素       | `<ul><li></li><li></li><li></li></ul>` | `driver.find_element(By.CSS_SELECTOR, "ul li:nth-child(3)")` |
| 偶數 / 奇數       | `<tr></tr><tr></tr>…`  | `driver.find_element(By.CSS_SELECTOR, "tr:nth-child(even)")`  |
| 最後一個元素        | `<ul><li></li><li></li></ul>` | `driver.find_element(By.CSS_SELECTOR, "ul li:last-child")`  |
| 同層下一個元素（+）    | `<label></label><input>` | `driver.find_element(By.CSS_SELECTOR, "label + input")` |
| 同層後面所有兄弟（~）   | `<h2></h2><p></p><p></p>` | `driver.find_element(By.CSS_SELECTOR, "h2 ~ p")`  |
| 多條件 AND（同一元素） | `<input type="text" name="username">` | `driver.find_element(By.CSS_SELECTOR, 'input[type="text"][name="username"]')` |
| 多選擇器 OR（`,`）  | `<button class="btn-primary">…` 或 `<button class="btn-main">…`  | `driver.find_elements(By.CSS_SELECTOR,".btn-primary, .btn-main")`  |


### Explicit Waits
```python
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
favoritenumber = WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.CSS_SELECTOR, "span[id='favoritenumber']"))
).text
```

## 實用補充

### 實用 XPATH 用法
- 用文字內容查找元素： `//*[text()='台北市']`
- 找到父層元素： `//*[text()='台北市']/parent::*`


### 查看找到 element 的 HTML
```python
elem = driver.find_element(By.XPATH, "//*[text()='台北市']")
html = elem.get_attribute("outerHTML")
print(html)
```

### 實用 JS script
**下滑至頁面底部**
```javascript
window.scrollTo(0, docment.body.scrollHeight);
```
**開啟分頁**
```javascript
window.open('about:blank', '_blank');
```

