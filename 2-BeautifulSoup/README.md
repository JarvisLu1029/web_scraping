# 🍜 BeautifulSoup

> 解析 HTML / XML 文件，從網頁中定位並提取所需資料

---

## 📦 安裝套件

```bash
pip install bs4 lxml
```

---

## 🔧 方法（Methods）

| 方法 | 說明 |
|:---|:---|
| `.find()` | 搜尋並返回第一個匹配指定標籤名稱的元素。如果找不到，返回 None。 |
| `.find_all()` | 搜尋並返回所有匹配指定標籤名稱的元素，返回值為一個列表。 |
| `.select()` | 根據 CSS 選擇器來選取所有匹配的元素 |
| `.select_one()` | 根據 CSS 選擇器來選取第一個匹配的元素 |
| `.get_text()` | 獲取元素內的所有文字內容，返回值為一個字符串。|

---

## 🏷️ 屬性（Attributes）

| 屬性 | 說明 |
|:---|:---|
| `.attrs` | 獲取元素的所有屬性，返回值為一個字典。|
| `.parent` | 獲取當前元素的父元素。|
| `.children` | 以生成器形式獲取當前元素的所有子元素。|
| `.descendants` | 以生成器形式獲取當前元素的所有子孫元素。|
| `.previous_sibling` | 獲取當前元素的前一個兄弟元素。|
| `.next_sibling` | 獲取當前元素的下一個兄弟元素。|
| `.previous_element` | 獲取文檔中當前標籤的上一個元素。|
| `.next_element` | 獲取文檔中當前標籤的下一個元素。|

---

## 🎨 CSS Selector 使用方式

搭配 `.select()` / `.select_one()` 使用：

| 說明 | CSS Selector | 範例 |
|:---|:---|:---|
| 按 tag 名稱選擇 | `tag` | `soup.select("p")` |
| 按 class 選擇 | `.class` | `soup.select(".title")` |
| 按 id 選擇 | `#id` | `soup.select_one("#main")` |
| 同時具有多個 class | `.class1.class2` | `soup.select(".btn.btn-large")` |
| 後代元素（不限層級） | `parent descendant` | `soup.select("div p")` |
| 子元素（直接子節點） | `parent > child` | `soup.select("ul > li")` |
| 屬性精準匹配 | `[attr="value"]` | `soup.select('input[type="text"]')` |
| 屬性開頭為某字串（^=） | `[attr^="value"]` | `soup.select('a[href^="https://"]')` |
| 屬性結尾為某字串（$=） | `[attr$="value"]` | `soup.select('img[src$=".png"]')` |
| 屬性包含字串（*=） | `[attr*="value"]` | `soup.select('div[class*="search"]')` |
| 第 n 個子元素 | `:nth-of-type(n)` | `soup.select("ul li:nth-of-type(2)")` |
| 最後一個子元素 | `:last-of-type` | `soup.select("ul li:last-of-type")` |
| 多選擇器 OR（`,`） | `sel1, sel2` | `soup.select("h1, h2, h3")` |
| 同層緊接下一個元素（+） | `prev + next` | `soup.select("label + input")` |
| 同層後面所有兄弟（~） | `prev ~ sibling` | `soup.select("h2 ~ p")` |

---

