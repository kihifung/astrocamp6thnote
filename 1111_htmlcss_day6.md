# 1111_htmlcss_day6

[![hackmd-github-sync-badge](https://hackmd.io/89Znenj0RdmayDkbMEdkEQ/badge)](https://hackmd.io/89Znenj0RdmayDkbMEdkEQ)

---
#### 上課日期：1111
###### tags: `html/css`
###### tags: `5xruby`


---
# 相關連結:
- 還沒看的，趕快去看啦!!! [AMOS老師 - 金魚都能懂的網頁教學(清單)](https://www.youtube.com/playlist?list=PLqivELodHt3iL9PgGHg0_EF86FwdiqCre)
	- 建議看：[金魚都能懂網頁設計入門:怎麼學CSS](https://youtu.be/h7wJ2YZarFc)，並整理出心智圖！
- 建議看：[金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/users/20112550/ironman/3803?sc=iThelpR)
- [金魚都能懂的網頁切版(清單)](https://www.youtube.com/playlist?list=PLqivELodHt3hxeuLX8PYaI8u1GcDaBoJo)
- [金魚都能懂的Bootstrap5網頁框架開發(清單)](https://www.youtube.com/playlist?list=PLqivELodHt3jq3oWBZfdhMu0GE7774HBW)
- [position-金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/articles/10253500)
- [AstroCamp課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)

---
# 0. 綱要/目錄
- [ ] 1. 定位position
- [ ] 2. 偽元素





---
# 1. 定位position
## 1.1. 定位的分類
* static
* fixed
* absolute
* relative
* sticky（炫炮性質）

## 1.2. position的相關性質
- 只要是block，寬度就是空間的寬度。但div就是內容的寬度。

## 1.3. 五個有position才有用的屬性
- top
- right
- bottom
- left
- z-index
### 1.3.1. fixed
#### 屬性衝突時
- 同時設定多個衝突屬性時，前面的才有效。但搭配margin時，會有**置中**的效果。前提是物件有設定尺寸。
> 範例![](https://i.imgur.com/xeuJYXT.png)
#### TRBL的應用
![](https://i.imgur.com/3JLj3jP.png)
#### 兩個box
![](https://i.imgur.com/5xamqfB.png)
#### 重疊 z-index
![](https://i.imgur.com/Rdzx7xI.png)


### 1.3.2. 絕對定位 absolute


### 1.3.3. 相對定位 relative

:::spoiler
快速生成五十個項目的清單
`ul>li_{$}*50 + tab`
```
結果：
<ul>
	<li>$</li>，$=1-50	
</ul>

```
:::
#### 練習：蓋板廣告
#### 練習：
#### 練習：
#### 練習：蝦皮頁面，商品圖上小標籤
#### 練習：三角形



---
# 2. [偽元素](https://developer.mozilla.org/zh-TW/docs/Web/CSS/pseudo-elements)
- [`:before`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::before)
- [`:after`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::after)
- 一定要有content屬性，即使是空的
- 常用在裝飾性的項目上面（範例010.html）


## [虛擬類別/偽類（Pseudo classes）(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/CSS/Pseudo-classes)
- 先前講過的偽類：
	- `:hover` 滑鼠停留時，套用指定選擇器的樣式。
	- `:visited` 拜訪過的
	- `:checked `內容的狀態


---

