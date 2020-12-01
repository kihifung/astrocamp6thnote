# 1201_javascript_day01

[![hackmd-github-sync-badge](https://hackmd.io/aiG7HSulR0SWWMrS9Erm6w/badge)](https://hackmd.io/aiG7HSulR0SWWMrS9Erm6w)


#### 上課日期：1029
###### tags: `javascript`
###### tags: `5xruby`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)


---
# 0. 綱要/目錄
- [ ] 重點1
- [ ] 重點2
- [ ] 重點3
- [ ] 重點4
- [ ] 重點5


---
# 1. theme1



##### 變數宣告

###### 分號：在js可加可不加
- 預設會幫忙加，ASI（Automatic Semicolon Insertion）
  > 所以換行的話，就是另外的意思
- 如果要做換行，可以用`()`或`[]`包起來
###### 縮排：js習慣space*4


##### function
- 在ruby裡看不到

##### [lexical scope 語彙範疇](https://cythilya.github.io/2018/10/18/lexical-scope/)
##### js的註解是"//"
##### function裡面可以包function，ruby不行
##### block在js可以單獨出沒，ruby不行
---
##### var和let的分別
- 限縮var範圍的是function
- 限縮let範圍的是{ }
- var可重複宣告，取代前面宣告過的變數
- let宣告過的變數，已經用掉，不能重複使用
- [devtools(chrome)](https://developers.google.com/web/updates/2019/12/devtools)
- 從 chrome 80 開始，在 devtools 裡 let 跟 class 可以重複定義

##### const跟let
> const宣告常數，let宣告變數
const不能re-assign(不能改變指向某值)
```javascript=
const x = 2  // 2不能改
const x = [1, 2, 3]  // 可以改陣列裡面的內容
const x = {...}  // 可以改Block裡面的內容
```
- js 可重複宣告，後面的會覆寫前面的
---
微軟開發Typescript加強Javascript的型別
- 強型別:php、Java
- 弱型別:Ruby、Javascript
---
- sync 同步執行
- async 非同步執行

###### 匿名函數
- js的函數可以不用取名稱，稱為匿名函數，但有些人認為有寫名稱才方便辨識。

###### 單一執行緒，FIFO
- stack runtime queue

##### 非同步處理
> 面試題：setTimeout
- setTimeout 多少有誤差
- [event loop到底是什麼?(youtube)](https://www.youtube.com/watch?v=8aGhZQkoFbQ&ab_channel=JSConf)
- [範例網站](https://ubin.io/j7V2Nd)



---
#### 練習js
- 在chrome的console
- 在termial裡鍵入node，進入REPL模式


---
##### 數字
- js的數字就是數字，沒有整數和浮點數的差別

##### 重要bug
```javascript=
> typeof(null)
'object'
```
##### NaN

##### 比較
- 要比較兩個東西時，使用三個等號會比兩個等號精準
- 其實兩個等號有檢查型別（規範手冊上寫的）：如果一樣，就會使用三個等號進行比較。
- [手冊連結(2019)](https://www.ecma-international.org/ecma-262/10.0/index.html#sec-abstract-equality-comparison)
  - 7.2.14 Abstract Equality Comparison
- [手冊連結(2020)](https://www.ecma-international.org/ecma-262/#sec-abstract-equality-comparison)
  - 7.2.15 Abstract Equality Comparison
> If Type(x) is the same as Type(y), then
> Return the result of performing Strict Equality Comparison x === y.

##### var false
> `var null`
> * undefined
> * null
> * 0
> * ""
> * false
> * NaN


##### [嚴格模式](https://www.w3schools.com/js/js_strict.asp)
`"use strict"` <br>
寫在第一行或function裡的開頭。<br>
寫成字串是因為在執行字串時，就只是執行，沒有回傳也沒有印出東西。


---
##### 表達式與陳述句
- 表達式(Expression) 
- 陳述句(Statement)


##### 課程練習
- 如何將list[]變成兩倍？
```javascript=
const list = [1, 2, 3, 4, 5];
const result = list.map(function(x){
            return x * 2;
          })
console.log(result);
>> [2, 4, 6, 8, 10]
```
- 挑出奇數
```javascript=
const list = [1, 2, 3, 4, 5];
const result = list.filter(function(x){
            return x % 2 == 1;
          })
console.log(result);
>> [1, 3, 5]
```

##### js的this
龍：js裡最難的

##### template literal 樣板字面值


##### callback
- 什麼意思？
- 什麼時候該用？

##### callback

##### [NaN](https://zh.wikipedia.org/wiki/NaN)
- 表示未定義或不可表示的值。常在浮點數運算中使用。

##### 課堂範例
```javascript=  
const goku = heroCreator('悟空', 100)
console.log(goku);
goku.attack();

function heroCreator(name, power){
  const hero = {} //literal
  hero.name = name
  hero.power = power
  hero.attack = function(){
    console.log(`${this.name} 造成 ${this.power}點的傷害`);
  }
  return hero
}
>> "悟空 造成 100點的傷害"
```
```javascript= 
const goku = heroCreator('悟空', 100)
console.log(goku)
goku.attack()

function heroCreator(name, power) {
  // return {
  //   name, 
  //   power, 
  //   attack: function() { 
  //     console.log(`${this.name} 造成 ${this.power} 點的傷害`);
  //   }
  // }

  const hero = {}
  hero.name = name
  hero.power = power
  hero.attack = function() { 
    console.log(`${this.name} 造成 ${this.power} 點的傷害`);
  }
  return hero;
}
```
---



---
# 附件
- [JS面試題(github-lydiahallie)](https://github.com/lydiahallie/javascript-questions)
  - 可轉換成繁中版本

- [JS面試題(github-sudheerj)](https://github.com/sudheerj/javascript-interview-questions) 



