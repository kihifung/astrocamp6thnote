# 1027_git_day2

#### 上課日期：1027
###### tags: `git`
###### tags: `5xruby`

---
# 相關連結
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25307238)

---
# 目錄
- [工作區、初始化](https://hackmd.io/PbWvPH__SjqmEO2J_q_MNg#Git%E5%88%86%E4%B8%89%E5%A4%A7%E5%8D%80%E5%A1%8A%EF%BC%9A%E5%B7%A5%E4%BD%9C%E5%8D%80%E3%80%81%E6%9A%AB%E5%AD%98%E5%8D%80%E3%80%81%E5%84%B2%E5%AD%98%E5%BA%AB)
- [標籤、貼紙](https://hackmd.io/PbWvPH__SjqmEO2J_q_MNg#%E6%A8%99%E7%B1%A4--%E8%B2%BC%E7%B4%99)
- [GitHub](https://hackmd.io/PbWvPH__SjqmEO2J_q_MNg#GitHub%E6%98%AF%E4%BB%80%E9%BA%BC%EF%BC%9F)
- [作業](https://hackmd.io/PbWvPH__SjqmEO2J_q_MNg?both#%E4%BD%9C%E6%A5%AD)
- [附錄](https://hackmd.io/PbWvPH__SjqmEO2J_q_MNg#%E9%99%84%E9%8C%84)

> 上面連結點了會另開連結...


---
### Git分三大區塊：工作區、暫存區、儲存庫

### 初始化git

- 在欲版控的根目錄下，執行`git init`，再執行`ls -al`會發現多了一個.git的隱藏檔案，所有在這個根目錄下的檔案更動都會紀錄在裡面。
- 用指令`git status`可以看到所在位置的目錄下，是否有檔案未被追蹤，可使用git add加到暫存區以進行追蹤。有任何資料異動，也會顯示在這裡

### 初始化後的檔案每次想要儲存都要做以下的事情

1. $ git add 檔案名(想全存就使用".")
2. $ git commit -m "這次commit的說明"(沒有-m就會掉進vim的深淵喔！)
```ruby
$ git status
位於分支 human
尚未暫存以備提交的變更：
  （使用 "git add/rm <檔案>..." 更新要提交的內容）
  （使用 "git restore <檔案>..." 捨棄工作區的改動）
	修改：     djiwd.html
	刪除：     hello.html

未追蹤的檔案:
  （使用 "git add <檔案>..." 以包含要提交的內容）
	aaa.html
```

:::info
### 不小心掉進Vim怎麼辦?(救救我)
Git內建的編輯器-Vim，有兩個模式：
* Normal 模式(命令模式)-逃脫方法
  離開 :q 存檔 :w 存檔後離開 :wq (冒號必打)
* Insert 模式(編輯模式)-逃脫方法
  操作前要按i或o或a其中一個，按ESC鍵可以退到命令模式
:::
    


### 快捷鍵
- `cd /`  回到c槽(如果使用window要用cd /mnt/c/)
- `cd -`  回到上一次操作
- `ctrl + W` 一個字一個字刪除(空格到空格是一個字)
- `ctrl + u` 整行刪除
- `ctrl + l` 整個版面清理
- `ctrl + r` 尋找曾經下過的指令

### 分支
- `cd /`  回到c槽(如果使用window要用cd /mnt/c/)
- `cd -`  回到上一次操作
    -  `git checkout -` 更換head到上ㄧ次
- `$git commit -m "ccc" --allow-empty` 允許註解空白
- 快轉合併（fast-forward）


## 分支（貼紙）

### 分支(branch)改名
`git checkout -` 將HEAD回到上一個分支位置（兩個互換）
`git branch`    可以查詢目前分支
`git branch -d` 可以刪除分支/標籤
`git branch -m` 改分支/標籤名
`git branch -f` 可強制移動分支
`git merge `（現在分支）（欲走到的分支位置）

### 刪除分支
 - 留著也沒關係，因為只是一個標籤/貼紙，容量很小(幾kb=幾千byte)，沒什麼實際的影響，不影響主枝幹。
 - 刪除未合併分支，並沒有實際刪除，只是隱形。（git沒有刪除這回事）

### tag標籤
> 使用代號的意思
> 通常用在重要的commit/里程碑
```
$ git tag 1.0.0 51d54ffc，其中1.0.0是自己設定的標籤
```

### 發生衝突
1. 發生在合併之後
2. 查看衝突的檔案，`$ git status`
5. 修改衝突的檔案（在文字編輯器裡，如vscode）
6. 將修改後檔案加到暫存區，`$ git add xxxx.html`
7. 將修改後檔案加到儲存庫，`$ git commit -m "add xxxx"` 

---
### head
- `$ git reflog` = ref+log，查看紀錄：檢視head的移動軌跡
- 會移動head的操作
    * checkout
    * commit
    * reset
    * merge



---
### Rebase 另一種合併的方式（剪貼？嫁接？）
- rebase跟merge的差異就是:
    - rebase有點像身為HEAD的貼紙，去踩著另一個貼紙往上爬的感覺；
    - 而merge則是再多開一個commit，把不是HEAD的那個節點加進來的感覺
- 操作練習
    ```
    # use branch2
    $ git checkout cat
    $ git rebase dog
    ```

:::info
**注意**：
如果使用是windows的同學，可能會有電腦解讀問題,說有沒有add的檔案而不讓你操作合併分支，可打以下指令解除：
`$ git config core. filemode false`
:::

### reset / become
- 同時搬移分支及HEAD，回到指定位置（代名詞）的狀態
- 使用參數
    ```
    --mixed：預設值，丟回工作目錄
    --soft：丟回暫存區
    --hard：丟進垃圾桶
    ```
    ```
    ＾ = caret 倒退一步
    ～n = tilde 倒退n步
    ex: head^^ = head~2
    ```
- 有兩個parent時：
    ^1：往1st parent移動
    ^2：往2nd parent移動
- checkout 只移動head，但reset會移動head和分支
### 使用標籤（tag）

* $ git alias(別名)
``` 
$ git config --global alias.co checkout 
$ git config --global alias.br branch
$ git config --global alias.st status 
```
* tag：通常用在里程碑 標示階段
* 分支：通常用來區別功能
* tag和分支的差異：tag不能移動只能刪除，分支可以移動可以刪除。

---
## GitHub是什麼？ 
- [練習用專案](https://github.com/kaochenlong/git-demo-123)
### 用push把你的專案上傳GitHub吧 

`$ git push origin master`
 > (你不想用origin也可以用其他名稱,但自己要記得)
 
`$ git push origin master:master `
 > (前面的master代表你本機的貼紙；後面的master代表你上傳後想叫甚麼貼紙)
 
`$ git push origin 1.0:abc `
 > (這個表示你想要把標籤1.0的commit上傳而且貼紙名稱改成abc)
    
### Heroku
> 未來你也許會使用到的平台;他要求你一定要使用master貼紙
```
$ git push heroku master
$ git push heroku cat:master
```
- 如果你調皮本機不想要上傳master貼紙也沒關係，只要上傳cat貼紙時跟他說雲端要改用master貼紙喔，這樣這個平台也給過


### 如果想把git改成英文版的話
```
$ echo "alias git='LANG=en_GB git'" >> ~/.zshrc
```
在終端機上輸入上列指令，然後重開就可以了。

### 如果想延長打字的壽命的話
```
$git config --global alias.co checkout
$git config --global alias.br branch
$git config --global alias.at status
```
以上是幾個簡單的縮寫替代，從此就靠co幫你checkout;st幫你status;br幫你branch

---
---
# 作業
## 別忘了回家作業 11/2 前要交！
- [回家作業下載連結](https://ubin.io/git-q-example)

---
## 附錄
### 筆記工具 HackMD
- [HackMD](https://hackmd.io/)：台灣新創，使用markdown語法，也可用html標籤（部分?）
- [markdown語法參考（Astrocamp粉專）](https://reurl.cc/gmN5eX)

