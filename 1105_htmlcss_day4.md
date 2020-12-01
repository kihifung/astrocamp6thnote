# 1105_htmlcss_day4

[![hackmd-github-sync-badge](https://hackmd.io/cZO5_tUKTpSjoBvqv5rpew/badge)](https://hackmd.io/cZO5_tUKTpSjoBvqv5rpew)

---
#### 上課日期：1105
###### tags: `html/css`
###### tags: `5xruby`


---
# 相關連結:
- 還沒看的，趕快去看啦!!! [AMOS老師 - 金魚都能懂的網頁教學](https://www.youtube.com/playlist?list=PLqivELodHt3iL9PgGHg0_EF86FwdiqCre)
- 建議看：[金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/users/20112550/ironman/3803?sc=iThelpR)
 - [web心智圖](https://cdn.discordapp.com/attachments/748046752870826045/771393916825894942/web.xmind)
 - [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)


---
# 0. 綱要/目錄
- [ ] 1. 作業review
- [ ] 2. 區塊（block）
- [ ] 3. margin的特性
- [ ] 4. inline與block的比較
- [ ] 5. 學習技巧



---
# 1. 作業review
1. 遇到什麼問題？
    1. 尺寸怎麼抓？ 
    2. 版面配置
    3. 垂直置中
    4. 線條
    5. 顏色
    	- 顏色抓取工具 
    7. icon
		- 用icon-font
1. 怎麼做
	  1.先分析尺寸，以看到的畫面來計算
	  2.先將版面排好（什麼東西放在哪裡）
	  3.
3. "+"：選取第一個物件(a)之後的物件(b)＝>被選取的是物件(b)
[金魚選取器](https://ithelp.ithome.com.tw/articles/10220656)

---
# 2. 區塊（block）

| 項目 | 解釋 | xxxx |顏色|
| -------- | -------- | -------- |-------- |
| width     | 內容寬 | content box  |藍色|
|padding  |邊框與內容之間|  |綠色|
| border |padding外的那條線  |  |黃色|
| margin | 物件與物件或物件與空間的距離 |  |橘色|
	
![](https://i.imgur.com/YPtx4EQ.png)
- 延伸閱讀：[金魚box-sizing](https://ithelp.ithome.com.tw/articles/10252827)


---
# 3. margin的特性
- margin:上右下左;
- margin:上下_右左;
- margin:上_右左_下;
- margin:上_右_下_左;
- margin:auto  將剩餘空間平均分配
	- margin:0 auto 0 auto 水平置中


---
# 4. inline與block的比較
| 項目 | Inline | Block |Inline-block|
| -------- | -------- | -------- | -------- |
|Width |  x   |   o   |o|
| Height |  x   |   o   |o|
|Margin 上下 |  x   |   o   |o|
|Margin 左右 | O |  O  |O|
|Padding 上下 | x   |   o   |o|
|Padding 左右|O |  O  |O|
|預設排列方向| 橫 | 直 |橫|
|橫排的方式| 預設 |父層-flex / 本身-float |預設|
|空白字元| 保留 |沒這問題 |保留|
|垂直對齊vertical-align| 支援	    | 不支援 |支援|
|文字水平對齊text-align| 支援  | 物件本身沒作用 |支援|







---
# 5. 學習技巧
> 知道哪裡有問題，前後比較才知道差異
- 紀錄問題：
- 計算時間：工時的評估。瞭解彼此的差異。做為精進的參考。

---
# 作業
- 導覽列的選項，左右都要有分隔線
- 範例如圖(pchome)
![](https://i.imgur.com/6Ngs4Hq.png)



---
# 附件
- [flex定位小遊戲](https://flexboxfroggy.com/) 
- [上課範例檔案](https://discord.com/channels/748042598983401482/748046752870826045/773831901118595073)

---
# 預習
- CSS的reset(金魚)




