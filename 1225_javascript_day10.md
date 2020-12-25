# 1225_javascript_day10

[![hackmd-github-sync-badge](https://hackmd.io/tQNgwrnNTbarqqqtQ6Eodg/badge)](https://hackmd.io/tQNgwrnNTbarqqqtQ6Eodg)


#### 上課日期：1225
###### tags: `javascript`
###### tags: `ruby`
###### tags: `5xruby`

---



---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
 - [範例檔(codepen)](https://codepen.io/collection/61ca9f9a0393b8991e38d2b3142e448d)
 - [課程補充教材(hackmd)](https://hackmd.io/ch89gwwaRJu9-LRQyisGPg)

---
# 0. 綱要/目錄
[TOC]



---
### 練習 001_multipleBy2

```javascript=
function multipleBy2(n) {
  // 實作
}

console.log(multipleBy2(2)) // 印出 4
console.log(multipleBy2(3)) // 印出 6
```

### 練習 002_doubleElement

```javascript=
function doubleElement(arr) {
  // 實作練習
  const result = [];
  for(let i = 0; i < arr.length; i++) {
    result.push(arr[i] * 2)
  }
  return result
}

const list = [1, 2, 3, 4, 5]
console.log(doubleElement(list))  // 印出 [2, 4, 6, 8, 10]
```
- 使用map
```javascript=
function doubleElement(arr) {
  return arr.map(function(item) { return item * 2} )
  return arr.map((item) => { return item * 2} )
  return arr.map(item => { return item * 2} )
  return arr.map(item =>  return item * 2)
  return arr.map(item => item * 2)
}
```
- 第2-6行，為同樣意思，但不同寫法（繁->簡）

### 練習003_squareElement
```javascript=
function squareElement(arr) {
  // 實作練習
  return arr ^ 2
}

const list = [1, 2, 3, 4, 5]
console.log(squareElement(list))  // 印出 [1, 4, 9, 16, 25]
```


---
#### 寫函數的目的
* 重複使用
* 給那段code意義

---
### 練習 004
```javascript=
function hello() {
  console.log('hi')
}

const a = hello()
console.log(a)
```

// 執行後會先出現 hi（第五行），再出現undefined（第六行）

### 練習 005
```javascript=
function funcGenerator() {
  function doubleElement(arr){
    let result = []
    for (let i = 0; i < arr.length; i++) {
      result.push = (arr[i] * 2)     
    } 
    return result
  }
  return doubleElement
}
const list = [1, 2, 3, 4, 5]
const a = funcGenerator()
console.log(a(list));
```
---
#### 書籍介紹 You Don't Know JS: Up & Going
- [中文版](https://www.tenlong.com.tw/products/9789863479666)
- [英文版](https://www.tenlong.com.tw/products/9781491924464)
- 作者建議：不要用匿名函數，因為出錯不好找出原因。
- 龍：想函數名字很麻煩，「心靈上支持作者的想法」。

---
### 006

```javascript=
function doubleElement(arr) {}
function squareElement(arr) {}

function myMap(arr, action) {
  const result = []
  for(let i = 0; i < arr.lengh; i++ ){
    result.push(action(arr[i]))
  }
  return result
}

function double(x) {return x * 2}
// const double = x => X * 2
function square(x) {return x * x}
const list = [1, 2, 3, 4, 5]

console.log(myMap(list, x => x * 2));
console.log(myMap(list, square));
```
---
#### 高階函數 higher order function
- 可以接受其他函數當作輸入的函數
- [說明(wiki)](https://zh.wikipedia.org/zh-tw/%E9%AB%98%E9%98%B6%E5%87%BD%E6%95%B0)

#### 閉包 Closure
- [說明(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Closures)
- 閉包（Closure）是函式以及該函式被宣告時，所在的作用域環境（lexical environment）的組合。
- 使用閉包讓你的function有記憶功能，用於像是計數器

#### let跟var的差別
- let必須先宣告才能用



---
### 007
- 程式碼與說明和執行結果↓↓↓
    - ![](https://i.imgur.com/muzyfoE.png)
    - ![](https://i.imgur.com/ek7T6I3.png)


### 008 Scope chain練習
- 程式碼與說明和執行結果↓↓↓
    - ![](https://i.imgur.com/GQr492g.png)


### 009
- 程式碼與說明和執行結果↓↓↓
  - ![](https://i.imgur.com/0LYO9qg.png)


#### IIFE
- IIFE = Immediately Invoked Function Expression
- 是一個定義完馬上就執行的 JavaScript function
- [說明(mdn)](https://developer.mozilla.org/zh-TW/docs/Glossary/IIFE)
- 常見的設計模式，包含兩個主要部分：
  - 第一個部分是使用Grouping Operator () ，包起來的 anonymous function。這樣的寫法可以避免裡面的變數污染到 global scope。
  - 第二個部分是馬上執行 function 的 expression ()，JavaScript 引擎看到它就會立刻轉譯該 function。
- 範例： 
```javascript=
(function () {
    var aName = "Barry";
})();
```
  - 上面原本函數外的括弧()()
  - 可以塞參數在後面
- 想寫套件的話，起手式可用IIFE
- 範例：jQuery，jQuery就是一個大的IIFE

---
#### [37 Essential JavaScript Interview Questions](https://www.toptal.com/javascript/interview-questions)
- 常見考題：
- [What will be the output of the following code:](https://bit.ly/2BBHINI)
```javascript=
for (var i = 0; i < 5; i++) {
	setTimeout(function() { console.log(i); }, i * 1000 );
}
```
- 圖示：
    -  ![](https://i.imgur.com/CAmIPLc.png)
- 結果會印出五個5
- 為什麼？
- 修正：i會依序變化
    - ![](https://i.imgur.com/oFQSNTg.png)
---
- 艱深考題：
- [What will the code below output to the console and why?](https://bit.ly/2hSLYTO )

```javascript=
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));
```
- `a = b = 3`，會先執行後面的`b = 3`

---


# Rails-補
> 購物車(續)、stimulus js
> > 將商品加入購物車時，購物車的數字立即變動

##### 關鍵字：
- stimulus js custom event
- [javascript customevent data(mdn)](https://developer.mozilla.org/zh-TW/docs/Web/API/CustomEvent/CustomEvent)



---
# 附件
- [leaflet](https://leafletjs.com/) 
  - an open-source JavaScript library for mobile-friendly interactive maps
- [這裡是附件的標題](這裡放連結) 


