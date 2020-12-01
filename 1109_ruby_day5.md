# 1109_ruby_day5

[![hackmd-github-sync-badge](https://hackmd.io/MZ8ySDMMQUmc_-MMZq2Dvw/badge)](https://hackmd.io/MZ8ySDMMQUmc_-MMZq2Dvw)

---
#### 上課日期：1109
###### tags: `ruby`
###### tags: `5xruby`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)


---
# 0. 綱要/目錄
- [ ] 1. Board / route / controller
- [ ] 2. Rails的格式與操作
- [ ] 3. 附錄 



---
# 1. Board / route / controller
### 安裝 / bundler / gemfile
`$ rails g model Board title`

- 學習框架就是學習慣例
- 在vscode裡，若要固定將__.html.erb檔改成是html格式，找到此行做修改即可。
（或者也可以逐次在檔案裡修改）
```
"emmet.incloudLanguage": {
 			"erb": "html"  }
```

## controller裡的實體變數 
在不同的def裡面，實體變數即使外貌一樣，仍視為不同動作下的結果，該動作結束後實體變數就消失。
- controller不要放會重複的東西


## 參數傳遞
```ruby=
GET /boards?id=2&name=3&cc=4
params = { "id" => 2, "name" => 3 }

POST /boards
params = { "title" => 'ccc', "ccc" => "ddd" }
```
:::info
#### 面試題：get跟post有什麼不一樣？
- 主要的不同，傳送方式不一樣，只是post稍微安全一點。除非進行加密。
- get：將參數（帳號密碼）在路徑裡面傳送（變成明碼），會出現在網址上，在瀏覽紀錄裡面看得到
- post：將參數放在php的requist body裡面傳送。
- 兩者傳送資料的型態不同，因此post送出後頁面重新整理會出現提示![](https://i.imgur.com/ICUNMpK.png)
:::

#### params
- 像是hash。
- 資料送到後端的過程，可用params去拿值，它會拿出類似hash的值（是rack幕後做的打包動作）。

#### 網址說明
網址：`http://localhost:3000/boards/new?id=2&name=?3#aaa`
* `http://`  - protocal
* `localhost` - hostname/ domain name
* `:3000/` - port （http預設是80，https預設是443）
* `/boards/new` - path-> route.rb 路徑（連結到哪個頁面）
* `?id=2&name=?3` - querystring查詢字串 -> 在rails裡是params的一部分
* `#aaa ` - 錨點aaa
- 延伸閱讀：[URL(wiki)](https://en.wikipedia.org/wiki/URL)
- 範例：
![](https://i.imgur.com/QQAnxNu.png)
- 帳號密碼可在本機的瀏覽器裡看到，network > name_sign_in > ...


### SASS/SCSS
- CSS的不同寫法
- [介紹文1](https://medium.com/andy-blog/day05-%E8%AE%93css%E4%B8%8D%E5%86%8D%E9%9B%A3%E8%AE%80-scss-6e46261a42b5)
- [介紹文2](https://tw.alphacamp.co/blog/css-preprocessor-sass-scss)
- [vscode裡的連結](https://sass-lang.com/)


---
# 2. Rails的格式與操作
## 2.1. 為何明明沒寫，可是頁面卻仍然有html的樣式內容？
> rails會將每個網頁共同的地方拉出來放

1. 理論上每個html.erb檔，都會有自己的layout，但如果沒有就會依application.html.erb檔的格式，所以又稱它為「預設全站的公版格式」。
> 如果要了解views的html.erb檔，可至views裡的layouts看application.html.erb檔即可知道。
> ![](https://i.imgur.com/D0St5J7.png)

2. 因為是公版格式，可以在此設定表頭或是註腳（footer）

---
## 2.2. 在rails裡更改css樣式表？
> SCSS、SASS
1. 如果想在rails裡更改css樣式表，有提供scss的格式，相關技巧寫法可看以下連結。
- [介紹文1](https://medium.com/andy-blog/day05-%E8%AE%93css%E4%B8%8D%E5%86%8D%E9%9B%A3%E8%AE%80-scss-6e46261a42b5)
- [介紹文2](https://tw.alphacamp.co/blog/css-preprocessor-sass-scss)
- [sass-lang](https://sass-lang.com/)

2. 更改的檔案，是在app/stylesheets/boards.scss檔案裡，如下圖：
![](https://i.imgur.com/cnPgQAl.png)


---
# 3. 其他補充網站
- [buildwith](https://builtwith.com/)：查詢網站使用哪些技術
- [hash裡包hash的寫法與詳解](https://apidock.com/rails/ActionController/Parameters/permit)（承豪提供）



