# 1102_ruby_day3

#### 上課日期：1102
###### tags: `ruby`
###### tags: `5xruby`


---
# 相關連結:
 - [投影片下載](https://cdn.discordapp.com/attachments/748046752870826045/772714897972396052/0.0.6b_-_Ruby_for_Rails_-_Block_.pdf)
 - [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)


---
# 1. Block(區塊)
> 說明這部分是什麼
1. `{}`
    1. 沒辦法單獨存在
    2. Block = 一段不會被主動執行的程式碼
    3. 寫法有兩種，基本一樣，有些微差異
        * `{}`
        * `do`...`end`
    5. block是一種
1. 控制權
    1. Block 就像寄生蟲一樣 依附在**方法**後面
    2. 要不要執行，要看「宿主」臉色:可以保留選擇要不要執行
    3. 用`yield`讓出控制權執行
    4. 在 Block 裡不使用 return
 - ES = ECMAScript ≒ JavaScript
 	- [ECMAScript](https://en.wikipedia.org/wiki/ECMAScript) 國際標準的稱呼
 	- [JavaScript](https://en.wikipedia.org/wiki/JavaScript) 一般通俗的稱呼
3. callback回呼/回報：功用是交代結果，一般程式執行完就執行完了，沒有相關的訊息顯示執行的結果，所以會以callback來顯示執行的狀況。
 - 在ruby裡面，不會特別寫return，因為語言不同，可能不會有正確的結果。
- `block_given?`
```ruby=
def a
  if block_given?
  yield
  end
end

a
# => 註解：不會印出來，也沒出錯
```

:::info
### 冷知識
- Block 的有大括號以及 do ... end 這兩種寫法，有什麼不同?
	- 個人觀感與偏好的使用
	- 大括號的功能較`do`...`end`強（篩選較嚴格）
- 大小寫：駝峰式（CamelCase）、蛇式（snake_case）
	- 不同語言有不同的偏好
	- 大駝峰：BigCamel；小駝峰：smallCamel
	- 大蛇：BIG_SNAKE；小蛇：small_snake
:::

### 物件化
> Block 沒辦法單獨存活 但被物件化之後就可以了
#### Proc
#### lambda
:::info
冷知識
- Proc 跟 Lambda 看起來很像，用起來也很像，但有什麼差別嗎?
    -Proc是一個類別，可以使用new方法將block實體化，本質上接近block，因此傳入的引數與參數不一致也不會出錯。
    -lambda是方法，所需參數與傳入的引數必須一致，否則會出錯。
Proc 與 Lambda
    * add_two_proc = Proc.new { |n| n + 2 } 
    * add_two_lambda = lambda { |n| n + 2 }
    * p add_two_proc.call(1, 2, 3) # 正常執⾏，印出 3 
    * p add_two_lambda.call(1, 2, 3) # 發生引數個數錯誤
:::


:::success
補充：常見於套件的寫法（*的使用）
```
def hello(a, *b, **c)
	p a
	p b
	p C
end
hello(1,2,3,5,3,1)
```
*接陣列
**接hash
:::


---

# 2. 物件導向
> 在 Ruby 裡，幾乎什麼東西都是物件
> 物件 = 狀態(名詞) + 行為(動詞)

- 在 Ruby 裡「幾乎」什麼都是物件，那什麼不是物件?

### 2.1. 類別與實體(class and instance)



# 3. 模組



# 4. 重構（refactor）

:::info
#### Ruby 物件模型圖
- 模組與class要分清楚，方形的都是class
- 模組不能new，不能繼承
:::

- ruby 裡面陣列可以直接相減

- [參考文章:Ruby Object Model](https://medium.com/lynn-%E7%9A%84%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/rails-%E6%96%B0%E6%89%8B%E6%9D%91-ruby-object-model-5c3b4b869df6)







---
# 附件
- [這裡是附件的標題](這裡放連結) 
- [這裡是附件的標題](這裡放連結) 


