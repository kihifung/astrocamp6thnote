# 1117_htmlcss_day7

[![hackmd-github-sync-badge](https://hackmd.io/_Y-9iQE9TwScsC0HZiwg4g/badge)](https://hackmd.io/_Y-9iQE9TwScsC0HZiwg4g)

---
#### 上課日期：1117
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
- [ ] RWD
- [ ] 格線系統
- [ ] 媒體查詢



### 叮嚀：flex一定要熟！
---
# 1. RWD
> 主要藉由尺寸來偵測使用裝置



1. 基本概念
		
- 主標題與內文的大小沒有一定的標準，可能是一個範圍。如果對象族群更改，需求也可能改變 
	- 確認好目標族群是誰？
	- 班上統計:
      - 主標題- 24~28px
      - 內文 - 18px
>    Amos: 發表和畢業的時候看作品，可能都不記得當初投票的結果
- bootstrap的寫法為由小寫到大（裝置）
- 因為優先權的關係，前面的條件滿足了就不會執行較小的條件


2. 媒體查詢		
```htmlmixed=
@media 裝置 and (條件) and (條件){
	符合條件後要執行的CSS
	}
```
- 其實就是優先權
  媒體查詢要放最後面，因為它本身是有條件發動的，普通常用的CSS寫在後面，會蓋掉有限制條件發動的媒體查詢的優先權。

- 課堂練習：平板桌機三欄 手機一欄
- RWD的寫法：固定或比例

#### calc
- 建議：只要有運算符號的，一律在前後加上空格，以方便辨識。

#### 另一種方法：格線

---
#### col 分欄容器


#### item 資料容器





---
# 附件
- [查看螢幕解析度](http://csscoke.com/webq/) 





