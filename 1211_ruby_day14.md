# 1211_ruby_day14

[![hackmd-github-sync-badge](https://hackmd.io/rLk15mqJSjWnstOs0St_ew/badge)](https://hackmd.io/rLk15mqJSjWnstOs0St_ew)


---

#### 上課日期：1211
###### tags: `ruby`
###### tags: `5xruby`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)



---
# 0. 綱要/目錄
- 套件
- [ ] paranoia 軟刪除
- [ ] kaminari 分頁
- [ ] friendly_id 網址美化
- [ ] aasm 狀態機
- [ ] pundit 權限


---
# 1. 軟刪除專案
- [paranoia](https://github.com/rubysherpas/paranoia)

1. Run your migrations for the desired models
 -  `rails g migration deleted_posts`
 - 建一個migration，名稱可隨意
2. 在新的migration裡面，加上這兩行
```
    add_column :clients, :deleted_at, :datetime
    add_index :clients, :deleted_at
```
- clients改為要改的model名稱，ex:posts
3. 在修改的model裡面加上這一行(ex:posts)
`acts_as_paranoid`
4. `rails db:migrate`
---
# 2. kaminari (日文：雷)
- 為什麼叫「雷」？因為作者(松田明)在[淺草雷門](https://www.google.com/search?q=%E9%9B%B7%E9%96%80&rlz=1C5CHFA_enTW920TW920&oq=%E9%9B%B7%E9%96%80&aqs=chrome..69i57j0l7.2868j0j1&sourceid=chrome&ie=UTF-8)。
- [專案連結](https://github.com/kaminari/kaminari)：功能為作分頁
- Asakusa.rb 社群：日本ruby最大社群
- [松田明
Akira Matsuda](https://github.com/amatsuda)
1. `gem 'kaminari'`，把這行加到Gemfile裡面
2. 安裝，`$ bundle`
- *注意：有些套件安裝後，server需要重新開啟！！
##### 分頁器
- [連結](https://github.com/kaminari/kaminari#views)
- 在show.html.erb裡加上`<%= paginate @comments %>`
- [安裝分頁切換器](https://github.com/kaminari/kaminari#to-edit-your-paginator)，`rails g kaminari:views default`

---
# 3. 狀態機
- FSM(finite-state machine）或FSA(finite-state automation)
- [說明(wiki)](https://zh.wikipedia.org/zh-tw/%E6%9C%89%E9%99%90%E7%8A%B6%E6%80%81%E6%9C%BA)
- [連結](https://github.com/aasm/aasm)
- 課堂的狀態機![](https://i.imgur.com/aI3Zka3.jpg)

- 某專案的狀態機(租借衣服) ![](https://i.imgur.com/Be4xdzy.png)

- [安裝](https://github.com/aasm/aasm#installation)
1. 安裝到gem
2. 建立migration
3. 修改建立migration
4. db:migrate
5. 修改board.rb

```ruby=
class Job < ActiveRecord::Base
  include AASM

  aasm do # default column: aasm_state
    state :public, initial: true
    state :hidden, :locked

    event :hide do
      transitions from: :public, to: :hidden
    end

    event :lock do
      transitions from: :public, to: :locked
    end

    event :open do
      transitions from: [:locked, :hidden], to: :public
    end
  end
end
```
6. 進入沙盒模式測試
7. 在board.rb修改`aasm(column: 'state', no_direct_assignment: true) do`（括弧中設定），讓狀態不可被隨便更改

---

#### 讓index略為簡潔
原本
在index.html.rb裡面：
```ruby=
<%= link_to board.title, board, class: "board-title board-title-#{board.state}" %>
```
可修改成：
1. 在index.html.rb裡面：
```ruby=
<%= link_to board.title, board, class: board_title_css(board) %>
```
2.在boards_helper.rb裡面：
```ruby=
module BoardsHelper
  def board_title_css(board)
    "board-title board-title#{board.state}"
  end
end
```

--- 
:::warning
＊使用套件，就像是安裝軟體，需先進行確定是否適宜(先詢問主管！)
:::

---

:::spoiler
卡位特殊套件名稱(gem)
- [範例](https://rubygems.org/gems/eddie)
:::

---
# 4. 更改網址名稱
- [套件連結](https://github.com/norman/friendly_id)
- [安裝套件](https://github.com/norman/friendly_id#usage)
1. Add this line to your application's Gemfile:
`gem 'friendly_id', '~> 5.4.0'`
 > Note: You MUST use 5.0.0 or greater for Rails 4.0+.
2. And then execute:
`bundle install`
3. Add a slug column to the desired table (e.g. Users)
`rails g migration AddSlugToUsers slug:uniq`
4. Generate the friendly configuration file and a new migration
`rails generate friendly_id`
 > Note: You can delete the `CreateFriendlyIdSlugs` migration if you won't use the slug history feature. 
5. Run the migration scripts
`rails db:migrate`


---
# 5. 權限管理套件 
> 這裡列出三款
- [cancan](https://github.com/ryanb/cancan)
- [cancancan](https://github.com/CanCanCommunity/cancancan)：cancan的下一代
- [pundit](https://github.com/varvet/pundit)
  - [安裝說明](https://github.com/varvet/pundit#installation)
1. 在gemfile裡面的公用區加入 `gem "pundit"`
2. `$ bundle`
3. include Pundit
```ruby  
class ApplicationController < ActionController::Base
  include Pundit
end
```
4. 建立policy資料夾 `$ rails g pundit:install` 和 `$ rails g pundit:policy`


---





---
# 附件
- [默默會ref](https://www.google.com/search?rlz=1C5CHFA_enTW920TW920&sxsrf=ALeKk01Xmvc1ntM1BEeQPstdIc8H4CIlxw%3A1607656847268&ei=j-XSX5z8D4ixmAWHoJb4Bg&q=+%E3%82%82%E3%81%8F%E3%82%82%E3%81%8F%E4%BC%9A%E3%81%AEIT%E5%8B%89%E5%BC%B7%E4%BC%9A&oq=+%E3%82%82%E3%81%8F%E3%82%82%E3%81%8F%E4%BC%9A%E3%81%AEIT%E5%8B%89%E5%BC%B7%E4%BC%9A&gs_lcp=CgZwc3ktYWIQA1CCm5QBWIKblAFg4qCUAWgAcAB4AIABV4gBV5IBATGYAQCgAQKgAQGqAQdnd3Mtd2l6wAEB&sclient=psy-ab&ved=0ahUKEwjc_7S6_MTtAhWIGKYKHQeQBW8Q4dUDCA0&uact=5)：日本的もくもく会  :100: 
- [RailsCasts](http://railscasts.com/)：早期的rails學習網站 :accept: 
- [GoRails](https://gorails.com/)：另一個教學網站 :accept: 


