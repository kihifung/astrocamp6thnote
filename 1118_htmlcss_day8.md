1118_htmlcss_day8
hackmd-github-sync-badge

上課日期：1118
tags: html/css
tags: 5xruby
相關連結:
AstroCamp課程影片
還沒看的，趕快去看啦!!! AMOS老師 - 金魚都能懂的網頁教學(清單)
建議看：金魚都能懂網頁設計入門:怎麼學CSS，並整理出心智圖！
建議看：金魚都能懂的CSS必學屬性
金魚都能懂的網頁切版(清單)
金魚都能懂的Bootstrap5網頁框架開發(清單)
position-金魚都能懂的CSS必學屬性
0. 綱要/目錄
重點1
重點2
重點3
重點4
重點5
1. theme1
定寬容器:
固定寬度的的容器
會依視窗變化寬度，但大到一個尺寸之後就不再變大的容器。 設定最大寬度，用max-width
設定RWD通常不會設定高度，因為螢幕變動時（改變寬度），內容不變，所以顯示會往下長。
斷點
設定不同大小的裝置的地方（從哪個尺寸、像素切開）

e.g.@media screen and (min-width: ....)

container定寬容器 > row > col分欄容器 > item資料容器

要幾個欄位，由col來決定

[note]:Bootstrap的先備知識：格線系統 Grid System

g-1、g-2、g-3…的g，是gutter

欄位間距（gutter）:由margin和padding形成

VScode小技巧
在外面加上一層1
選取目標區塊
cmd + shift + p
鍵入wrap(選abbreviation)
輸入新包覆外層的名稱
ex:section.news = <section class="news">

在外面加上一層2
選取目標區塊
cmd + shift + p
鍵入wrap(選individual lines with abbreviation)
輸入新包覆外層的名稱
li* = 每個項目分別加上li

其他
option + shift + 方向鍵 = 往…方向複製 cmd + 前/後 = 跳到最前面/最後面

等比例區塊
常見於網頁中的嵌入區塊，像是youtube播放區塊、googlemap等。

使用padding-bottom來設定
這裡的尺寸（百分比）會參照父層的寬度
父層的contain box >> 扣掉padding)

嵌入
mv比例 => img撐開
img比例 => iframe比例
mv比例 => iframe比例
iframe寬高 => mv寬高 ＝ iframe原始比例
作業 code review
主標題（h1）的使用
一般來說，一個頁面只會有一個h1，太多可能被google視為對搜尋SEO作弊。
BUT，在html的設定文件中，每個章節（section）可以有一個主標題(h1)
命名-少用方位與編號
如class="left"
在桌機的left/right，到了手機就為變成top/bottom => 就會變成名稱與實際顯示的不符
或是內容數量有變動，編碼與內容也會不符
歸零的設定
避免使用*，可以找normalize.css來用
圖片
掉圖是大忌！！！
路徑記得設定好！
margin與padding
margin會有重疊的問題
作業
先前的切版作業，改用RWD再做一次
手機的選單請見金魚#23
附件
Keyboard shortcuts for macOS(HackMD)
Keyboard shortcuts for Windows(pdf)
wireframe(chrome擴充功能)
看網頁架構
web-paint(chrome擴充功能)
在網頁上畫線
選擇或建立 Branch
