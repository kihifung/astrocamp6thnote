# 1030_git_day3_ruby_day2 

[![hackmd-github-sync-badge](https://hackmd.io/NfcopxcNQYqR57gwVrbpOw/badge)](https://hackmd.io/NfcopxcNQYqR57gwVrbpOw)

---
#### 上課日期：1029
###### tags: `git`
###### tags: `ruby`
###### tags: `5xruby`


---
# 相關連結:
 - [【GIT 小教室】](https://www.youtube.com/playlist?list=PLBd8JGCAcUAF2_im__kqZTfEAKnlmfPJy)


---
# 0. 綱要 / 目錄
1. GitHub說明


---
# 1. GitHub說明
> 接續上次的部分
1. 功能說明
1. issue
    - 討論問題用
    - 只有close，沒有刪除
    - 也有人拿來寫[部落格](https://github.com/aszx87410/blog)
    - 按星星的意思
    - 前端三大框架：VAR, vue, react，angular已經很後面
1. project
    - 專案管理，類似trello
    - column = 看板(trello)
    - note = 卡片(trello)
1. 將專案拉下來
    - `$ git clone (專案位置)`
    - 專案位置可看 **[Code]** 裡的選項：https, ssh, GitHub CLI

# 2. Clone、fetch
> 說明這部分是什麼
1. 將專案clone會將全部都拉下來，包含分支
    - 遠端節點分支origin
    - 遠端分支和本地分支的差別：
    - 通常只會clone一次，之後都是pull和push
2. 遠端進度與本地進度
3. fetch
4. 怎樣移動master？
- reset
- merge
- git remote add origin xxxx
```
$ git fetch oirgin master
$ git merge oirgin/master
```
 - pull = fetch + merge



# 3. 分支的重要性
### 3.1. 分支的重要性
- 舉例：
    如果沒有開分支，大家都會主幹做更新，會產生很多枝節，結構會變得很亂。

### 3.2. fork
- 在GitHub上操作
- 發出PullRequest
    - **說明/註解要寫清楚**，別人才知道這個PR的意思，是否要接收這個PR。
- 發生衝突：
- squash and merge：把多顆捏成一顆（不在意過去的歷史）
-多人專案使用方法：
 1. 有一個人先開一個commit接下來專案的協作者各自fork一份到自己的GitHub裡(同一個專案之後才推得上去)
 2. 你做好自己的部分後發通知給主要的專案者
 3. 接下來以main作為主要的HEAD，當分支經過大部分人確認過之後再merge進來(如果在公司就是資深工程師或boss審核)
 4. 每次做之前要先pull原本的進度在push上去


### 延伸閱讀：
- [Learn Git Branching](https://learngitbranching.js.org/?locale=zh_TW)

---
---





# 4. Ruby
### 4.1. Ruby 
> 基本介紹，自己看先修
- 小括號要注意
- 縮排不要四個空白，兩個就好（一般習慣）
- 縮排很多空白太多也會影響版面的使用

### 4.2. Rack：小型框架
- [Rack專案@GitHub](https://github.com/rack/rack)
- Rack是一種介面
- 不用特別安裝，通常安裝ruby時即有一起安裝
- 工具：[LiveShare on VScode](https://xiaosean.github.io/vscode/2018-05-19-VSCode-Live-share/)
:::info
- 使用rack列印出訊息
-  ![](https://i.imgur.com/gRoExtz.png)
- 第4行：是給瀏覽器Header看的，跟HTML裡的Header是不同東西
- 第5行：實際出現在瀏覽器的東西是引號內的訊息
:::
- chrome的外掛，可能會影響html原始碼的內容
- [duck typing鴨子型別](https://zh.wikipedia.org/wiki/%E9%B8%AD%E5%AD%90%E7%B1%BB%E5%9E%8B)
:::info
- [列印特定文字和環境變數] 
 ![](https://i.imgur.com/3qwFDwy.png)
- 結果
 ![](https://i.imgur.com/3ITHMQm.png)
:::
 - rails就是一個大型的rack，指令透過伺服器發生作用



---

### 參考資源
- [Ruby的Gem套件管理服務](https://rubygems.org/) 
- [HTTP 狀態碼](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Status)

### 延伸閱讀
- [1104 直播測試 互動式 Rebase](https://www.youtube.com/watch?v=4iyWWyg1dFE)

