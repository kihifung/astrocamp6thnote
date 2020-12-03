# 1116_ruby_day7

[![hackmd-github-sync-badge](https://hackmd.io/-8RWvc75TFmgT-HHcTXKCg/badge)](https://hackmd.io/-8RWvc75TFmgT-HHcTXKCg)

---
#### 上課日期：1116
###### tags: `ruby`
###### tags: `5xruby`
###### tags: `SQL`


---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
- 應用程式：
	- [DB Browser for SQLite](https://sqlitebrowser.org/)
	- [MySQL Server](https://dev.mysql.com/downloads/mysql/)
	- [MySQL WorkBench](https://www.mysql.com/products/workbench/)

---
# 0. 綱要/目錄
- [ ] 資料庫相關介紹
- [ ] 新增修改刪除（SQL/Ruby）
- [ ] 其他指令（SQL/Ruby）



---
# 1. 資料庫

- 常見資料庫軟體：
	- MySQL
	- PostgreSQL(PG)
		- [使用手冊](https://docs.postgresql.tw/)
	- MS_SQL
	- Oracle_database
		> rails常用MySQL和PGSQL

##### PHP的常用軟體LAMP：
* linux
* apache
* mysql
* php

- 一個伺服器可以有很多資料庫(DB)
- 一個資料庫可以有很多表格(table)
- SQL(Structured Query Language)結構化查詢語言

#### RDBMS關聯式資料庫管理系統

#### 資料型態
- char/varchar/text
- interger/...
- 圖片不要放在資料庫，一般放在rails的public或是AWS的S3。

#### 資料庫語法

NN：not mull 非空
PK：Primary Key
AI：autoincrement自動增值（像是流水號）
U：unique（通常沒勾選沒差）

##### SQL語法
- 大小寫沒差
- 但建議關鍵字大寫
- char(10)和varchar(10)有什麼差別：長度都是10，字多時後者比較節省空間。
- 

#### 資料表追加欄位 (ALTER TABLE)

#### 語言的分類 DDL/DML/DQL
- DDL資料定義語言：create/drop/update
- DML資料操作語言：新增修改刪除
- DQL資料查詢語言：select


#### 可能的問題SQL injection
- [著名的資安漏洞](https://zh.wikipedia.org/wiki/SQL%E6%B3%A8%E5%85%A5)
- [閱讀1](https://cnews.com.tw/140190825a01/)
- [閱讀2](https://www.inside.com.tw/article/6359-sql-injection-fools-speed-traps-and-clears-your-record)

#### 資料寫入的順序是否依照表格順序？
- 有對照就不用
#### 如果varchar(10)輸入超過10個字會怎樣？
- 會出錯
#### 單引號裡要包單引號，前面要加"\"


---
## 2.語法(SQL/Ruby對照)
- 註解：連續2個減號字元 `--` 後的文字為註解，或「`/*`」與「`*/`」所包起來的文字為註解
### 插入資料（新增）/選取全部
```sql=
1. 
INSERT INTO heroes(name, hero_level, hero_rank)
VALUES('cccc', 's', 2) 
2.
SELECT * FROM heroes;
```
```ruby=
1.
Hero.create(name:'cccc', hero_level:'s', hero_rank:2)
2.
Hero.all
```

### 過濾
```sql=
1.
SELECT * FROM heroes Where hero_level = 'S';
2.
SELECT *  FROM heroes
Where hero_level = 'S' AND gender = 'F';
```

> SQL的大小寫都可輸入，但ruby要注意轉換（或是查詢時使用upper/lower等方法）
```ruby=
1.
Hero.all.where(hero_level:'S')
or>> Hero.where(hero_level:'S')
2. 
Hero.where(hero_level:'S').where(gender:'F')
or>> Hero.where(hero_level:'S', gender:'F')
```


### 只取用部分資料
> 如果有目的，選取特定的資料而不是全部，可節省效能
```sql	
SELECT name, gender  FROM heroes
Where hero_level = 'S' 
```
```ruby	
Hero.select(:name, :gender).where(hero_level:'S')
```

### 空值
```sql=
SELECT *  FROM heroes
Where age = '' OR  age is NULL;
-- 空字串或沒有填
```
```ruby=
Hero.where(age: nil)
```

### 關鍵字搜尋(like)
```sql=
"%"的用法＝模糊比對
SELECT *  FROM heroes
Where name like '背心'  >> 完全比對
SELECT *  FROM heroes
Where name like '背心%' >> 背心+xxx
SELECT *  FROM heroes
Where name like '%背心%' >> 背心，模糊比對
 ```

```ruby=
Hero.where("name like' '%背心%")
rails沒有like的方法，這是硬寫
```


SELECT *  FROM heroes
Where age BETWEEN  '10' AND '25'
Where age >= 10 AND age =< 25;

#### and/or
列出所有S級和A級的英雄
```sql=
SELECT *  FROM heroes
Where hero_level =  'S'  or  hero_level =  'A' ;
```
```ruby=
Hero.where(hero_level:['S', 'A'])
```
### not
```sql=
SELECT *  FROM heroes
Where hero_level is not 'S'
```
```ruby=
Hero.where.not(hero_level: 'S')
```

### 排除
不是S級也不是A級
```sql=
SELECT * FROM heroes
Where hero_level in ('S', 'A');
```

### 條件句
```sql=
UPDATE heroes
SET age = 10
WHERE id = 25;
```
如果忘記加上第三行，會變成全部的資料都改成十歲！很恐怖！
```ruby=
h = Hero.find(25)
h.update(age: 10)
```

### 更新
- 所有人老一歲
```sql=
UPDATE heroes
SET age = age +1
```
- 同時更新兩個欄位
```sql=
UPDATE heroes
set hero_level = 'B' , hero_rank = 101
WHERE id = 35
```

### 刪除
DELETE FROM heroes
WHERE id = 2
- 記得要加條件句，不然都會刪掉
- 被刪掉的資料，欄位會空在那邊，後面的不會遞補

### 更進階的查詢
```sql=
SELECT count(*) as CC
FROM heroes
WHERE hero_level = 'A'
```
- 將出現的欄位命名為CC

### 加總
```sql=
SELECT sum(age)
FROM heroes
WHERE hero_level = 'A'  
```
```ruby=
1. Hero.where(hero_level:'A').sum
2. Hero.sum(hero_level:'A')
```
- 有要計算什麼，讓資料庫來計算，不要特別跑迴圈計算

### 分組
```sql=
SELECT sum(age)
FROM heroes
GROUP by hero_level
```
- 分別列出各組(等級)年紀的總和

### 挑掉重複的
```sql=
SELECT DISTINCT danger_level 
FROM monsters
> 妖怪裡面的危險等級有什麼？
```

### 排序
```sql=
SELECT *
FROM heroes
WHERE hero_level = 'S'
ORDER by age DESC   --反向排序
```
```ruby=
Hero.where(hero_level:'S').order("age DESC")
or>> Hero.where(hero_level:'S').order(age: :DESC)
```

### 只看前三筆
```sql=
SELECT *
FROM heroes
WHERE hero_level = 'S'
ORDER by hero_rank
LIMIT 3
```


## 多個表格-ER圖(Entity Relationship Diagram)
- 可以手繪或軟體轉
- 開始作業前先進行繪製，比較清楚會需要用到哪些model


#### mySQL
* Restrict
* Cascade
* set null
* no action

### 外部鍵（FK）
- PK需要獨一無二、FK本身不用
- 甚至可以是空值
#### 外部鍵的限制


### 資料完整性

### 交集
inner join
在rails中，只要用到多對多，就有用到join

```sql=
SELECT m.name, danger_level,
FROM monsters as m
INNER JOIN heroes as h
on m.kill_by = h.id
WHERE m.kill_by != '' and h.hero_level = 'S'
```



---
# 附件
- [上課投影片](https://discord.com/channels/748042598983401482/748046752870826045/777817409255112724) 
- [範例檔(SQLite)](https://discord.com/channels/748042598983401482/748046752870826045/777789558233235518) 
- [範例檔(MySQL)](https://discord.com/channels/748042598983401482/748046752870826045/777817496345378856)
- [資料庫筆記整理](https://hackmd.io/-MZwSOngT_Gv7C-dUjBzGA)
- [Running an SQL Injection Attack(youtube)](https://www.youtube.com/watch?v=ciNHn38EyRc)