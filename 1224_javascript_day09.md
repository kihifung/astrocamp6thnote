# 1223_javascript_day09

[![hackmd-github-sync-badge](https://hackmd.io/WSNqPxU4Sq--B4zA6ghg7A/badge)](https://hackmd.io/WSNqPxU4Sq--B4zA6ghg7A)


#### 上課日期：1223
###### tags: `javascript`
###### tags: `Vanilla JavaScript`
###### tags: `5xruby`

---



---
# 相關連結:
- [課程影片](https://campus.5xruby.tw/courses/1136422/lectures/25361517)
 - [課程練習檔(github)](https://github.com/kaochenlong/shopping_cart_js)
## VScode擴充功能
- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
- [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass)




---
# 0. 目錄
[TOC]


---
### 1. 增加一些監聽事件
> 設定相關class名稱 remove-item-btn
```htmlmixed=
<button class="remove-item-btn btn btn-danger btn-sm"></button>
```

> 刪除按鈕、刪除整行(main.js)

```javascript=
document.addEventListener('DOMContentLoaded', () => {
  const removeItemBtns = document.querySelectorAll('.remove-item-btn')

  removeItemBtns.forEach(btn => {
    btn.addEventListener('click', e => {
      const row = e.currentTarget.parentElement.parentElement
      row.remove()
    })
  })
})
```
- parentElement：第一個只刪除按鈕；第二個是再往上一層，刪除整行

### 2. 
> 增加class名稱
```htmlmixed=
<tr class="cart-item">
  <td><input class="quantity"></td>  
  <td class="price">$8.5</td>
  <td class="subtotal">$8.5</td>
</tr>
```

> 把setRemoveItemBtn拉出來
```javascript=
function setRemoveItemBtn(e) {
  const row = e.currentTarget.parentElement.parentElement
  row.remove()
  } 
```

> 刪除與購物車計算連動
```javascript=
function updateCart() {
    const cartItems = document.querySelectorAll('.cart .cart-item')

    let total = 0
    cartItems.forEach(item => {
      const quantity = item.querySelector('.quantity').value
      const price = item.querySelector('.price').innerText.replace('$', '')
      total += (quantity * price);
    })
    document.querySelector('.total-price').innerText = `$${total}`
  }
```
- 設定class名稱quantity, price, total-price






---
### 3. 幫輸入框加上事件
> xxxx
```javascript=
  const inputs = document.querySelectorAll('.cart .quantity')
  inputs.forEach(input => {
    input.addEventListener('change', setQuantity)
  })
```

```javascript=
function setQuantity(e) {
  console.log('hi');
}
```
- `console.log('hi');`，暫時的，確認有寫正確可以印出東西

> 更簡潔的程式碼
> 
把這個

```javascript=
  const removeItemBtns = document.querySelectorAll('.remove-item-btn')

  removeItemBtns.forEach(btn => {
    btn.addEventListener('click', setRemoveItemBtn)
  })
```
改成這個
```javascript=
  document.querySelectorAll('.remove-item-btn').forEach(btn => {
    btn.addEventListener('click', setRemoveItemBtn)
  })
```
quantity的部分比照辦理


---
# 4. 把上面的商品加到購物車

```javascript=
  const row = document.createElement('tr')
  row.classList.add('cart-item')
  row.innerHTML = `
    <td>${productName}</td>
    <td><input type="number" value="1" class="quantity"></td>
    <td class="price">$${price}</td>
    <td class="subtotal">$${price}</td>
    <td><button class="remove-item-btn btn btn-danger btn-sm"><i class="fas fa-trash-alt"></i></button></td>
  `
  const itemList = document.querySelector('.item-list')
  itemList.appendChild(row)

  row.querySelector('.remove-item-btn')
     .addEventListener('click', setRemoveItemBtn)

  row.querySelector('.cart .quantity')
     .addEventListener('change', setQuantity)

  updateCart()
}
```

# 5. 新增品項會併到原有同名品項
> 而不是每次按每次新增一列
```javascript=
function setQuantity(e) {
  const input = e.target
  let quantity = input.value
  if (quantity <= 0) {
    quantity = 1
    e.target.value = quantity
  }

  const cartItem = input.parentElement.parentElement
  const price = cartItem.querySelector('.price').innerText.replace('$', '')
  cartItem.querySelector('.subtotal').innerText = `$${quantity * price}`

  updateCart()
}
```

# 6. 更新購物車（小計）
> 數量更新時，小計也會更新
```javascript=
function updateCart() {

    item.querySelector('.subtotal').innerText = `$${ quantity * price }`

  })
```

# 7. 清空購物車
> 先設定按鈕名稱`class="empty-cart-btn`
```javascript=
document.addEventListener('DOMContentLoaded', () => {
  document.querySelector('.empty-cart-btn').addEventListener('click', emptyCart)
}
```
```javascript=
function emptyCart(e) {
  document.querySelector('.item-list').innerHTML = ''
  updateCart()
}
```


---
# 重新做一次
- 先切回到初始的commit
```vim
$ git add .
$ git commit -m "finish"
$ git reset 91915b30 --hard
```

### 部署
- [完成品連結](https://dazzling-shockley-8a7cb0.netlify.app/)
- [netlify](https://www.netlify.com/) 
  - 簡便的部署方案[說明](https://docs.netlify.com/site-deploys/overview/#deploy-summary)

---
# 練習
1. 用vue.js來寫
  - 課程練習檔可參考
2. 用react.js來寫


---
# 附件

- [這裡是附件的標題](這裡放連結) 


---
# 第七屆說明會
> 教室都不能使用喔
* 12/23(Wed.)
* 12/29(Tue.)
* 01/07(Thu.)
* 01/13(Wed.)
* 
- [詳見招生連結](https://astro.5xruby.tw/#seminars-list)
