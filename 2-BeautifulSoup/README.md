# BeautifulSoup
### 安裝套件
```
pip install bs4 lxml
```

### BeautifulSoup Method / Attribute
| 方法 | 說明 |
|:---|:---|
| `.find()`         | 搜尋並返回第一個匹配指定標籤名稱的元素。如果找不到，返回 None。 |
| `.find_all()`     | 搜尋並返回所有匹配指定標籤名稱的元素，返回值為一個列表。 |
| `.select()`       | 根據 CSS 選擇器來選取所有匹配的元素 |
| `.select_one()`   | 根據 CSS 選擇器來選取第一個匹配的元素 |
| `.get_text()`     | 獲取元素內的所有文字內容，返回值為一個字符串。|


| 屬性 | 說明 |
|:---|:---|
| `.attrs`              | 獲取元素的所有屬性，返回值為一個字典。|
| `.parent`             | 獲取當前元素的父元素。|
| `.children`           | 以生成器形式獲取當前元素的所有子元素。|
| `.descendants`        | 以生成器形式獲取當前元素的所有子孫元素。|
| `.previous_sibling`   | 獲取當前元素的前一個兄弟元素。|
| `.next_sibling`       | 獲取當前元素的下一個兄弟元素。|
| `.previous_element`   | 獲取文檔中當前標籤的上一個元素。|
| `.next_element`       | 獲取文檔中當前標籤的下一個元素。|
