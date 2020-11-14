# 1113_ruby_day6

[![hackmd-github-sync-badge](https://hackmd.io/EOFrEBNKTSiSGJVlmjhzmA/badge)](https://hackmd.io/EOFrEBNKTSiSGJVlmjhzmA)


#### 上課日期：1113
###### tags: `ruby`
###### tags: `5xruby`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)


---
# 0. 綱要/目錄
- [ ] rails 專案
- [ ] 新增
- [ ] 修改
- [ ] 刪除
- [ ] 重點5


---
# 1. rails 專案

##### manifest file 清單文件
- 被用來定義擴展或檔案打包相關數據
- 減少檔案的大小和require的數量
- 註解等訊息都會被壓縮
![](https://i.imgur.com/28I7VUg.png)
- `require_tree .`，一種便捷的寫法（龍哥：偷懶），表示以下的東西都require 
- 應該直接寫明需要require什麼項目才好，這樣可以清楚知道到底用什麼
		
##### 
- [Asset Pipeline 說明](https://ihower.tw/rails/assets-pipeline.html)


##### 
- [前端工具：webpack](https://webpack.js.org/)
- Rails 6 開始支援
- 5之前為asset pipeline
---
- note: 當東西越來越多的時候，要將其中一些模組化。不但可以整理版面，也可以讓其他地方拿來用。
- note: 局部渲染（不是完整的檔案），前面檔名有底線，
##### meta programming
- 用程式碼來寫程式
- 舉例：用一台3D印表機製作出一台印表機的零件（然後將其組裝起來）=> 用印表機印出印表機

- 在alias（別名）裡面會設定相關的名稱，類似關鍵字的模糊比對，通常會包含該方法的各種變化。

---

- Board.find(1)    #只會找到一筆資料，只能數字
- Board.find_by(id: 2)	#只會找到一筆資料，可以接hash
- Board.where(id: 3) #會找到一組資料（陣列）
- Board.all  		#會找到一組資料
#### 面試題：find跟find_by差在哪？
- 找到資料有差
- 錯誤訊息也不同
- 相近的另一種方法：find_by! <-加一個驚嘆號

---
##### 錯誤訊息的處理方法
在Controller裡面：
`rescoue_form ActiveRecord::RecordNotFound, with: ABC `
=> 只要在這個Controller出現ActiveRecord::RecordNotFound這個錯誤訊息，就會用with後面的ABC方法來處理。接著在下方定義ABC。
- 這種方法通常不會公開，會放在下方的private裡面
- 比較好的方式是，讓它連結到404頁面
- rails會有一個內建的404頁面，放在public下面
	- 放在public下面的，不需要經過MVCR的處理
	- 404頁面，其實是一個很好的廣告/導覽頁面，因為使用者會好好看這一頁。

---

note: create 和 update 因為流程上很像，所以code也長得很像
note: new 和 edit 因為流程上很像，所以code也長得很像

##### unobtrusive javascript 非侵入式JavaScript
- 不要將JS綁在html裡面


---
- php的laravel(2011)模仿自rails(2004)

##### before_action 
- 在action之前就先執行，這樣可以減少後面action中同樣的程式碼
- before_filter同義，是較早的版本

##### 局部渲染
- 要注意不要有 "@" 實體變數，讓它主動去抓資料產生變化。而是讓它被動（的提供內容）

- note: 省略時，要注意 對應到的資料是否唯一/常用。
- note: 在rails裡，沒有特別註明格式，預設為html

---
# 作業
本週 Ruby 作業練習：

- 開一個全新的 Rails 專案
- 手工撰寫針對 Book 的 CRUD 功能
  - Book 有書名跟售價兩個欄位
- 邊講解邊錄影，錄影上傳到 Youtube
- 儘量把時間壓在 30 分鐘內
- 11/17（二）10:00 前交件

