## 使用原生 js 来替代 jQuery




#### 获取元素

```js
// jQuery
$(selector)


// Native
function $(el) {
  return document.querySelector(el)
}

// 转换为数组
function $$(el) {
  return Array.prototype.slice.call(document.querySelectorAll(el))
}
```




#### 添加元素到匹配的元素集合（数组）

```js
// jQuery
$(selector).add($(newEl))


// Native
$$(selector).push(newEl)
```




#### 添加类名（addClass）

```js
el.classList.add(className)
```


