# 1120_ruby_day8

[![hackmd-github-sync-badge](https://hackmd.io/WgspogPORnqDeC5PcFPk3Q/badge)](https://hackmd.io/WgspogPORnqDeC5PcFPk3Q)

---
#### 上課日期：1120
###### tags: `ruby`
###### tags: `5xruby`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)


---
# 0. 綱要/目錄
- [ ] 1. Rails專案(續)
- [ ] 2. 資安
- [ ] 3. AJAX與turbolinks




---
# 1. Rails專案（續）
#### 新增選單列選項
- 在右上角加上「登入」和「註冊」
- 怎麼做？要在哪裡修改？
1. _navbar.html.erb
		- 新增選項
```htmlmixed=
  <ul>
    <li><%= link_to "註冊", '#' %></li>
    <li><%= link_to "登入", '#' %></li>
  </ul>
```
-
2. routes.rb
` get 'user/login', to: 'users#login'`

#### redis 

##### validates

##### 名稱與路徑
- 設定時，不同的名稱可以有相同的考量
- 新增borad的方法，也可以套用在user上面


##### 正規表示式
- 也叫常規表示式/正規表達式
- 找出訊息的通則
- [rubular](https://rubular.com/):ruby專用 
- 範例：
```ruby	
  validates :email,format: { with: /[\w]+@([\w-]+\.)+[\w-]{2,4}/ }
```
> email的正規表示法

##### 有session不代表有登入


---

##### [麵條式代碼](https://zh.wikipedia.org/zh-tw/%E9%9D%A2%E6%9D%A1%E5%BC%8F%E4%BB%A3%E7%A0%81)
- 「指一個原始碼的控制流程複雜、混亂而難以理解，尤其是用了很多GOTO、例外、執行緒、或其他無組織的分支。其命名的原因是因為程式的流向就像一盤面一樣的扭曲糾結。」
- 常見於php


---
# 2. 資安
- 可以[查詢密碼]的網站就是沒有加密
##### 參考網站：[我的網站沒加密](https://plainpass.com/) [FB](https://www.facebook.com/PlainPass)


##### 加密
- 不要用md5
- 可用[sha1](https://zh.wikipedia.org/wiki/SHA-1)

##### 撒鹽巴
- 自己設的加密
- [wiki的說明](https://zh.wikipedia.org/wiki/%E7%9B%90_(%E5%AF%86%E7%A0%81%E5%AD%A6))


---
# 3. 非同步網頁技術AJAX
#### 非同步的js => AJAX
- Asynchronous JAvaScript and XML
- 著名網站：Google Map
- `form_with` 背後就是用AJAX

##### turbolinks
- Rails預設讓每個頁面更換都使用Ajax技巧(
Turbolinks)。在預設的Gemfile中可以看到gem "turbolinks"，以及Layout中的data-turbolinks-track。
- 作用是讓超連結都只用Ajax的方式將整個body內容替換掉（預設網頁的頁首頁尾都一樣）=>這樣換頁時就不需要重新載入head部份的標籤，包括CSS和JavaScript等等，可以節省換頁時的時間。
- 缺點：會幫你做cache，又名troublelinks
- [Turbolinks深度研究](https://www.writershelf.com/article/rails-turbolinks%E2%84%A2-5-%E6%B7%B1%E5%BA%A6%E7%A0%94%E7%A9%B6?locale=zh-TW)


---
# 附件
- [Top In JavaScript Library Usage Distribution in Taiwan](https://trends.builtwith.com/javascript/javascript-library/country/Taiwan) 
	- JS函式庫市占率
	- jQuery佔九成以上(TW)

---
####  Rails的sever忘記關掉的時候
> 複製tmp/pids/server.pid裡面的數字:`$ kill -9 (貼上)`


