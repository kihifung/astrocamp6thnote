# 1118_htmlcss_day8

[![hackmd-github-sync-badge](https://hackmd.io/_Y-9iQE9TwScsC0HZiwg4g/badge)](https://hackmd.io/_Y-9iQE9TwScsC0HZiwg4g)


#### 上課日期：1118
###### tags: `html/css`
###### tags: `5xruby`


---
# 相關連結:
- [AstroCamp課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
- 還沒看的，趕快去看啦!!! [AMOS老師 - 金魚都能懂的網頁教學(清單)](https://www.youtube.com/playlist?list=PLqivELodHt3iL9PgGHg0_EF86FwdiqCre)
	- 建議看：[金魚都能懂網頁設計入門:怎麼學CSS](https://youtu.be/h7wJ2YZarFc)，並整理出心智圖！
- 建議看：[金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/users/20112550/ironman/3803?sc=iThelpR)
- [金魚都能懂的網頁切版(清單)](https://www.youtube.com/playlist?list=PLqivELodHt3hxeuLX8PYaI8u1GcDaBoJo)
- [金魚都能懂的Bootstrap5網頁框架開發(清單)](https://www.youtube.com/playlist?list=PLqivELodHt3jq3oWBZfdhMu0GE7774HBW)
- [position-金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/articles/10253500)



---
# 0. 綱要/目錄
- [ ] 重點1
- [ ] 重點2
- [ ] 重點3
- [ ] 重點4
- [ ] 重點5


---
# 1. theme1
#### 定寬容器:
- 固定寬度的的容器
- 會依視窗變化寬度，但大到一個尺寸之後就不再變大的容器。
  設定最大寬度，用`max-width`
- 設定RWD通常不會設定高度，因為螢幕變動時（改變寬度），內容不變，所以顯示會往下長。

#### 斷點
- 設定不同大小的裝置的地方（從哪個尺寸、像素切開）

  e.g.`@media screen and (min-width: ....)`


- container定寬容器 > row > col分欄容器 > item資料容器
	> 要幾個欄位，由col來決定
- **[note]**:Bootstrap的先備知識：格線系統 Grid System
- `g-1`、`g-2`、`g-3`....的g，是gutter
	> 欄位間距（gutter）:由margin和padding形成


---

### VScode小技巧
#### 在外面加上一層1
1. 選取目標區塊
2. cmd + shift + p
3. 鍵入wrap(選abbreviation)
4. 輸入新包覆外層的名稱
	> ex:section.news = `<section class="news">`

#### 在外面加上一層2
1. 選取目標區塊
2. cmd + shift + p
3. 鍵入wrap(選individual lines with abbreviation)
4. 輸入新包覆外層的名稱
	> li* = 每個項目分別加上li

#### 其他
option + shift + 方向鍵 = 往..方向複製
cmd + 前/後 = 跳到最前面/最後面

---

# 等比例區塊
> 常見於網頁中的嵌入區塊，像是youtube播放區塊、googlemap等。
- 使用padding-bottom來設定
- 這裡的尺寸（百分比）會參照父層的寬度
 	> 父層的contain box >> 扣掉padding)

### 嵌入
1. mv比例 => img撐開
1. img比例 => iframe比例
1. mv比例 => iframe比例
1. iframe寬高 => mv寬高 ＝ iframe原始比例

---
# 作業 code review
#### 主標題（h1）的使用
- 一般來說，一個頁面只會有一個h1，太多可能被google視為對搜尋SEO作弊。
- BUT，在html的設定文件中，每個章節（section）可以有一個主標題(h1)

#### 命名-少用方位與編號
- 如`class="left"`
- 在桌機的left/right，到了手機就為變成top/bottom => 就會變成名稱與實際顯示的不符
- 或是內容數量有變動，編碼與內容也會不符

#### 歸零的設定 
- 避免使用`*`，可以找normalize.css來用


#### 圖片
- 掉圖是大忌！！！
- 路徑記得設定好！

#### margin與padding
- margin會有重疊的問題


---
# 作業
- 先前的切版作業，改用RWD再做一次
- 手機的選單請見[金魚#23](https://www.youtube.com/watch?v=E9SosNZkX7Y)

---
# 附件
- [Keyboard shortcuts for macOS(HackMD)](https://hackmd.io/@astrocamp6th/ByyYELf9v) 
- [Keyboard shortcuts for Windows(pdf)](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
- [wireframe(chrome擴充功能)](https://chrome.google.com/webstore/detail/wireframe/amchfjeinhflcmbpdgdihhdoogdagcaf?hl=zh-TW)
	- 看網頁架構
- [web-paint(chrome擴充功能)](https://chrome.google.com/webstore/detail/web-paint/emeokgokialpjadjaoeiplmnkjoaegng/related?hl=zh-TW)
	- 在網頁上畫線

