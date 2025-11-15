# PyAutoGUI
### 安裝套件
```
pip install pyautogui keyboard
```

### 🖥 系統資訊

| 方法 | 回傳 | 說明 |
| ---------------- | -------- | -------- |
| `size()`         | `(w, h)` | 目前主桌面解析度 |
| `position()`     | `(x, y)` | 目前滑鼠座標   |
| `onScreen(x, y)` | `bool`   | 座標是否在螢幕內 |


### 🖱 滑鼠動作

| 方法 | 說明 |
| ------- | ------ |
| `moveTo(x, y, duration)`                | 移動到絕對座標        |
| `moveRel(xOffset, yOffset, duration)`   | 相對移動           |
| `click(x, y, clicks, interval, button)` | 點擊（可指定座標／次數／鍵） |
| `doubleClick()` / `rightClick()`        | 快捷點擊           |
| `dragRel(x, y, duration, button)`       | 把滑鼠「從目前位置拖曳某段距離」|
| `dragTo(x, y, duration, button)`        | 把滑鼠「拖曳到座標」     |
| `scroll(clicks)`                        | 滑鼠滾輪（上正下負）     |


### 📸 螢幕與影像偵測

| 方法 | 主要參數 | 回傳 | 說明 |
| ---------- | ------------- | -------------- | --------- |
| `screenshot(path=None, region=None)`      | `path: str, region: (x, y, w, h)` | `PIL.Image`    | 全螢幕或區域截圖，`region` 為 (左上 x, 左上 y, 寬, 高) |
| `locateOnScreen(image, confidence=None)`       | `confidence: float(<1)` | `Box` 或 `None` | 螢幕上尋找**第一個**匹配的位置（需要安裝 OpenCV 才可用 `confidence`） |
| `locateAllOnScreen(image, confidence=None)`    | `confidence: float(<1)` | 迭代器          | 尋找**所有**匹配的位置，回傳一個可迭代的 Box 序列 |
| `locateCenterOnScreen(image, confidence=None)` | `confidence: float(<1)` | `(x, y)` 或 `None`       | 找到第一個匹配區域的**中心點座標** |
| `pixel(x, y)` | `x: int, y: int` | `(R, G, B)` | 取得指定螢幕座標像素的實際顏色 |
| `pixelMatchesColor(x, y, (R, G, B), tolerance=0)` | `x: int, y: int, (R, G, B), tolerance: int` | `bool` | 檢查某座標點顏色是否與指定 RGB 相同（可用 `tolerance` 允許誤差） |

### ⌨️ 鍵盤動作

| 方法                          | 主要參數 | 回傳 | 說明 |
| ----------------------------- | ------------ | ------ | ----------- |
| `write(text, interval)`       | `str, float` | `None` | 模擬輸入文字      |
| `press(key)`                  | `str`        | `None` | 單鍵（如 enter） |
| `keyDown(key)` / `keyUp(key)` | `str`        | `None` | 按下／放開       |
| `hotkey(*keys)`               | 多鍵         | `None` | 組合鍵（順序處理）   |
