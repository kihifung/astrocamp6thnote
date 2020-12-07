# 1207_ruby_day13_vue

[![hackmd-github-sync-badge](https://hackmd.io/96KXn_ekSHCbZo3NSPWSMw/badge)](https://hackmd.io/96KXn_ekSHCbZo3NSPWSMw)

---
#### 上課日期：1207
###### tags: `ruby`
###### tags: `5xruby`
###### tags: `javascript`
###### tags: `vue`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
- 官方網站：[英文](https://vuejs.org/)、[中文](https://cn.vuejs.org/v2/guide/)、[重新認識 Vue.js | Kuro Hsu
](https://book.vue.tw/)

---
# 0. 綱要/目錄
- [ ] javascript的前端框架
- [ ] Vue.js



---
# 1. javascript的前端框架
##### 範例
```javascript=
var a = 1
var b = a * 2  

console.log(b)  // 2
a = 2
console.log(b)  // 2
```
- 因為處理b的程式只有在第2行被執行，所以在第4行和第6行時，不會受到其他影響。
- 變數之間不會連動。

#### 前端框架介紹
##### Reactive Programming
* facebook React.js   1st
* 個體戶 Evan You  Vue.js  2nd
* google Angular.js   3rd   
  - Angular改版後，不太好用，沒有很通行。
  - 除了原本的jQuery外，新的大多還是react和vue
  - [Vue.js紀錄片](https://youtu.be/OrxmtDw4pVI)
  - Honeypot這個頻道很多相關的紀錄片


---
# 2. Vue.js
- 漸進式框架 Progressive Framework
- 官方網站：[英文](https://vuejs.org/)、[中文](https://cn.vuejs.org/v2/guide/)、[重新認識 Vue.js | Kuro Hsu
](https://book.vue.tw/)
- 一開始先寫英文，後來應要求才有中文
- 使用CDN方式引入vue.js，在html原始碼中加入下面這行：
```htmlmixed=
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

:::info
##### CDN
- Content Delivery Network 或 Content Distribution Network
- [wiki說明](https://zh.wikipedia.org/zh-tw/%E5%85%A7%E5%AE%B9%E5%82%B3%E9%81%9E%E7%B6%B2%E8%B7%AF)：一種透過網際網路互相連接的電腦網路系統，利用最靠近每位使用者的伺服器，更快、更可靠地將音樂、圖片、影片、應用程式及其他檔案傳送給使用者，來提供高效能、可擴展性及低成本的網路內容傳遞給使用者。
:::

##### 範例

```htmlmixed=
<div id="app">{{ message }}</div>
```
```javascript=
new Vue({
  el: '#app', 
  data: { message: 'world123' }
})
```
- 結果會印出world123

##### 範例
![](https://i.imgur.com/3eVEtGC.png)
- v-model的v是vue的意思
- 這部份可以將v-model的內容轉換成{{message}}輸出(見下方的"123342")
- 更多（兩個輸入框）
- ![](https://i.imgur.com/EmKSCg9.png)


##### 物件與json
1. 紅框中的部分為js中的物件
2. json為js的物件表示法，所以會和紅框中的部分很像
    - 圖示：
      - ![](https://i.imgur.com/1ElfSE7.png)

##### DOM與Virtual DOM
- vue.js使用Virtual DOM：部分網頁渲染
- [DOM(mdn)](https://developer.mozilla.org/zh-TW/docs/Web/API/Document_Object_Model)

##### 範例
![](https://i.imgur.com/WvYi5GC.png)
![](https://i.imgur.com/PTjmbVM.png)


##### 網頁的生命週期
- [網頁的生命週期(kurohsu)](https://ithelp.ithome.com.tw/articles/10197335)

##### v-if和v-show
- v-if：隱藏物件
- v-show：不顯示
- [條件渲染(vue-cn)](https://cn.vuejs.org/v2/guide/conditional.html#v-show)



##### Single source of truth 單一來源真相
- [wiki說明](https://en.wikipedia.org/wiki/Single_source_of_truth)

---
##### v-bind
```htmlmixed=
  <div id="app">
    <a v-bind:href="url">連結</a>
    <button v-on:click="clickme">按我</button>
```
簡寫：
```htmlmixed=
  <div id="app">
    <a :href="url">連結</a>
    <button @click="clickme">按我</button>
  </div>
```
* v-bind:href = :href
* v-on:click = @click

##### 判斷
- 判斷輸入數字，給予不同結果
- `<input v-model="age">`和`<span v-if="age >= 18">`
```htmlmixed=
  <div id="app">
    年紀：<input type="text" v-model="age">
    <span v-if="age >= 18">已成年</span>
    <span v-else>18 禁</span>
  </div>
```
```javascript=
new Vue({
  el: '#app',
  data: {
    isAdult: true,
    age: '' },
  methods: {
    clickme: function(e) {
      console.log('clicked!'); },
  }
})
```

##### 課堂作業
- 把js部分做出來（可是純js或vue，html有需要可改）
- ![](https://i.imgur.com/p6ii246.png)

- javascript的寫法
```javascript=
document.querySelector(".bmi_btn").addEventListener("click" ,function(){
  // 提示：BMI = 體重(kg) / 身高(m) 平方
  const height = document.querySelector("#bodyHeight").value / 100
  const weight = document.querySelector("#bodyWeight").value
  const bmi = weight / (height * height)
  const result = document.querySelector("#resultText")
  result.innerHTML = Math.round(bmi*100 )/100;
})
```
- jQuery的寫法
```javascript=
new Vue({
  el: ".calculator",
  data:{
    height: '',
    weight: '',
    result: '0'
    },
  methods: {
    cal: function(e) {
      let value = this.weight/((this.height/100) * (this.height/100))
      this.result = parseFloat(value).toFixed(2)
    }
  }
})
```


##### vanilla.js
- [vanilla.js](http://vanilla-js.com/)
- 原生框架的一種稱呼
- [精通VanillaJS](https://www.ithome.com.tw/voice/106182)
---

##### v-for

---


##### Vue Lifecycle
[Vue Lifecycle Diagram](https://vuejs.org/v2/guide/instance.html#Lifecycle-Diagram)


---
### new一個專案
- 安裝vue

##### app.vue 元件檔
- 三個區塊控制前端的三個部分






---
# 作業
- 看完[vue中文官網](https://cn.vuejs.org/v2/guide/index.html)的影片 




