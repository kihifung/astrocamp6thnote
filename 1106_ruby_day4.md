# 1106_ruby_day4

[![hackmd-github-sync-badge](https://hackmd.io/rhCCiyiLRYeZte3LbM-bVQ/badge)](https://hackmd.io/rhCCiyiLRYeZte3LbM-bVQ)

---
#### 上課日期：1106
###### tags: `ruby`
###### tags: `5xruby`

---
# 相關連結:
 - [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)


---
# 0. 綱要/目錄
- [ ] 測試TDD-基本介紹
- [ ] 測試TDD-各種小知識
- [ ] Rails專案


---
# 1. 測試驅動開發 TDD(Test-Driven Development)
>- 不會就找不到ruby工作！！！
>- 在寫程式之前，先寫一個測試(程式)，如果程式可以通過測試，程式就可執行。

- 這是一種開發方式，一種安全網的概念
- 先寫一段code去驗證另外一段code是否可行
- 先寫測試，再寫程式

#### 實行時的想法
- 測試不存在的功能，假設它可以正常運作
- 測試失敗時，可以修正這個問題 >>> 知道哪裡有問題，修改後，才會變成「沒有問題」。

#### 安裝
- 測試套件minitest與 RSpec(框架):
  - minitest為ruby內建
  - 但RSpec比較好寫、通用
- 安裝 `$ gem install rspec`

#### 角色
- 寫程式時工程師
- 寫測試時是PM、使用者

---
## 1.1. 各種小知識 
### 1.1.1. 版號命名規則


| <center>4.0.0</center> |3.10.0 | 3.8.2 | 3.8.0 |
| -------- | -------- | -------- |-------- |
| major / minor / patch |    |      |
	- patch 修改小地方
	- minor 修改一些功能，有可能不相容
	- major 大改版，通常不會向下相容

- rails 目前(2020.11.06)版本是6.0.3.4
- 接下來的版本是6.1-rc(release candidate)，表示準備要發布的版本，基本不會有什麼大修改

### 1.1.2. Ruby特有種
- Rake = Ruby Make
- RSpec = Ruby Spec
	- Spec：specification 規範/規格書


##### 延伸閱讀
- [軟體版本編號(wiki)](https://zh.wikipedia.org/wiki/%E8%BB%9F%E4%BB%B6%E7%89%88%E6%9C%AC%E8%99%9F)

---

#### AAA 3A原則
- arrange 先排列好
- act     操作它
- assert  判斷它完成

#### 省略原則
- 通常小括號、大括號或 return可省略不寫
- 想法：盡量省略，讓ruby看起來像英文
- 注意：但如果會影響判斷的話，就不要省略


#### singleton method單體/單例方法
- 目的：保證一個類別只會產生一個物件，而且要提供存取該物件的統一方法

#### 變數前的@
- 有些人不清楚規則，就全部都加
- 全部都加不會有問題，但就是很多餘
- "@"有記憶功能 
- [Ruby Memoization](https://blog.niclin.tw/2019/08/04/ruby-memoization/)


#### ruby沒有屬性
- `attr_reader :xxxx`  
- attr = Attributes 屬性
---

#### review question
- TDD是寫程式來測試程式，那誰來測試TDD？
	- 遵循3A原則，用肉眼來測試TDD
- 為什麼要寫測試？

#### 測試後的符號
"`.`"：完成（幾個點就代表有幾個examples）
![](https://i.imgur.com/PeZR4Se.png)
"`*`"：pending 有東西還沒做（it 方法如果後面沒有加上 Block，預設會是 pending 狀態）
![](https://i.imgur.com/qECjmfY.png)



---

---
# Rails專案
## 1. [可挑戰題目(1102)](https://discord.com/channels/748042598983401482/748046752870826045/772781415896449034)
- Dcard
- 巴哈姆特
- Mobile01 (phpbb/discuz/wordpress/drumla)
- iThome 鐵人賽
- Pinterest / IG
- 財報狗 / 虛擬貨幣網站
- 電商 / 購物
- Pocket / Chrome Extension

## 高級題目
- Hey.com
- VSCode Electron(HTML/CSS/JS)


---

## 2. 以Dcard為例
- 會員系統
	- email / password
	- nickname
	- account
	- avatar 大頭照
	- school
- 看板
	- 分類
	- 名稱
	- 文章s
		- 標題title
		- 作者author
		- 內文content
		- 回應s

### 重新分類
- User
	 - has_many Boards
	 - has_many Posts
	 - has_many Comments
- Category
  - has_many Boards
- Board
	 - belongs_to Category
	 - has_many Posts
	 - belong_to User 版主/管理員
- Post
	 - has_many Comments
	 - belongs_to User
	 - belongs_to Board
- Comment
  - belongs_to Post
  - belongs_to User

### 重新分類2
> 畫圖

## 建立專案
1. 找一個適合的地方建立專案資料夾
`$ rails new NAME`
2. 進入到該資料夾
	`cd NAME`
	`rails s`
:::info
`rails server` > `rails s`
rails server 命令會啟動一個小型的網路伺服器，叫做 WEBrick，是 Ruby 內建的伺服器。想要在瀏覽器存取 Rails 應用程式，使用 rails server 來啟動伺服器。
:::

3. 確認專案已建立，在瀏覽器鍵入，`localhost:3000`
4. 建立基本資料
`$ rails g model User email password nickname account avatar school`
	- 如果打錯的話：`$ rails b model User email password nickname account avatar school`，將g改成b，再打一次
5. 進入資料夾 xxx > db > migrate 
	- Migration這個資料夾的目的是什麼？
		- 描述說接下來這個表格掌什麼樣子
		- 跟model沒有(直接)關係
		- Migration是跟table有關係，但不是一對一
		- 東西做錯的話，新增一個migration再去修正它
		- 用途：紀錄所有資料的欄位和意義


 6. 修改，可先進入沙盒模式模擬： 
 - `$ rails console --snadbox`
 - 離開：ctl+d or exit
 
-----


---
# 附件
- [上課投影片](https://discord.com/channels/748042598983401482/748046752870826045/774152748664094750) 
- [Ping-Pong, Paired Programing](https://thoughtbot.com/upcase/videos/ping-pong-paired-programing) 


