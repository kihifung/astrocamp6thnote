# 1209_javascript_day04
> #### 透過 JavaScript 進行 HTTP 請求 & 非同步

[![hackmd-github-sync-badge](https://hackmd.io/s_wCvJCIRdqsJ0x7DCxVDQ/badge)](https://hackmd.io/s_wCvJCIRdqsJ0x7DCxVDQ)



---
#### 上課日期：1209
###### tags: `javascript`
###### tags: `5xruby`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)



---
# 0. 綱要/目錄
- [ ] HTTP request via JavaScript
- [ ] Asynchronous / 非同步
- [ ] http POST via JavaScript
  - [ ] fetch / then
  - [ ] async / await


---
# 1. HTTP request via JavaScript

#### chrome dev tools
- network頁面的disable cache和 preserve log
- 開發中要把(檢視瀏覽器裡的)Network裡的Disable cache打開，通常會打勾，確定是最新版。

##### fetch(...)
- 提供了一個能獲取包含跨網路資源在的資源介面。它有點像我們所熟悉的 XMLHttpRequest。
- 讓靜態頁面中可以動態呈現（以javascript去遠端抓取資料）
- [(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/API/Fetch_API)
- 在 fetch(...) 出現之前：
  * `$.ajax()`
  * `XMLHttpRequest`
```javascript=
fetch(...)
  .then(request => request.json())
  .then(posts => { ... })
```

##### Posts API server
- [Git repository](https://github.com/5xTraining/pastleo-js-posts-api)
- [實作範例](https://pastleo-posts-api.herokuapp.com/posts)

##### JSON
- `{}` (物件)裡包的鍵值一定要用字串`""`方式



##### Arrow Function
- [箭頭函式(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
  > 擁有比函式運算式還簡短的語法。它沒有自己的 this、arguments、super、new.target 等語法。本函式運算式適用於非方法的函式，但不能被用作建構式（constructor）。
  
例
```javascript=
var test = (a, b) => a + b
test(1, 2)
// 3
```

### template strings 樣板字面值
- [MDN說明](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Template_literals)
- 一種新的寫法，使用反引號"\`"來包裹
- 範例：


#### CORS 跨來源資源共享
- [Cross-origin resource sharing(wiki)](https://zh.wikipedia.org/zh-tw/%E8%B7%A8%E4%BE%86%E6%BA%90%E8%B3%87%E6%BA%90%E5%85%B1%E4%BA%AB)

---
# 2. Asynchronous / 非同步
- 非同步語法問題：Callback hell
 > 為了執行非同步，可能會造成程式碼太多層
- 解法：使用promise

- [延伸閱讀](https://realdennis.medium.com/callback-hell-%E8%88%87-promise-%E4%B8%80%E8%B5%B7%E4%BE%86%E6%8A%8A-settimeout-%E5%B0%81%E8%A3%9D%E6%88%90-promise-%E5%90%A7-e542ef84967f)

#### async function
- 寫法：
```javascript=
async () => {}
async function() {}
async function name() {}
```
- 預設會回傳 Promise
- 可用 await 關鍵字
  - `resolved = await promise`

* callback 改寫為 promise 
  1. 修改 執行的動作
  2. 修改 常數
  
  
  
---
# 3. http POST via JavaScript
> 範例9. 建立新增post的頁面，將資料上傳

#### fetch(url, options) 的 options
* url 與 posts index 相同
* 使用'POST'方法
* headers: { Authorization: '...' }
  * ... = pastleo-js-posts-api-secret 通關密語/key
* body: new FormData(form)
  * FormData

### 密語的設定
在[這裡](https://github.com/5xTraining/pastleo-js-posts-api/blob/master/app/controllers/posts_controller.rb#L105)設定：
/pastleo-js-posts-api/app/controllers/posts_controller.rb
```ruby=
def verify_api_authorization
      if request.headers['Authorization'] != 'pastleo-js-posts-api-secret'
        head :forbidden
      end
end
```

### 錯誤處理
* 錯誤處理
  * request.ok
  * 顯示錯誤訊息
* Loading 效果
* 防止重複送出
* 成功後清除輸入
* 
---


# 回顧 Recap
* fetch(...)
  * CORS
* new Promise(resolve => { ... })
* async / await




---
# 附件
### window 與 document
- 一般寫的
`window.addEventListener("DOMContentLoaded", function(){})` 和
`document.addEventListener("DOMContentLoaded", function(){})` 有一樣的效果，因為作用都是在document這一層。
- 但load方法在document會聽不到（詳見附圖）。
```javascript=
document.addEventListener("load", () => {
  console.log('聽不到！');
})
```
![](https://i.imgur.com/C9POkhV.png)
> 龍：要知道哪些層級（或元件）聽得到哪些事件，就得查找手冊了




