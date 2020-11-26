# 1124_htmlcss_day9

[![hackmd-github-sync-badge](https://hackmd.io/gF9pl_EcSGGGOQjO2GdOTA/badge)](https://hackmd.io/gF9pl_EcSGGGOQjO2GdOTA)



#### 上課日期：1124
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
- [ ] bootstrap


---

#### （思考）如果要橫向排列有幾種方式？
- flex
- float
- position
- ...

#### (思考）物件的特性與呈現的效果
- block物件才會預設直排，span就不會
- 有些本身就有的屬性，好好使用，後續就不用進行過多的設定


---
#### 寬度
- 100%，畫面寬度，不含捲軸 
- 100vh，視窗寬度，畫面寬度加上捲軸
- 字隨螢幕改變：width100%; font-size:4.5vw[絕對大小/畫面大小*100%]
---


# 1. bootstrap
1. [複製模版](https://v5.getbootstrap.com/docs/5.0/getting-started/introduction/#starter-template)
	- 另存成網頁備用


#### layout > Breakpoints 斷點


| Breakpoint |Class infix  |	Dimensions||
| -------- | -------- | -------- |-------- |
| X-Small | None   | <576px |
| Small | sm  | ≥576px  |手機|
| Medium | md  | ≥768px  |平板直
| Large  | lg  | ≥992px  |平板橫
| Extra large |xl|≥1200px | 桌機
| Extra extra large|xxl |≥1400px|大螢幕
	
斷點，需搭配[定寬容器(container)使用](https://v5.getbootstrap.com/docs/5.0/layout/containers/)
	
尺寸代號
- X-small(All)
- sm 手機橫向
- md 平板直向
- lg 平板橫向
- xl 桌機
- xxl 大畫面

		
#### layout > Containers	
![](https://i.imgur.com/CWJMHhT.png)

#### snippet-creator(vscode	套件)
- 快捷鍵設定
1. 寫好想要的內容
2. 選取後，cmd + shift + p 
3. 輸入套件名稱 crea... 或 snip...
4. 選擇內容的類別（html,...）
5. 輸入快捷鍵完整名稱
6. 輸入快捷鍵（打什麼會跑出來）
7. 輸入快捷鍵的內容描述
8. 開心使用快捷鍵
-
**[note]** bootstrap的排版預設都用flex

##### flex
> 包含三個屬性 flex-grow、flex-shrink 和 flex-basis。

* grow：伸展性，是一個數值，當空間分配還有剩餘時的當前元件的伸展性，預設值為 0，如果設置為 0 則不會縮放。
* shrink：收縮性，是一個數值，當空間分配還不足時的當前元件的收縮性，預設值為 1，如果設置為 0 則不會縮放。
* basis：基準值，可使用不同的單位值。

##### 自動折行
- bootstrap除非超過12個，不然只有手動折行
##### 自動欄寬
- `<div class="row row-cols-2 row-cols-md-4">`
- row-cols-2：自動分兩欄 
- row-cols-md-4：手機以上自動分四欄
- 利用父層的寬度來設定

##### Gutters 欄間距
- 指的是padding，由父層來決定
- g-1, g-2, ..., g-5
- p-1, p-2, ..., p-5
- px-1, px-2, ..., px-5
- - py , pt 
- 範例：圖片之間等距
```htmlmixed=
.col img{  width: 100%;  }
<div class="row g-3 row-cols-2 row-cols-md-4">
	<img src="#">
</div>
```

##### /utilities/spacing/
- 
##### components/card/
##### components/list-group
- [介紹頁面](https://v5.getbootstrap.com/docs/5.0/components/list-group/)
- 選單：有選項、連結、按鈕等等
- flush：去除外框線
##### Image overlays
- [介紹頁面](https://v5.getbootstrap.com/docs/5.0/components/card/#image)
- 用`card-img-overlay`替換`card body`
##### card-group
- 可能不太實用
- 包在card外面可讓卡片組件變成橫排
- AMOS：用格線就好了


---




---
# 附件
- [Background-image 之二- 金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/articles/10248148) 
- [幻燈片製作無困難-金魚都能懂的Bootstrap5網頁框架開發入門](https://www.youtube.com/watch?v=l-x3o38zYEQ) 


