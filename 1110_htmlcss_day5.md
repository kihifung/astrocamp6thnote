# 1110_htmlcss_day5

[![hackmd-github-sync-badge](https://hackmd.io/1hkHD128Q5GqS-y5blN3Cw/badge)](https://hackmd.io/1hkHD128Q5GqS-y5blN3Cw)

---
#### 上課日期：1110
###### tags: `html/css`
###### tags: `5xruby`


---
# 相關連結:
- 還沒看的，趕快去看啦!!! [AMOS老師 - 金魚都能懂的網頁教學(youtube)](https://www.youtube.com/playlist?list=PLqivELodHt3iL9PgGHg0_EF86FwdiqCre)
- 建議看：[金魚都能懂網頁設計入門:怎麼學CSS](https://youtu.be/h7wJ2YZarFc)，並整理出心智圖！
- 建議看：[金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/users/20112550/ironman/3803?sc=iThelpR)
- [金魚都能懂的網頁切版(youtube)](https://www.youtube.com/playlist?list=PLqivELodHt3hxeuLX8PYaI8u1GcDaBoJo)
- [金魚都能懂的Bootstrap5網頁框架開發(youtube)](https://www.youtube.com/playlist?list=PLqivELodHt3jq3oWBZfdhMu0GE7774HBW)
- [position-金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/articles/10253500)
- [AstroCamp課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
---
# 0. 綱要/目錄
- [ ] 課程說明
- [ ] 父層的設定-flex(box)
- [ ] 子層的設定



---
# 1. 課程說明
1. 全部十天
	1. 已上四天 
	2. 兩天：flex、position、boxmodel的計算、box xxxx、reset（、float）
	4. 三天：RWD、Bootstrap
	  - Bootstrap先看影片！！
	  - [金魚都能懂的Bootstrap5網頁框架開發(youtube)](https://www.youtube.com/playlist?list=PLqivELodHt3jq3oWBZfdhMu0GE7774HBW)
	5. 最後一天：workshop


---

# 2. 父層的設定-Flex (Box)
> 不同層級：父層、子層的關係

### 2.1. display:flex
> 之前講過
### 2.2. flex-flow
1. flex:wrap
1. flex-direction
	> 設定主軸的方向
	> 預設為語言的方向，一般常見為中文英文，所以通常會以為是由左往右（阿拉伯文即由右至左）
	1. 設定由右至左
		- `<body dir="rtl">` 在body設定：dir為方向 rtl為右至左
		- 設定css：`flex-direction: row-reverse; `  "語言書寫的方向（行列/橫）：設定為反向"
		- 設定css：`flex-direction: column;` "欄的方向（直），由上往下"
			> 參考：`flex-direction: column-reverse;` 為由下往上
  	2. [直排參考連結(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/CSS/writing-mode) 
	3. main-axis主軸  cross-axis交叉軸
		- 兩個軸，一個可順向逆向，另一個為每次都單一方向
### 2.3. justify-content
> 指定主軸的兩個特性：對齊跟分布
 1. `justify-content: flex-end`，對齊主軸的尾端。
 2. `justify-content: center;`， 置中對齊。
 3. `justify-content: space-around;`  /* 把剩餘空間分配到子項目的左右兩側 */
![](https://i.imgur.com/H0ZRQqe.png)
4. `justify-content: space-evenly;`，均分周邊空間，效果等同    
 ```
	.item1,.item2,.item3{ margin-left: auto; }
	.item3{  margin-right: auto; }
```
![](https://i.imgur.com/eM2mcMQ.png)
:::info
##### 日常練習
- 平常網站看到的是around 還是between ？
- 物件周圍空間均等，物件間的距離比側邊寬兩倍
:::
5.折行 置中 
	`flex-wrap: wrap;`  
  `justify-content: center;`
![](https://i.imgur.com/ei84ywq.png)
6. 折行 between
	`flex-wrap: wrap;`  
  `justify-content: space-between;`
![](https://i.imgur.com/inTIoDc.png)
7. wrap-控制交叉軸(主軸顛倒)
	`flex-wrap: wrap-reverse;`  
  `justify-content: space-between;`
![](https://i.imgur.com/01BYSB0.png )

### 2.4. align-items
> 控制子物件在該列的定位，亦就是說「指定交叉軸的對齊和分佈」。
1. 水平置中、垂直置中
`justify-content:center;`（水平置中）
`align-items: center;`（垂直置中）
![](https://i.imgur.com/5YAnGcH.png)

2. 水平置中、垂直置頂
`justify-content:center;`（水平置中）
`align-items: flex-start;`（垂直置頂）
![](https://i.imgur.com/pCdIr46.png)

4. 水平置中、垂直置底
`justify-content:center;`（水平置中）
`align-items: flext-end;`（垂直置底）
![](https://i.imgur.com/OVZAbV2.png)


### 2.5. align-content
> 高度依內容高度而定

1. 案例1
      `align-items: flex-end;`，置底
      `align-content: center;`
			`item{height:600px}`   
      `item3{height:150px}`
![](https://i.imgur.com/TIlCOXH.png)

### 2.6 flex-direction

### 2.7 flex-wrap




##### 兩層class
`<div class="item item1">1</div>`，可分別對item和item1作設定



---
# 3. 子層的設定


## 3.1. order 順序
- 大於0：往尾端的方向移動
- 小於0：往起點的方向移動
- 數字越大越往末端排
- order值一樣時，則照原順序排列。
- 原始碼不便，但顯示的位置不同。

##### 練習1:54213
- 寫法1：依照數字大小排序
![](https://i.imgur.com/tbHCUmS.png)
- 寫法2：倒序 + 3拉到最後面
- 寫法3：利用基本的順序作變化（先寫的在前面）
![](https://i.imgur.com/rjuryVy.png)
- 即使折行，也還是會照著順序排列

##### 練習2：順序更動+高低交錯
- 寫法1：排序、折行、調整高度、調整外距
![](https://i.imgur.com/0l6JFjT.png)
- 寫法2：分兩欄，左1234，右56
![](https://i.imgur.com/VKhu9MJ.png)



## 3.2. boxmodel的計算
- flex-basis 基本值：控制物件主軸的長度。
- flex-shrink 收縮值：設定為0，會超過父層的寬度。設定為1，會等量收縮。
- flex-grow 成長值：會將剩下主軸的長度分配給設定的份額，份額依設定的數值總量決定。
	- 只有一個設定，其他的保持原樣，有設定的會取得剩下的長度。
	- A(2),B(1),C(1)，則A會佔1/2，BC則各佔1/4。

##### 課堂練習：四列圖文，左右交叉
![](https://i.imgur.com/5FU2FOk.png)
 - 寫法1：flex-order排序
 - 寫法2：圖文左右交叉，設定偶數行的反向
`.wrap .item:nth-child(even){flex-direction: row-reverse;}`
 - 寫法3：使用選取器nth-of-type(odd)或nth-of-type(even)
 ![](https://i.imgur.com/KXaIpyv.jpg)

 - 寫法4：使用選取器nth-of-child

---
#### vertical-align 垂直置中
- 必須是inline性質的物件（包含inline-block）
- 使用baseline需注意，對齊的是文字的基準線（表示會多出一小段）

---
##### 小作業
這兩者的差異
```htmlmixed=
	:nth-last-child
	:nth-last-of-type
```

---
### 附件
- [上課範例檔案](https://discord.com/channels/748042598983401482/748046752870826045/775641473781596180)


