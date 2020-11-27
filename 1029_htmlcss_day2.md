# 1029_htmlcss_day2

#### 上課日期：1029
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
# 0. 今日綱要 / 目錄
> 1. [表單](https://hackmd.io/3QgapOxBSk-Pg9nqGtSyHg?both#1-%E8%A1%A8%E5%96%AE)
> 2.  
> 3. 

# 1. 表單
### 以網站的會員資料為例：一個表單會有什麼資料？
> 怎樣的資料適合怎樣的呈現？使用者會怎樣使用？如何操作？
 - 下拉選單：
     - 星座
     - 最高學歷
 - 單行文字：
     - 姓名
     - 帳號
     - 信箱
     - 密碼
     - 電話
     - 職業
     - 身分證字號
     - 推薦人
     - 商品名稱
     - 地址：
         - 行政區的區分？
         - 一般為下拉選單，北部都放前面、筆畫少的放前面。（有時會有拼音排序）
         - 台鐵的網站為另一種想法：先篩選區域，再進行細部選擇。雖然多一個動作，但單一操作上較為簡潔。
 - checkbox：
 - 多行文字/textarea：
     - 留言
     - 商品簡介
     - 評論
     - 自我介紹
     - 對話框（chatbot）
 - 特殊：
     - `form`+`input`


```htmlmixed=
<form action="">
  <label for="user_name">姓名</label>
  <input type="text" id="user_name">
  <!-- 
   - 這種寫法，上面的for的值，要跟下面的id的值一樣。
   - 功用為點選欄位名稱時，游標可以自動跳到欄位裡面，以方便輸入
  -->
<br>

<label>
姓名
  <input type="text">
</label>
```
- 上面屬性裡面type的選擇，在電腦前看不出來，但在手機上差別就很明顯，填寫對應欄位時會挑出相應的虛擬鍵盤
- [HTML` <input> `type Attribute (W3SCHOOL參考整理)](https://www.w3schools.com/tags/att_input_type.asp)

### 在手機上預覽
 1. VScode開啟Go Live（右下角），以伺服器模式進行，開啟後會顯示port號
 2. 在左側網頁檔案上，右鍵可以live server模式在瀏覽器開啟
 3. 確定ip為何 
     - mac：左上角蘋果 > 系統偏好設定 > 網路 > 狀態 > ip 
     - pc：命令提示字元(cmd) > $ ip config > 查看ip v4
 4. 把電腦的網址中`:`前的網址替換成剛剛找的ip
 5. 安裝chrome套件 - [the QR code extension](https://chrome.google.com/webstore/detail/the-qr-code-extension/oijdcdmnjjgnnhgljmhkjlablaejfeeb?hl=zh-TW)
 6. 手機與電腦調整成相同網域
 7. 以手機掃描QRcode以進行檢視

### 標籤的選擇
> 成對的標籤，對空間的分配會比較明確
```
<input type="button" value="送出資料">
<button>送出資料</button>
```
 - 同樣都是按鈕，但下面的較常使用，較適合CSS。

### checkbox  
    <label>
       <input type="checkbox" id="user_name">
       不睡覺
    </label>
- [ ] checkbox

### radio
```
<label>
    <input type="radio" name="aa">
    是
</label>
```
### figure
 - `figcaption` 作敘述圖片，以區隔其他內文標籤，例如`<p>`
### picture
 - 某些功能RWD常用
*(02:00pm前)*
---

- [tag支援度查詢-can i use](https://caniuse.com/)




---

# 2. CSS    
> 負責處理視覺的部分 
> 如何只用文字來描述網頁的長相、特徵（屬性）
>  (14:00pm)

## 2.1. 基本介紹
> 什麼是CSS
> CSS撰寫方式及語法規則
 - 設定完要使用分號(;)結尾
 - 寫在html的tag內的屬性，也叫inline style
   `<p style="color:green; font-size: 20px;">`
 - 寫在head裡的style
      ```htmlmixed=
        <head>
            ......
          <style>
            p{
              color:red;
              font-size: 20px;
            }
          </style>
        </head>
      ```
- 參考範例
![](https://i.imgur.com/i7R1lH1.png)
    > 紅色為html寫法，紫色為css寫法
    
## 2.2 選取器
- `class` ([金魚](https://ithelp.ithome.com.tw/articles/10217192))
在tag裡設定class，選取器以`.class名稱`選取；同一個class可指定給多個tag
- `id` ([金魚](https://ithelp.ithome.com.tw/articles/10217585))
在tag裡設定id，選取器以`#id名稱`選取；一個id只能指定給一個tag
- 層疊式宣告 ([金魚](https://ithelp.ithome.com.tw/articles/10218978))
- `*`全選

### 同時對標籤與屬性下命令
 - 優先權：id > class > tag >
 - CSS設定或`<style>`裡，重複設定的對象，後面的設定會蓋掉前面的
 - **優先權原則:明確性越高、獨特性越高，優先權越高** 
 - id:可以用減號、底線、英數，但字首不可為數字

### 常見錯誤
- 有時候沒有反應可能是多了空格，或是全形的問題

### 課堂練習
- 練習 *(03:10pm)*
    - 練習使用不同階層的選取器
    - 五個段落
    - 第一段：
        - 淺灰色的背景：#ddd
        - 文字色彩：#666
        - 強調strong = #fa0
    - 其他段落：
        * 其他文字色彩：#666
        * 強調strong = #333
- 老師示範多層框的控制（顏色、虛線實線、邊界距離等等屬性）（15:25）
- 選取器的觀念很重要，後面javascript也會用到

### 延伸閱讀
- [金魚都能懂的CSS必學屬性 page3](https://ithelp.ithome.com.tw/users/20112550/ironman/3803?page=3)



---

## 優先權
> 說明這部分是什麼
1. 常見優先順序：!important > inline style > id > class > tag > * > 繼承
    - inline style：寫在tag裡面的屬性後面
    - !important：有最高權限，不是通則，是特例，直接指定。
    - 如果 在class和id裡面都有!important，則會顯示id裡面的!important，因為id的權限比class高。
    ```htmlmixed=
    #box{
    color: pink !important;
    }
    .box{
    color: maroon !important;
    }
    ```


---
## 課堂作業
 - 寫一個table (16:20)
   - 跟表格相關的標籤有什麼
   - 這些標籤的功用是什麼
   - 合併儲存格怎麼做（上下合併、左右合併）
   - 參考資料
       - [(金魚)](https://ithelp.ithome.com.tw/articles/10222225)
        - [HTML 表格 (table) 結構化、合併和群組教學範例 - MIS 腳印](https://www.footmark.info/web-design/html/html-table-structured-merge-group/)

## 延伸閱讀
- [玩轉 CSS FLEX | CSS教學 | 網頁教學 | 網頁設計](https://youtu.be/_nCBQ6AIzDU)(youtube影片)
- [什麼是16進位色彩?](http://csscoke.com/2015/01/01/rgb-hsl-hex/)


---
# 附錄
- [Chrome內建QRCode產生器，免外掛將網址直接轉為QR碼](https://www.techbang.com/posts/80849-chrome-built-in-qr-code-generator) 
- [網頁色彩碼](http://csscoke.com/2015/01/01/rgb-hsl-hex/) ：RGB、HSL、Hex
- [心智圖法：xmind](https://www.xmind.net/xmind8-pro/)

