# 1127_ruby_day10_javascript_day0

[![hackmd-github-sync-badge](https://hackmd.io/0mIS-lNgRiWiYGz4jzfX1Q/badge)](https://hackmd.io/0mIS-lNgRiWiYGz4jzfX1Q)

---
#### 上課日期：1127
###### tags: `ruby`
###### tags: `5xruby`
###### tags: `javascript`

---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)



---
# 0. 綱要/目錄
- [ ] 程式語言簡史
- [ ] JavaScript初探
- [ ] rails專案(續)
	- [ ] webpack



---
# 1. 程式語言簡史
- python, java, php, ruby, javascript等語言都在1990年代早期誕生，多少跟windows的普及有關（Matz）
- [Javascript(wiki)](https://zh.wikipedia.org/wiki/JavaScript)
- [JavaScript 是什麼?(MDN)](https://developer.mozilla.org/zh-TW/docs/Learn/JavaScript/First_steps/What_is_JavaScript)

---
# 2. Javascript初探
1. 變數
- 使用前要先宣告var(指定特定區域，例如在function裡宣告) 
- 如果不使用var的話，會變成全域變數
> [color=#bf6211]面試題：js宣告變數時，有沒有加var差在哪裡？

- 分號記得要加
```javascript=
var a = 1;
```

2. window <br>
 指現在這個頁面本身
4. context
5. function

- undefined 未定義：有這個東西，但是還沒有定義這個東西是什麼
- not defined 沒有定義：沒有這個東西

##### 變數提升 variable Hoisting
- [說明(MDN)](https://developer.mozilla.org/zh-TW/docs/Glossary/Hoisting)
##### 語言的類型：編譯與直譯 Compilation vs Interpretation
- 編譯：c, java
- 直譯：ruby, js(過程中有部分在執行編譯)


##### js的建立期與執行期
1. 建立期：
    - 1A. 註冊名稱（取得變數名稱） Identifier
	- 1B. 進行初始化
    
2. 執行期： 2. 執行函數/變數 <br>
        *邏輯判斷在這段執行*

> [color=#bf6211]面試題：什麼是變數提升

##### 另一種變數宣告 let
- 問題：let 跟 var 差在哪？
```javascript=
console.log(a) 
let a = 1
```
- 錯誤訊息：Uncaught ReferenceError: Cannot access 'a' before initialization

##### 暫時死區 TDZ（Temporal Dead Zone）
let會先把宣告的變數做**暫時死區**
> [color=#bf6211]面試題：什麼是TDZ？
- 有些人說let就是新版的var：大部分的時候是
- js會在建立期的時候，將全部的變數都先定義完。

#### 其他語法使用
- `document.querySelector()` 抓取參數帶入的選取器所指定的一個(HTML)元素
- `document.querySelectorAll()` 抓取參數帶入的指定選取器的多個元素
- `document.getElementById()` 抓取指定id的元素
- `innerHTML` <br>
  HTML
  ```htmlmixed=
  <div id="abc">123</div>
  ```
  JS
  ```javascript=
  var e = document.getElementById('abc');
  e.innerHTML = "<h1>456</h1>";
  ```
  網頁渲染出來結果會是h1標題大小的`456`
- `innerText` <br>
  以上例來說，改用innerText只會替換tag裡面的字元，不會把字串裡寫到的tag憶起渲染，只是單純的抓字元，所以JS會渲染成普通字大小的`<h1>456</h1>`
- `classList`
  在動態時指定
- `addEventListener`
- `preventDefault` <br>
  舉例
  ```javascript=
  addEventListener("click",function(evt){
  evt.preventDefault();
  alert(evt.target);
  })
  ```
  

##### html的id屬性
> [color=#bf6211]面試題：class和id有什麼不同
- js在 GetElementByID時 只可控制id，但無法控制class
- [ID選取器(金魚)](https://ithelp.ithome.com.tw/articles/10217585)

##### DOM (Document Object Model) 文件物件模型
- [說明(wiki)](https://zh.wikipedia.org/zh-tw/%E6%96%87%E6%A1%A3%E5%AF%B9%E8%B1%A1%E6%A8%A1%E5%9E%8B)
- [說明(w3c)](https://developer.mozilla.org/zh-TW/docs/Web/API/Document_Object_Model)
- DOM提供了一個文件（樹）的結構化表示法，並定義讓程式可以存取並改變文件架構、風格和內容的方法。提供了文件以擁有屬性與函式的節點與物件組成的結構化表示。(MDN)

##### 寫法
- js 小駝峰
- ruby 蛇式

> [color=#bf6211]
問：method和function有什麼不一樣？<br>
問：參數、引數有什麼不一樣？

##### Event.preventDefault()
- 如果事件可以被取消，就取消事件（即取消事件的預設行為）。但不會影響事件的傳遞，事件仍會繼續傳遞。
- [說明(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/API/Event/preventDefault)



## 名詞
- scope chain
- execution context
- scope chain
- runtime
- stack
- stack overflow
- tree shaking
---
# 3. Rails專案(續)
![](https://i.imgur.com/wjDqeEU.png)
第四行的`require("channels")`是預設指向名稱`channels`的同層資料夾裡的index.js。


##### 啟動webpack的server
`bin/webpack-dev-server`
- 用node寫，比rails快很多，用來跑js比較好


##### RWX

`drwxr-xr-x `
`-rwxr-xr-x`
d上一層為資料夾，- 為檔案

* R:read
* W:write
* X:execute


|user自己 | group | others |
| -------- | -------- | -------- |
| RWX     | RWX     | RWX     |

 


`$ chmod u+x ./aaa` 此指令意思是幫user(/aaa這個檔案)加X(execute)的權限

> 二進位
> chmod 777 (rwxrwxrwx)
> chmod 666 (rw-rw-rw-)
> chmod 444 (r--r--r--)



---







---
# 預告
- 下次要在js裡面塞ruby code~


# 附件
- [js投影片](https://speakerdeck.com/eddie/learn-javascript-well) 


