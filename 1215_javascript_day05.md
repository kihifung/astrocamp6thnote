# 1215_javascript_day05

[![hackmd-github-sync-badge](https://hackmd.io/l6sQ1L0RTOyhY7DxbFeY2g/badge)](https://hackmd.io/l6sQ1L0RTOyhY7DxbFeY2g)

---
#### 上課日期：1215
###### tags: `javascript`
###### tags: `5xruby`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)


---
[TOC]

# 今日重點
  - OOP
  - this

---
# 0. 網路穩定性雜談
- 1214 google大當機
- 業界標準：99.99% 
- 電信業的穩定，熱更新（不停機的更新）
- elixir：
  - 發明來處理熱更新
  - 以類ruby的方式撰寫，轉譯為Erlang
  - 發明者原本寫ruby
  - Erlang為Ericsson電信發明出來
  - 台灣社群大約100人


# 1. Tailwind CSS
- [官網](https://tailwindcss.com/)
- [介紹文](https://5xruby.tw/posts/tailwind-css-plugin/)
- Tailwind CSS 是一套 Utility-First CSS，相當具有彈性，也非常適合快速刻板。
- 但是一整包很大包（因為包含各種可能的情況），需要最佳化
- 最佳化：可使用[PurgeCSS](https://tailwindcss.com/docs/optimizing-for-production#writing-purgeable-html)來去除掉沒用到的部分


---
# 2. 物件導向OOP
#### var / let
* var = function
* let = block
- 同樣程式用var和let的效果可能不一樣

#### 字面值
- 字面值和屬性相同時，可省略
```javascript=
name: name,
action: action,
```
可以改寫為
```javascript=
name
action
```
#### 解構式
```javascript=
const goku = heroCreator('悟空', '龜派氣功')
這兩行
let name = goku.name
let action = goku.action
與這一行同義，叫做解構式
let { name, action } = goku
console.log(name, action);
```
- 解構式會把同名的抓出來

#### Javascript的物件導向
- [說明(MDN)](https://developer.mozilla.org/zh-TW/docs/Learn/JavaScript/Objects/Object-oriented_JS)

#### 原型鍊 [Prototype]
- [該來理解 JavaScript 的原型鍊了](https://blog.techbridge.cc/2017/04/22/javascript-prototype/)
- [物件原型(MDN)](https://developer.mozilla.org/zh-TW/docs/Learn/JavaScript/Objects/Object_prototypes)
    >- JavaScript 的物件即透過原型 (Prototype) 機制相互繼承功能，且與典型的物件導向 (OO) 程式語言相較，其運作方式有所差異。
- [__proto__](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Object/proto)

:::info
**面試題**：__proto__與prototype的差別？
:::

##### javascript的類別是假的，是語法糖衣。
##### javascript的世界全都是物件

---
##### 當在 new 的時候會做的事：五個步驟
1. 進入泡泡
2. 建立空物件 {}
3. this -> {}
4. 把 {}.__proto__ -> 這個 function的 prototype
5. return this  
##### js原型鏈圖示
![](https://i.imgur.com/YjKsdRN.jpg)


##### 繼承與原型鏈 
- [說明(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)


---
# 3. this
- js的this寫在哪裡沒有差，只在乎誰呼叫他。
- 即使被包在函數內也是，由呼叫者決定
- [淺談 JavaScript 頭號難題 this：絕對不完整，但保證好懂](https://blog.techbridge.cc/2019/02/23/javascript-this/)
- [JavaScript程式語言的中文入門書籍](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/this.html)

### this的五項規則
1. 函數執行的時候，有沒有使用 `new` 關鍵字？如果有，`this` 就是指向那個物件本身。
2. 「誰呼叫，誰就是 `this`」規則。
3. 是否使用箭頭函數？有的話就不會有自己的 `this`。
4. 是否有使用 `bind`、`apply` 或是 `call` 方法？有的話 `this` 的指向也會跟著改變。
5. 是否有開啟「嚴格模式」？


##### 課堂範例(規則1)
```javascript=
function hello() {
  console.log(this);  // 會印出什麼？全域變數undefined

  function world() {
    console.log(this);  // 會印出什麼？全域變數undefined

    const game = {
      name: "Zelda",
      greeting: function() {
        console.log(this); // 會印出什麼？Zelda
      }
    }
    game.greeting();
  }
  world();
}
hello();
```

#### bind() 方法
- `Function.prototype.bind()`
- [說明(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
> - bind() 方法，會建立一個新函式。該函式被呼叫時，會將 this 關鍵字設為給定的參數，並在呼叫時，帶有提供之前，給定順序的參數。

- bind本身不會執行，只會產生新函數 

#### apply() 方法
- `Function.prototype.apply()`
- [說明(MDN)](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)
> - apply() 方法會呼叫一個以 this 的代表值和一個陣列形式的值組(或是一個 array-like object )為參數的函式。
> 
> - 注意：這個函式的語法和call() 幾乎一樣，最大的不同是 call() 接受一連串的參數，而 apply() 接受一組陣列形式的參數。

- **＊** apply()跟call()的差別？基本運作一樣，但apply()只能接一個。

##### 課堂範例(apply())
```javascript=
const 戰士 = {
  hp: 100, 
  mp: 10, 
  attack: function() {
  }
}

const 法師 = {
  hp: 50, 
  mp: 100, 
  heal: function(){
    this.hp += 10
  }
}

console.log(戰士);
法師.heal.apply(戰士)
console.log(戰士);
```

##### 課堂測驗
```javascript=
var hero = {
  name: '悟空',
  sayMyName: function() {
    console.log(this.name);
  }
};

hero.sayMyName();   // A

var speakOut = hero.sayMyName;
speakOut();         // B

const someone = { name: '路人' }

hero.sayMyName.call(someone);  // C

function here() {
  console.log(this);
}

const there = () => {
  console.log(this);
}

here();   // D
there();  // E
```
問：ABCDE各印出什麼？
* A. 悟空，前面有呼叫 
* B. undefined，this為全域變數
* C. 路人
* D. 全域變數
* E. 全域變數


---
#### 課後複習
- [javascript-questions(github)](https://github.com/lydiahallie/javascript-questions)






---
# 附件
- [這裡是附件的標題](這裡放連結) 
- [這裡是附件的標題](這裡放連結) 


