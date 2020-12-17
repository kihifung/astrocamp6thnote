# 1217_javascript_day06

[![hackmd-github-sync-badge](https://hackmd.io/HyzXBLPuQFqNM6dkqfA_oQ/badge)](https://hackmd.io/HyzXBLPuQFqNM6dkqfA_oQ)

> JavaScript 的模組化以及 NodeJS
> 
#### 上課日期：1217
###### tags: `javascript`
###### tags: `5xruby`

---
[TOC]

---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
- [投影片連結](https://ppt.cc/fPHiEx)
- [隨堂練習包](https://ppt.cc/fwlXpx)



---
# 0. 綱要/目錄
- [ ] 模組化 module
- [ ] Node.js
- [ ] 重點3
- [ ] 重點4
- [ ] 重點5


---
# 1. JavaScript modules / ES module
#### 為什麼要模組化
- 避免產生過大的檔案，造成執行上的問題
- 傳統 JavaScript 沒有內建取得別的 JavaScript 的功能，於是人們就自己發明各式各樣的工具：browserify / rails assets pipeline / gulp.js / rollup.js / webpack


#### 模組化寫法1 commonJS
* NodeJS 的引入方式，require是node.js的寫法
* `pkg = require('pkg_name')`
* `module.export = ...`



#### 模組化寫法2 ES module
* ECMA將其標準化（ECMA Script = ES）
* [MDN 文件](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
* [ES module: A cartoon deep dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)
* 關鍵字：`import` / `export` 

#### 範例10.
> 用 ES module 改寫
```javascript=
<script type="module"></script>
import moduleDefault from './another.js'
export default moduleDefault
```



---
# 2. [Node.js](https://nodejs.org/)
- 從chrome拉出來的javascript
- 可以取用系統功能，目前最常被拿來處理前端 assets

### NodeJS interactive shell
* 使用指令 `node` 進入，就像是瀏覽器的 `Console`
* 沒有 `window`，但有 `global`
  * 沒有 BOM / DOM API
  * `console`, `JSON`, `setInterval`...等工具跟瀏覽器是一樣的


#### 範例11. 使用nodejs查看json檔
- `const fs = require('fs/promises')`  // 取用nodejs內建的函式庫
- 查看json：在該資料夾中同時放置欲查看的json和該程式，接著輸入指令 `node pretty-print-json.js posts.json`
  - 其中pretty-print-json.js為程式名稱，posts.json為檔案名稱


#### 範例 12. node-project-json-to-csv
> 目的：把 JSON 轉換成 CSV
1. 在資料夾下建立 NodeJS 專案：$ npm init
- 接下來會逐項確認資料，要修改就直接輸入
```json=
{
  "name": "11_node-project-json-to-csv",
  "version": "0.0.1",
  "description": "Post JSON to CSV",
  "main": "main.js",
  "scripts": {
    "main": "node main.js posts.json posts.csv"
  },
  "author": "PastLeo",
  "license": "ISC",
  "dependencies": {
    "fast-csv": "^4.3.1"
  }
}
```
  - 安裝npm, `npm install --save fast-csv`
2. 結束後會產生的檔案
* package.json
* package-lock.json
* node_modules(資料夾)
3. 執行程式（轉換json TO CSV：`$ npm run main`

#### 全域安裝
- npm install -g XXXXXXXX
- npm install -g http-server
- 如果安裝不了可能是存取權限的關係（注意看錯誤訊息），這時可在指令最前面加上sudo (接著會要求輸入管理者密碼)
- `$ http-server` ，即可啟動


---

# 3. YARN
- 提供的功能跟 npm 是一樣的
- 當初 facebook 嫌 npm 爛所以自己做了這個
- yarn.lock ~= package-lock.json(npm)
- BUT!同一個專案下不要yarn跟 npm同時用，一次用一個就好

### 前端 Assets 打包 
- [Webpack](https://webpack.js.org/)
* 目前主流的前端 bundle 工具
  * rails 的 [webpacker](https://github.com/rails/webpacker) 就是這個的橋接
* [plugins](https://webpack.js.org/plugins/) / [loaders](https://webpack.js.org/concepts/loaders/) 非常多

#### 範例13. hello-webpack
0. [參考資料](https://webpack.js.org/guides/getting-started/)
1. npm init 
2. 建立一個webpack檔案"webpack.config.js"
```javascript=
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```
3. 修改webpack.config.js
```javascript=
  mode: 'development',  // 可看看有加沒加的差異
  entry: './src/main.js',  //修改進入點
  output: {
    filename: 'bundle.js',  //產生的檔案
    path: path.resolve(__dirname, '.'), //產生檔案的位置， "." 點表示同一層
```
- 沒有加development的話，全部的code會被壓成一行
- 有加development的資訊比較完整、易讀
4. 修改index.html
```htmlmixed=
<script type='module' src='bundle.js'></script>
```
- 其中src='bundle.js'，表示讀取的檔案，即前面webpack產生的檔案(bundle.js)
- type='module' 這部份可刪掉

5. 執行，產生bundle.js
`$ npx webpack --config webpack.config.js `
- npx：直接執行專案內指令，如果專案內沒有套件，就會上網去下載來安裝。
- webpack存在於node_modules/.bin/裡面




#### hello-webpack，加入 typed.js 打字效果
1. npm install typed.js --save
> 有加--save才會存到package.json裡面
2. 修改package.json
- 加入bundle部分
```json=
"scripts": {
    "bundle": "webpack --config webpack.config.js"
```
3. 修改add-one.js
    1. 安裝、引入 npm 套件，並透過 webpack 打包給瀏覽器 `import Typed from 'typed.js';`
    2. new Typed 
```javascript=
    var typed = new Typed(textSpan,{
    strings: ['Loading...Loading...Loading...'],
    typeSpeed: 60
  });
```
- 
    3. 完成時移除原本 Loading...
4. 執行` $ npm run bundle`
- 每次修改後，需要重新bundle

#### 打完日期時移除 cursor


---
# 4. [Babel](https://babeljs.io/)
- Babel is a JavaScript compiler.


# 5. JavaScript 語法檢查
- [ESLint](https://eslint.org/)
- 為什麼需要語法檢查？
  * 強迫團隊使用 best practice
  * 避免錯誤
  * 維護程式碼品質
  * 讓程式碼風格統一
  * 通常會在 CI 流程裡面檢查

### 安裝
1. set up a configuration file：`$ npx eslint --init`                      
2. 回答問題（8題） 
:::spoiler
1. How would you like to use ESLint? …
  To check syntax only
  To check syntax and find problems
❯ To check syntax, find problems, and enforce code style

2. What type of modules does your project use? …
❯ JavaScript modules (import/export)
  CommonJS (require/exports)
  None of these

3. Which framework does your project use? …
  React
  Vue.js
❯ None of these
  
4. Does your project use TypeScript? › No / Yes(No)
  
5. Where does your code run? …  (Press `<space>` to select,` <a> `to toggle all, `<i>` to invert selection)
✔ Browser
  Node

6. How would you like to define a style for your project? …
❯ Use a popular style guide
  Answer questions about your style
  Inspect your JavaScript file(s)

7. Which style guide do you want to follow? …
❯ Airbnb: https://github.com/airbnb/javascript
  Standard: https://github.com/standard/standard
  Google: https://github.com/google/eslint-config-google
  
8. What format do you want your config file to be in? …
❯ JavaScript
  YAML
  JSON
  
9. Would you like to install them now with npm? › No / Yes(Yes)  
:::

 - ![](https://i.imgur.com/3Snabj1.png)

3. 檢查語法錯誤 `$ npx eslint src` ，src為目的地 
4. 修改eslintrc.js
```javascript=
    "rules": {
        "semi": ["error", "always"],
        "quotes": ["error", "double"]
    }
```


5. 修改package.json
- 加入lint和lintf，自動檢查與自動修正
```json=
  "scripts": {
    "bundle": "webpack --config webpack.config.js",
    "lint": "eslint src/",
    "lintf": "eslint src/ --fix"
  },
```

6. 處理剩下來的錯誤



---


