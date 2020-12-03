# 1202_javascript_day02

[![hackmd-github-sync-badge](https://hackmd.io/3FtzAAzrT72ex8gB8BaqUg/badge)](https://hackmd.io/3FtzAAzrT72ex8gB8BaqUg)

---
#### 上課日期：1202
###### tags: `javascript`
###### tags: `5xruby`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)


---
# 0. 綱要/目錄
- [ ] 網頁中的互動以及行為
  - [ ] 控制背景顏色
  - [ ] 使用按鈕控制背景顏色
  - [ ] 把按鈕改成開關
  - [ ] 動態建立元件 create-element
  - [ ] timer-jquery 計時器


---
- [投影片連結](https://ppt.cc/fD89Qx)
- [隨堂練習包](https://ppt.cc/fpeMux)
---

# 1. 網頁中的互動以及行為-以JS操控網頁

## 1.1 控制背景顏色
```htmlmixed=
  <style>
    html, body {  height: 100%; }
    body { background: #353535;  margin: 0;  }
    body.light {   background: #d4c370;   }
  </style>
```
```javascript=
  <script>
      document.body.addEventListener('click', function(){
         document.body.classList.toggle('light') 
      })
  </script>
```

## 1.2. 使用按鈕控制背景顏色
- 直接越過body，直接取用id
- 瀏覽器讀取網頁有方向：由上而下，所以控制後面的寫在前面會讀取不到。
- 使用DOMContentLoaded來處理

```javascript=
<script>
window.addEventListener('DOMContentLoaded', function(){
      document.getElementById('toggle').addEventListener('click', function(){
        document.body.classList.toggle('light')
  })
})
</script>
```
- 修改按鈕的文字
- 使用 `.textContent` 和 `this`
- js中的this 類似 ruby中的self
![](https://i.imgur.com/IhjJoVi.png)
- 在這裡`this` 等於`document.getElementById('toggle')`

#### 如果不想用this
- 有可能因為無法一目了然知道在指什麼
- 可考慮使用變數代替
- `const togglebtn = document.getElementById('toggle')`
- 原本this的地方，改成[變數]

## 1.3. 把按鈕改成開關
- 把原本的toggle改成 on/off，拆成兩部分來寫
```javascript=
<script>
    window.addEventListener('DOMContentLoaded', function(){
      document.getElementById('on').addEventListener('click', function(){
        document.body.classList.add('light')
      })
      document.getElementById('off').addEventListener('click', function(){
        document.body.classList.remove('light')
      })
    })
</script>
```
#### querySelector
- 效果類似css的選取器，基本上css選得到的都選得到
- 設定常數來取代重覆的地方
- 開關的效果相反寫
![](https://i.imgur.com/0xWcDBf.png)

#### 把js搬出去
- 就像css可以搬出去一樣，js也可以搬出去
- `<script src="main.js"></script>`

#### 瀏覽器 JS 中的 window
- 全域變數
- console.log 等同於 window.console.log
- window.document = document

#### location
- 重新導向
- 範例：`location.href = 'https://google.com'`

## 1.4. 動態建立元件 create-element
### 1.4.1. Create & append
* document.createElement(...)
* debugger
* parent.appendChild(el)
* 
### 1.4.2. 直接指定 innerHTML
* .innerHTML = ...
  > 透過指定字串建立 DOM，很強大
  > 要注意是否有使用者輸入的資料
--
- 使用者在textContent裡面寫的就是文字
- 
### 1.4.3. 刪除 DOM
##### .remove() = [`ChildNode.remove`](https://developer.mozilla.org/en-US/docs/Web/API/ChildNode/remove)
- The ChildNode.remove() method **removes the object from the tree it belongs to.**
- 回到父層刪掉自己
### 1.4.4. 放至指定位置
refEl.insertAdjacentElement('afterend', el)
- 'afterend'，位置的字串，插入的位置
  - 'beforebegin': Before the targetElement itself.
  * 'afterbegin': Just inside the targetElement, before its first child.
  * 'beforeend': Just inside the targetElement, after its last child.
  * 'afterend': After the targetElement itself.

##### 附加的code
- 加到js最下面
```javascript=
window.test = function(position) {
  const div = document.createElement('div')
  div.className = 'time'
  div.textContent = '! ' + position + ' !!' + (new Date()).toString()

  document.querySelector('.title').insertAdjacentElement(position, div)
}
```
## 1.4.5. timer-jquery 計時器
- 引入 [jQuery](https://code.jquery.com/)
- 選擇 minified ，複製`<script>`那部份
- 檢查是否引入成功，在devtools的console裡面鍵入 `jQuery.fn.jquery`。如果成功的話會跳出版本編號。

### 基本計秒功能
`<script>` 引入 jQuery
```javascript=
$(window).ready(callback)
$(...).click(callback)
$(...).text(...)
setInterval(callback, milliseconds)
```

### 暫停功能
```
timer = setInterval(...)
clearInterval(timer)
```
BTW, 只跑一次的
```
timeout = setTimeout(...)
clearTimeout(timeout)
```

### 來點效果
* $(...).slideDown() / $(...).slideUp()
* $(...).prependTo() / $(...).appendTo()
* 最後來點速度感：更動 數值大小


---


# 2. 名詞解釋： 
## DOM
- Document Object Model
- HTML 元素在 JavaScript 的界面
- 前面看到的Document～
- [說明(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/API/Document)

---
## jQuery
- 一般市面常見js框架
- 新的多用react和vue
- 常見特徵： $ / $()
- [api Doc](https://api.jquery.com/)
- `document.querySelector()` => `$()`
---

# [作業](https://discord.com/channels/748042598983401482/748046752870826045/783642279276445727)
- 用原生 DOM API 改寫 05_timer-jquery




---
# 附件
- [Web API 心智圖](https://drive.google.com/file/d/1KLNmPTFkvzWGTYuoMsQDG9WZcHgyC9dj/view) 



