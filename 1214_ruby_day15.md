# 1214_ruby_day15
---
[![hackmd-github-sync-badge](https://hackmd.io/0U9lPxDqQ1ayBJXDzE9vLQ/badge)](https://hackmd.io/0U9lPxDqQ1ayBJXDzE9vLQ)

---

#### 上課日期：1214
###### tags: `ruby`
###### tags: `5xruby`

---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
- [購物車(為你自己學rails)](https://railsbook.tw/chapters/27-shopping-cart-part-1.html)


---
# 0. 綱要/目錄
- [ ] 購物車 with TDD



---
# 1. 購物車

### 書店
- [the pragmatic bookshelf(書店)](https://pragprog.com/)
  - 老闆為[David Thomas](https://en.wikipedia.org/wiki/Dave_Thomas_(programmer))，也是Ruby的大大。
  - [AWD6](https://pragprog.com/titles/rails6/agile-web-development-with-rails-6/)：裡面的方法為把購物車做到資料庫裡面
- [另一間書店](https://www.packtpub.com/)
  - 龍：水準參差不齊，需慎選！

### 購物車設計
  * cart
  * cartitem
  * 每一頁都可以看到，用Session


#### 基本功能：
1. 把商品丟到到購物車裡（購物車裡就有東⻄）
2. 重複點擊購物，購買項目(CartItem)不會增加，但數量會改變
3. 商品可以放進去也可以拿出來（購物車）
4. 每個購買項目都可以計算它自己的金額(小計)
5. 可以計算整台購物車的總金額
6. 特別活動-折扣(ex: 全面九折、滿千送百、滿額免運）

#### 安裝套件
* rspec-rails
* factory_bot_rails
* faker

#### 裝在哪？
* group :development, :test
* group :development

##### minitest
第一層資料夾有個叫test，使用rspec用不到，那是用[minitest](https://rubygems.org/gems/minitest)才會使用到。
vendor資料夾也是空的，也可以刪掉．

##### 寫測試的目的
- 建立安全網
- 是QA不是QC
- AAA原則：
  * Arrange
  * Act
  * Assert
- 測試時以變動最小為原則，一次改一個，才知道哪裡有問題


#### 指令
1. 安裝測試資料夾： `$ rails g rspec:install`
2. 在rspec下建立model： `$ rails g rspec:model Cart`


#### 套件 timecop
- [gem連結](https://rubygems.org/gems/timecop)
- [用 Timecop 自由穿梭時間軸](https://medium.com/@tonyhsu/%E7%94%A8-timecop-%E8%87%AA%E7%94%B1%E7%A9%BF%E6%A2%AD%E6%99%82%E9%96%93%E8%BB%B8-e9d606e8dbd3)
  - 修改時間為特定時間

### 名詞解釋
- WIP的意思即為Work In Process，處理中。

---
```ruby=
  def serialize
     items = []
      @items.each do |item|
      items << { "item_id" => item.item_id,
                 "quantity" => item.quantity }
    end
```
---


---
# 附件
- [Ruby文件](https://ruby-doc.com/) 
- [RailsHurts](https://railshurts.com/)：隨機出現十題，看看是ruby語法，還是rails語法 
- [Ruby Association](https://www.ruby.or.jp/en/)
  - 一個日本的組織，有在發放證照
  - [題庫(銀級)](https://www.ruby.or.jp/assets/images/en/certification/exam_prep_en.pdf)
  - [題庫2(銀級)(github)](https://github.com/ruby-association/prep-test/blob/master/silver.md)
  - [題庫(金級)(github)](https://github.com/ruby-association/prep-test/blob/master/gold.md)
  
  
