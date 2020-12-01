# 1026_git_day1

[![hackmd-github-sync-badge](https://hackmd.io/bTmUOsYXSGqdcgyxEex10w/badge)](https://hackmd.io/bTmUOsYXSGqdcgyxEex10w)

#### 上課日期：1026
###### tags: `git`
###### tags: `5xruby`


---
# 相關連結
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25305569)

---
# 0. 綱要/目錄
1. Git簡介
2. 安裝 Git
3. 常用終端機指令介紹
4. 使用分支
5. 如何回到上一步 


# 1. 安裝與設定
1. 安裝git(git bash)
     > 安裝在wsl，`$ sudo apt install git`
2. 查看版本 `$ git --version`
3. 進行基本設定
    ```
    $ git config --list
    $ git config --global user.name "name"
    $ git config --global user.email "email@gmail.com"
    ```
4. 
    - **初始化 $ git init**
    - 列出資料夾全部內容 $ ls -al
    - 改變資料夾 cd XXX
    - 回到上一層 cd ..
    - 留在當下那一層 cd .，一個點指這一層，兩個點指上一層
    - 創建資料夾 mkdir XXX
    - $ git status
    - $ rm -rf .git 刪除.git這個資料夾
         - rm = 刪除
         - f = force 強迫 
         - r = recursive 
    - pwd 確定在哪個資料夾
    - ls -al / ls -l 顯示目錄，a 表示顯示隱藏檔。 
    - `.`開頭的資料夾，為隱藏的資料夾
    - $ man  = manual 
    - $ git --all 全部都上git
    - 新建一個資料 touch index.html

---
# 2. 相關概念

- 不同的os之間，下指令時是跟外殼（shell）溝通，藉由殼來取資料
- terminal終端機，是一個介面


---

* 工作目錄：桌面
* 暫存區域：ram
* 儲存庫（本地）：hdd / ssd
* 儲存庫（遠端）：cloud

----
- `$ git add` 工作目錄 存到 暫存區
- `$ git commit `暫存區 存到 儲存庫
- 暫存區 的功用之一是「收集待處理事件，再一起處理」
- `$ git push` 本地 推到 遠端
- `$ git pull` 遠端 拉到 本地
![](https://i.imgur.com/AOidnvx.png)
- mac螢幕截圖/錄影：shift + cmd + 5



---

- `$ git commit -m "1st commit"`，引號內是本次commit的註解，很重要！！！
- 不要直接打 `git commit`，會進入到vim
    - vim 是很古老的文字編輯器
- 什麼時候需要commit?
    - 完成一個階段任務時
 - `$ git log`   看紀錄
 - `$ git log --oneline` 簡要的看紀錄（一個一行） 
 - [git範例檔](https://drive.google.com/file/d/11ye5C_wpMwsfwz-myFSMZasnVOH52nCh/view)：https://ubin.io/git-files

# WSL
 - `$cd /mnt/c/xyz`，更換目錄到Ｃ槽的xyz資料夾
     - mnt = mount 掛載，藉由一個通道連到shell外面
 
# checkout
 - restore  救回檔案 (讓檔案或目錄回到最近一次的 add > commit 的狀態，需有commit才能救回。不要輕易使用checkout *，有危險性)
 - switch   切換分支

# [blame](https://gitbook.tw/chapters/using-git/git-blame.html)
 - `$ git blame XXX.html`
 - `$ git blame -L 5,10 index.html`  只看5~10行
 - `git log -p FILENAME` 檢視歷史紀錄



---
# 回復
> 先到暫存區找，有的話就蓋掉

# 分支 branch
- `$ git branch` 查看目前分支
- 現在所處分支上面會有星號
- `$ git branch XXX`  建立名為xxx的分支
- `$ git checkout XXX` 更換所處分支到XXX
- `$ git switch XXX` 更換所處分支到XXX
- `$ git branch ddd 657fce7` 將ddd的標籤貼到657fce7這個分支上面 
- `$ git checkout -b net`，創建net分支並切換到net



---

### [常用指令參考](https://g0v.hackmd.io/s/HyK3GOr_P)
