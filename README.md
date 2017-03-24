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



## DOM 相关

#### 添加元素到匹配的元素集合（数组）

```js
// jQuery
$(selector).add($(newEl))


// Native
$$(selector).push(newEl)
```


#### 添加类名（addClass）

```js
// jQuery
$(el).addClass(className)


// Native
el.classList.add(className)
```


#### 插入元素（after）

```js
// jQuery
$(el).after("<div></div>")


// Native
el.parentNode.insertBefore(newEl, el.nextSibling)
```

