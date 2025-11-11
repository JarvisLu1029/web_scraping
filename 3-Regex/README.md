# Regex
> [!NOTE]
> 可以使用該網站練習、撰寫 Regex
> https://regex101.com/

### 基礎字元 (Character Classes)
| 說明 | 正規表達式 | 範例 |
|------|-------------|------|
| 一個字元: a、b or c | `[abc]` | `abc`def |
| 一個字元，除了: a、b or c | `[^abc]` | abc`def` |
| 一個字元，在某個範圍內: a-z | `[a-z]` | `abcd`XYZ0123 |
| 一個字元，不在某個範圍內: a-z | `[^a-z]` | abcd`XYZ0123` |
| 一個字元，在某個範圍內: a-z or A-Z | `[a-zA-Z]` | `abcdXYZ`0123 |
| 任何單一字元 | `.` | 任何字元 |
| 任何空白字元 ( \f\r\n\t\v ) | `\s` | 空格、換行、換頁等 |
| 任何非空白字元 ( 不是 \f\r\n\t\v ) | `\S` | 非空格、非換行、非換頁等 |
| 任何數字 | `\d` | `10`ab |
| 任何非數字 | `\D` | 10`ab` |
| 任何文字字元 | `\w` | `10ab`/\*AZ^$ |
| 任何非文字字元 | `\W` | 10ab`/\*AZ^$` |
| 避開特殊字元 | `\` <br>ex. `\.tw` | xxx_tw@yahoo.com`.tw` |

### 數量限定符 (Quantifiers)
| 說明 | 正規表達式 | 範例 |
|------|-------------|------|
| 0個或1個 d | `ad?` | `ad`db`eeea`ccb`aa` |
| 0個或更多 d | `ad*` | `addb`eeea`accb`aa |
| 1個或更多的 a | `a+` | `aaa`, `aabbb`aaa |
| 完整 3 個 a | `a{3}` | a, `aaa`, aabaaa, `aaaaa` |
| 3 個以上的 a | `a{3,}` | aa, `aaa`, aabaaa, `aaaaa` |
| 3 個到 6 個之間的 a | `a{3,6}` | a, `aaaaa`, aa, `aaaaaa`aa |

### 位置匹配 (Anchors & Boundaries)
| 說明 | 正規表達式 | 範例 |
|------|-------------|------|
| 字串的開始 | `^` <br>ex. `^Chainsaw` | `Chainsaw` let devil saw  |
| 字串的結束 | `$` <br>ex. `saw$` | Chainsaw let devil `saw` |
| 位於文字邊界的字元 | `\b` <br>ex. `\bis` | My name `is` Jarvis Lu|
| 非位於文字邊界的字元 | `\B` <br>ex. `\Bis` | My name is Jarv`is` Lu|

### 群組與選擇 (Groups & Alternation)
| 說明 | 正規表達式 | 範例 |
|------|-------------|------|
| 配對 a 或 b | `a\|b` | `a`ddb`eeea`ccb`a` |
| 以群組的方式配對，同時捕捉被配對的資料 | `( ... )`<br>Ex: `(1[0-9]{3}\|20[0-9]{2})` | `1992`, 4096, `2019`, 3000,<br>`1789`, `1776`, `1024`, 8192 |
| 配對卻不在群組裡顯示 | `Denji (?:Pochita)` | `Denji Pochita`, Denji Makima |

### 環視 (Lookaround Assertions)
| 說明 | 正規表達式 | 範例 |
|------|-------------|------|
| 正向環視<br>（這位置右邊要出現什麼） | `Denji(?= Pochita)` | `Denji` Pochita, Denji Makima |
| 負向環視<br>（這位置右邊不能出現什麼） | `Denji(?! Pochita)` | Denji Pochita, `Denji` Makima |
| 正向回顧<br>（這位置左邊要出現什麼） | `(?<=Denji) Pochita` | Denji `Pochita`, Denji Makima |
| 負向回顧<br>（這位置左邊不能出現什麼） | `(?<!Denji) Pochita` | Denji Pochita, Makima `Pochita` |

### Python 使用 Regex
|函式|用途|回傳類型|
| --- | --- | --- |
|`re.match()`|從字串開頭開始比對|Match 物件或 None|
|`re.search()`|搜尋整個字串，只找到第一個符合的|Match 物件或 None|
|`re.findall()`|回傳所有符合的結果|	list
|`re.sub()`|取代符合的部分	|str|
