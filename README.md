## 使用原生 js 来替代 jQuery

----

### 获取元素

```js
function $(el) {
  return document.querySelector(el)
}

// 转换为数组
function $$(el) {
  return Array.prototype.slice.call(document.querySelectorAll(el))
}
```


### 添加元素到匹配的元素集合（add）

```js
$$(el).push(newEl)
```

### 添加类名（addClass）

```js
el.classList.add(className)
```

### 插入元素（after）

```js
el.parentNode.insertBefore(newEl, el.nextSibling)
```

### 插入元素（append）

```js
el.appendChild(newEl)
```


### 插入元素（before）

```js
el.parentNode.insertBefore(newEl, el)
```


### 获取/设置 元素属性（attr）

```js
// 获取
el.getAttributr("src")

// 设置
el.setAttribute("src", "../img/foo.png")
```

### 筛选（children）

```js
el.children
```

### 深度拷贝（clone）

```js
el.cloneNode()
```

### closest

从元素本身开始，在 DOM 树逐级向上级元素匹配，并返回最先匹配的祖先元素 

```js
function closest(el, selector = false) {

    const matchesSelector = el.matches || el.webkitMatchesSelector || el.mozMatchesSelector || el.msMatchesSelector;

    do {
        if (matchesSelector.call(el, selector)) {
            return el
        }
    } while ((el = el.parentElement) !== null)

    return null
    
}
```
