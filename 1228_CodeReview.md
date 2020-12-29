# 1228_CodeReview

###### tags: `codereview`

--
[TOC]

---
### 1. 要撰寫readme
> readme應該要有什麼內容？
- [參考連結](https://www.itread01.com/content/1546336472.html)
- README.md檔案是一個專案的入門手冊，裡面介紹了整個專案達到什麼樣子的效果、需要搭建什麼樣的環境、具備什麼樣的技能等等。


### 2. commit的命名
- [約定式提交conversation commit](https://www.conventionalcommits.org/zh-hant/v1.0.0/)
- 一種用於增加提交說明之人機可讀性意義的規範
- 寫commit時的參考規範
- commit log描述不用底線(https://www.conventionalcommits.org/zh-hant/v1.0.0/)
- commit 的命名不用底線 


### 3. 套件Gem
- [套件管理網站](https://rubygems.org/)
- gemfile裡面使用的套件最好寫清楚版本編號，這樣有異動時才容易看出差別
- 上線自動抓最新版時出錯才容易發現

### 4. rails/concern
> concern應該要寫什麼？
- [Rails 程式碼整理術（入門）](https://railsbook.tw/chapters/25-organize-your-code.html)
- 有共同的動作可以放rails concern
- Rails 有提供 Concern 的功能，可以把「共同的行為」集中起來，有需要的再「引入」，而不使用繼承。

### 5. 狀態機state
- Board.where(state:‘open’)等同於 Board.open (狀態機的語法糖)
- 狀態機中的enum可以使用


### 6. 驚嘆號
- find_by要給驚嘆號
- 不錯的寫法：`become_driver!`


### 7. 其他 
- 程式碼的斷行不要超過三行
- 欄位不要用type，type是預設的單表繼承功能
- link_to ('成為外送員', root_path, class: 'nav-link')
