# 1028_htmlcss_day1

[![hackmd-github-sync-badge](https://hackmd.io/W8LVzdCdQd-B98vVegs4UQ/badge)](https://hackmd.io/W8LVzdCdQd-B98vVegs4UQ)

---
#### 上課日期：1028
###### tags: `html/css`
###### tags: `5xruby`

---

# 相關連結:
- 還沒看的，趕快去看啦!!! [AMOS老師 - 金魚都能懂的網頁教學](https://www.youtube.com/playlist?list=PLqivELodHt3iL9PgGHg0_EF86FwdiqCre)
    - Day2~Day22
- 建議看:[金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/users/20112550/ironman/3803?sc=iThelpR)
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25335888)

---

# 1. 基本介紹introduction
 > HTML是什麼？什麼是CSS？
### 概念說明
 - 畫面 > 視覺
 - 程式 > 功能
- 目的：將畫面轉成網頁，網頁：html, css, 程式
    - 程式：ROR, JS, ...
- 框架：Bootstrap(視覺面), vue, angular, react, ...
- 教學內容主要為html, css, bootstrap三大部分

### 資料整理  
- 開資料夾用日期區分，筆記時可加註當時的時間，方便對照影片中的段落。(11:00am)



# 2. HTML

### web:文字 圖片 影音 (詳見老師提供的Xmind)
  * 文字：內文,引用,超連結
      *  清單：ol, il, ...
      *  語意區塊：文章article, 章節section, 側邊欄aslide, header(常用於頁首), footer(常用於頁尾) 
  * 圖片：圖表, 相片, gif動畫, 插畫, icon/圖示 ...

        > 需要知道各個格式的特性
        > 檔案大小會影響傳輸速度，進而影響使用者體驗。
      * 支援圖片格式：jpg, gif, png, webp, svg
      * [jpg](https://zh.wikipedia.org/wiki/JPEG)：一種破壞性壓縮的圖檔，顏色有256^3種
      * [gif](https://zh.wikipedia.org/wiki/GIF)：256色、做動畫、醜醜的透明區
      * [png](https://zh.wikipedia.org/wiki/PNG)：有8位元(跟gif一樣，只差不會動)和24位元(256^3色，平滑的半透明區)
      * [webp](https://zh.wikipedia.org/wiki/WebP)：破壞性壓縮、256^3、平滑的半透明區（新興的格式）
      * [svg](https://zh.wikipedia.org/wiki/%E5%8F%AF%E7%B8%AE%E6%94%BE%E5%90%91%E9%87%8F%E5%9C%96%E5%BD%A2)：向量檔，放大縮小畫質不變；可用於icon上，也適合給因應各種大小裝置所需的圖(RWD)
      * `<img src="圖片來源地址" alt="替代文字">` img只有單一個tag，沒有後面相對應的tag
      * 語法：<標籤 屬性="值">
  * 影音：影片, 聲音 
### [什麼是html(wiki)](https://zh.wikipedia.org/zh-tw/HTML)
    * 標記語言（不是程式語言!!）
    * HTML描述了一個網站的結構語意（就是網站的骨架）
    * 網頁不會知道自己應該長什麼樣，所以需要進行標記

### 架構與語意 
  * 網頁上的東西會有很多，所以需要分組（使用`<div></div>`來區分）以結構化資訊。 (11:27am)
    [練習]
      ```
      <div>
         <img>
         h2>標題</h2>
        <p>內文</p>
      </div>

      <div>
        <img>
        <h2>標題</h2>
        <p>內文</p>
      </div>
      ```
    * div = division
  * 視覺和語意要區分清楚：語意是內容為何，視覺只是美化 
  * 盲人上網時使用語意閱讀器，會讀取語意標籤以理解資訊（最有名的盲人叫做**Google**!!!）(11:36am)
  * 標籤好好寫，才好讓Google抓取資料，出現在搜尋結果上。（不要偷懶都只用`<div>`）
  * 關鍵字：示範關鍵字設定的搜尋效果(12:05am) 
      * 範例：**垂直置中**，[23種CSS垂直置中技巧| CSS可樂](http://csscoke.com/2018/08/21/css-vertical-align/)
* 　SEO(搜尋引擎最佳化)：幫助商家能優先出現在目標族群的搜尋清單內。
---

### 參考工具
- [HTML5 Outliner(chrome擴充功能)](https://chrome.google.com/webstore/detail/html5-outliner/afoibpobokebhgfnknfndkgemglggomo/related?hl=zh-tw)：查看網頁的結構




# 3. 標籤

### 清單
* ol：ordered list
* ul：unordered list
* li：list item 
    #### 課堂作業
     - 寫一個清單
     - 父層 & 子層
       - 範例：`<li>`是子層，要有`<ul>`或`<ol>`作父層
     - 標籤縮排很重要，是基本能力，對於層級的認知很有用(12:30am)

### head裡面
   - 大部分不是給人看的，給應用程式看
   - meta (property)是給社群網站使用(fb/og/...)
    - head和body通常不用再縮排（在`<html>`下）   
### 特別的標籤
- 有些標籤像是`<img>`，標記的資訊不足時，需要額外的訊息。
    - `<img src="test.svg" alt="測試用圖片">`
    - <標籤 屬性="值">
    - 特別屬性-替代文字（alt）：圖片消失時顯示的文字
    - 就本範例來說，在safari裡面，要特別加上圖片的尺寸才能顯示（width="200"）
    
# 4. VScode操作技巧
   - 新增檔案：
        - 標題列點兩下
        - 快捷鍵：cmd + n
   - 更換檔案性質
        - 右下角切換，如圖，plain text > html
        - 快捷鍵:
            1. cmd+k (Mac) / ctrl+k (Windows)
            2. m
![](https://i.imgur.com/u99Bdm3.png)
![](https://i.imgur.com/VCXHKKs.png)
  - 常用[Emmet](https://pjchender.blogspot.com/2016/07/emmet.html)輸入
  - 在設定裡
![](https://i.imgur.com/p1g51NR.png)
- 安裝套件
    * chinese lorem 中文假文
    * live server 直播伺服器
    * Fake Image Snippet Collection 假圖
    * auto rename tag 自動前後標籤更名
    * 安裝後測試:
      * lorem      -英文假文
      * lorem10    -英文假文10個單字
      * ctlorem    -中文假文
      * ctlorem10  -中文假文10字
* 相關設定
    * 自動換行：wrap->on ![](https://i.imgur.com/sigMrpj.png)(14:25am) 
* 移動此行 快捷鍵：alt+上下方向鍵 (Windows) / option+上下方向鍵 (Mac)


# 5. 路徑
- 參考：[Background-image 之一 - 金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/articles/10247622) 
    ### 課堂作業：
     - 做一個資料夾，內有兩個子資料夾（demo, pic）
     - 第一層有三個網頁（01.html,02.html ,03.html）和兩個圖檔（aaa, bbb）
     - demo裡有兩個網頁（d01.html, d02.html）
     - pic裡面有兩個圖（111, 222）
     - 作業一：在d01.html顯示aaa和111
     - 作業二：做04.html，顯示bbb和222

# 6. 其他
### [<!DOCTYPE html>](https://developer.mozilla.org/zh-TW/docs/Glossary/Doctype)
\<!DOCTYPE>會告知你的瀏覽器這個文件是用哪個版本的 HTML （或 XML）撰寫。Doctype 是一種宣告，而非 tag。你也可以把它想作「document type declaration」（文件類型宣告），或是縮寫的 「DTD」。
*(04:20pm)*

# 標籤說明
- `<meta>`
- `<br>` 換行，單個標籤
- `<img>` 圖片，單個標籤
- `<p>` 段落
- `<a>` 連結
- `<h1>`~`<h6>` 標題h1~h6


# Amos書單、片單
(依序)
- [網頁設計入門](https://www.youtube.com/playlist?list=PLqivELodHt3iL9PgGHg0_EF86FwdiqCre)
  - [CSS必學屬性](https://ithelp.ithome.com.tw/users/20112550/ironman/3803?sc=iThelpR)
  - [CSS選取器](https://ithelp.ithome.com.tw/users/20112550/ironman/2799)
- [網頁切版](https://ithelp.ithome.com.tw/users/20112550/ironman/2623)
- [Bootstrap](https://ithelp.ithome.com.tw/users/20112550/ironman/3796)



---
# 附件
- [這裡是附件的標題](這裡放連結) 
- [這裡是附件的標題](這裡放連結) 
