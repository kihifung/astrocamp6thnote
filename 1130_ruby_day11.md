# 1130_ruby_day11

[![hackmd-github-sync-badge](https://hackmd.io/-4ssPre_Qi6cAskH8seKYg/badge)](https://hackmd.io/-4ssPre_Qi6cAskH8seKYg)

---
#### 上課日期：1130
###### tags: `ruby`
###### tags: `5xruby`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)



---
# 0. 綱要/目錄
- [ ] rails專案(續)
  - [ ] 留言功能comment
  - [ ] AJAX
  - [ ] 面試題


---
# 1. 留言comment
> 文章的評論功能

1. comment
	- content text
	- user belongs_to
	- post belongs_to 

```ruby=
rails g model Comment content:text user:belongs_to post:belongs_to
rails db:migrate
```

##### new和create的差別
- post要new還是create?
- comment要new還是create?

##### n+1問題 N+1 Query
> [color=#bf6211]面試題：什麼是n+1問題
- n+1是很經典的效能殺手：有幾個東西就會執行查詢n+1次，因為執行太多次查詢，對於效能有很大的耗損。但rails有方法可以只要1+1次。
- 會發生 n+1 一定有兩個表格以上，但有兩個以上表格不一定會發生 n+1
- [[ Rails ] N + 1 Query 網站效能問題](https://medium.com/@chaowu.dev/rails-n-1-query-41aa92ffb92e)
- [bullet(github)](https://github.com/flyerhzm/bullet)
	> - help to kill N+1 queries and unused eager loading
- [rack mini profiler(gitgub)](https://github.com/MiniProfiler/rack-mini-profiler)
- [rack-mini-profiler 2.2.0](https://rubygems.org/gems/rack-mini-profiler/versions/2.2.0)
```ruby=	
gem install rack-mini-profiler
bundle
```

---
##### 刪除文章
- 兩種方法：
  - `is_deleted: boolean true`
  - `deleted_at: datetime nil`
> 後者雖然多紀錄了時間(多使用了一些記憶體)，但資訊比較完整
`$ rails g migration add_deleted_at_to_comment`
```ruby=
class AddDeletedAtToComment < ActiveRecord::Migration[6.0]
  def change
    add_column :comment, :deleted_at, :datetime, default: nil
    add_index :comments, :deleted_at
  end
end
```
	- 因為這種資料很常會被查詢，所以建立一個索引 => 使用硬碟空間換取查詢的時間。
	- 建立欄位時，需要考量這個資料的性質，會怎樣被使用？使用情形是什麼？
	- 以二元樹（binary tree）方式建立索引

##### 在console看現在時間
```
$ rails c
$ Time.now
```


##### 找錯誤
在程式碼中，覺得有問題的地方，打一個明顯好找的訊息。執行看看，是在哪裡壞掉。


###### 把商業邏輯包在controller裡

###### scope的用法：見先修教材
- 通常沒在用
- 但會用在假刪除、軟刪除

###### 如果想看垃圾桶的資料
- 如果是系統管理員想要調資料，那就要用unscope
- [paranoia(github)](https://github.com/rubysherpas/paranoia)

##### 封裝（Encapsulation）
- 把不必要的東西裝起來。
> - 一種將抽象性函式介面的實作細節部份包裝、隱藏起來的方法。
> - 同時，它也是一種防止外界呼叫端，去存取物件內部實作細節的手段，這個手段是由程式語言本身來提供的。
> - 封裝被視為是物件導向的四項原則之一。(wiki)


# 2. [AJAX](https://zh.wikipedia.org/zh-tw/AJAX)

- 只是在演戲
- 一定要會喔～

##### 按讚功能很難寫
- 多個文章<-->多個使用者


---
# 3. 面試題

- [面試題目(5xruby_2017)](https://discord.com/channels/748042598983401482/748046752870826045/782895130709065749)

* 在ruby裡面，public和private有什麼不同？
* ruby跟rails的差別
* 常數和變數的差別
* 實體方法跟類別方法的差別
* 類別與模組的差別
* ruby引入模組裡：include和extend的差別
* hash[:key] 和 hash["key"]的差別（一個是字串，一個是符號）
* 1到100，取五個不重複的數字，怎麼做？
* duck typing是什麼？什麼時候用得到？
* symbol和string的差別
* migration file 和schema.rb的差別


---
# 附件

- [Rendering Collections](https://guides.rubyonrails.org/layouts_and_rendering.html#rendering-collections)
