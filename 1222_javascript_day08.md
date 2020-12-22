# 1222_javascript_day08

[![hackmd-github-sync-badge](https://hackmd.io/QqKfNUVxTjmfXLSTQJt-wg/badge)](https://hackmd.io/QqKfNUVxTjmfXLSTQJt-wg)


#### 上課日期：1222
###### tags: `javascript`
###### tags: `5xruby`

---



---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
 - [課程文件說明](https://reurl.cc/VXreeN)
 - [課程範例檔](https://drive.google.com/file/d/1GrQSP-dmPivr6-Xa7WjNZ_wlljcu-4aV/view)


---
[TOC]

---
# 0. 綱要/目錄
- [ ] React.js
- [ ] 重點2
- [ ] 重點3
- [ ] 重點4
- [ ] 重點5


---
# 1. 基本背景與環境設定

### VScode所需套件
- [LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
- [todo-tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)
  - 標注todo的地方都會變色，方便辨識
- [JavaScript (ES6) code snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.JavaScriptSnippets)
  - 快捷鍵，網頁內有表可查
- [beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)
    - 排版用

### VScode外框顏色設定
> 目的：多視窗時方便辨識
![](https://i.imgur.com/c4nb1o2.png)
- [設定說明(vscode)](https://code.visualstudio.com/api/references/theme-color)
- 在setting裡面搜尋`workbench.colorCustomizations`，修改setting.json，有user和workspace選項（依使用者或是工作區）。
- 個別資料夾變更選擇workspace，圖中範例為設定`"activityBar.background": "#f5b043"`
- 各種顏色設定
    - 範例：![](https://i.imgur.com/cGoOq2j.png)
    - 可比較顏色與變色區域
    - 或是直接使用[Peacock套件](https://marketplace.visualstudio.com/items?itemName=johnpapa.vscode-peacock)

### JSX用Babel轉譯
React要使用bable套件，因為要使用JSX，原生JS看不懂。
```javascript=
 <head>
    ....
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/6.26.0/babel.js"></script>
  </head>
  <body>
    .....
    <script type="text/babel" src="app.js"></script>
  </body>
```
這邊範例用cdn引入React和Bable，同時用`<script type="text/babel" src="app.js">`做即時轉譯。但這方式效能不好，只是上課範例用。


---
# 2. React 實作

### virtual DOM 
- 用code渲染出來的
- 範例1：js打完可用liveshare查看html，使用dev tools可以看到原本的沒有寫h1，卻出現了。

#### function內的參數都有順序
- 第一個是JSX，再來是DOM
- render只能塞兩個參數
- JSX一定要有一個根節點
- Adjacent JSX elements must be wrapped in an enclosing tag (一個封閉的tag)


#### JSX
- 副檔名JSX與JS的差別：react的專屬副檔名為jsx，但使用js也沒有影響
- 在jsx裡面支援html語法，但class會變成classname
- 在JSX裡面遇到大括號{}，裡面的東西都會以javascript方式運算
- 任何的標籤都可以結束自己，只要後面沒有子元素

# 3. JS設定snippet
設定好就可以在JS打snippet了
1. 開啟VScode settings
2. 點開右上圖是打開 settings.json
    - ![](https://i.imgur.com/id0X8dO.png)
3. 在setting.json裡面加上這段
```javascript=
  "emmet.includeLanguages": {
      "javascript": "javascriptreact"
    },
```
  - ![](https://i.imgur.com/W2qRDl5.png)


### 大小寫（開頭）
- 所有的component都要大寫開頭
- 小寫會當成html的div
    - ![](https://i.imgur.com/deq1asR.png)


---
# 3. 範例三Props
- props：慣例的參數名稱
- children是內建的關鍵字
- Props外部傳進來的，state是內部的狀態

---
# 4. 範例四state
- 計數器
### 進階:兩個有按鈕的計數器
  - ![](https://i.imgur.com/6TE4PYp.png)

- component取得參數的唯一方式就是從props來

# 5. 範例五setState


---
# 6. 範例六 （重覆了）
(無)

---
# 7. 範例七 啟動console.log


---
# 8. 範例八 list-rendering
- 迴圈裡面的virtual DOM 都要加唯一的key值（ex: 電商中，商品都要有唯一的key值）
- 完全不用處理DOM，都是render出來的
- props裡面的值都是唯讀的

# 9. 範例九 list-rendering-advance
- 把json渲染出來

# 10. (重覆了)

# 11. useRef
- React只處理virtual DOM，要處理DOM還是要原本的函式

:::info
### React什麼時候會觸發重新渲染？
不知道，看情況
因為程式碼是由上往下讀，所以前面控制指令讀完後，後面的可能還沒渲染出來。
立即更新會造成效能太差。
可用useEffect觀察。
:::

### Hook功能
- react16開始變成正式功能
- useXXXX都是


# 13. 兩個component的溝通
- 限定一等親的溝通
- 父傳子透過props
- 用on命名開頭

# 14. to-do list
- 分為三部分todoForm, todoItem, todoList
#### todoForm
> 輸入文字，確認後，產生一筆資料

- 用form包，支援原生的enter事件 

#### todoItem



---



---
# 16.範例十六 
- 較為進階（略過）


---
# 附件
- [奶綠茶的codepen](https://codepen.io/milkmidi/) 
- [其他js範例](https://www.shadertoy.com/view/Ms2SD1)
- [奶綠茶的粉絲頁](https://www.facebook.com/milkmidifans) 
- [語法糖](https://zh.wikipedia.org/wiki/%E8%AF%AD%E6%B3%95%E7%B3%96)

