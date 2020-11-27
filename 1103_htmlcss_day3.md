# 1103_htmlcss_day3

#### 上課日期：1103
###### tags: `html/css`
###### tags: `5xruby`


---
# 相關連結:
- 還沒看的，趕快去看啦!!! [AMOS老師 - 金魚都能懂的網頁教學](https://www.youtube.com/playlist?list=PLqivELodHt3iL9PgGHg0_EF86FwdiqCre)
- 建議看:[金魚都能懂的CSS必學屬性](https://ithelp.ithome.com.tw/users/20112550/ironman/3803?sc=iThelpR)
 - [web心智圖](https://cdn.discordapp.com/attachments/748046752870826045/771393916825894942/web.xmind)
 - [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
 - [資源網站-MDN](https://developer.mozilla.org/zh-TW/docs/Web/HTML)：標籤等資訊查詢
 - [資源網站-caniuse](https://caniuse.com/)：tag支援度查詢

---
# 0. 綱要/目錄
- [ ] CSS優先權
- [ ] CSS的位置


---
# 1. CSS 優先權
> 不同屬性顯示的先後順序
1. 繼承
    1. 文字相關的屬性才會有繼承的問題
1. 為什麼不用分數的算法
  	1. 有盲點，必須確定設定的對象相同，才能比較
3. 篩選條件
	- 選取器就是一種篩選條件
	- 範例：(h1和box都選取)
	```htmlmixed=
	<style type="text/css">
		 h1.box{color:red}
	</style>
	```
	- not屬性

4. 冒號
	- 一個冒號：都是偽類(Pseudo Classical)superclass
	- 兩個冒號：偽元素(pseudo-element)

:::warning
- 注意冒號前的空格
```htmlmixed=
<style type="text/css">
        p#amos span{color: #ffaa00;}
        p:hover{color: red;}
        p :hover{color: blue;}
</style>
```
:::
:::info
#### 假文生成
- lorem
- ctlorem
#### 假圖生成
- fakeimg
- picsum
###### *打前幾個字 + tab ＝> 自動抓取 (vscode)
:::

5. hover
 - overflow


# 2. CSS的位置
> 實際內容在檔案中的位置
1. style
  - 讀取網頁時，會先讀取html（DOM），再來是css和javascript。
  - 寫在哪裡都可以（head/body/html外等等），但是....
  	- 寫在head：先顯示xxx  才變成
  	- 寫在body：先讀取xxxx
2. 把css拉出來寫
	- 多個網頁時，只要一個css檔就好（位於同一層）
3. flex
- 將內容轉向（橫向）
- 在屬性內設定：`display:flex;`




# 作業
- 做一個網頁
- 目標：
 ![](https://i.imgur.com/jparxVo.jpg)
- 分組交作業（面對出口）：(5)左、(2)中右、(3)中左、(4)中後、(1)右
- 11/4四上課前交
- 交一個資料夾（壓縮檔），檔名：組別－姓名
- 資源：[小圖icon](https://imgur.com/a/og8CsoI)

---
# 預習-金魚
- 下次上課前必預習 金魚網頁設計入門day8、10、 11、 12（區塊尺寸計算、換個新盒子）
- 金魚都能懂的CSS必學屬性 系列(day27~29)






