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



#### 插入元素（append）

```js
// jQuery
$(el).append("<div></div>")


// Native
el.appendChild(newEl)
```





#### 插入元素（before）

```js
// jQuery
$(el).before("<div></div>")


// Native
el.parentNode.insertBefore(newEl, el)
```





#### 设置/获取 属性（attr）

```js
// jQuery
$(el).attr("src", "../img/foo.png")


// Native
el.getAttribute("src")

el.setAttribute("src", "../img/foo.png")
```





#### 深度拷贝（close）

```js
// jQuery
$(el).clone()


// Native
el.appendChild(newEl)
```





#### 获得匹配元素集合中每个元素的子元素（content）

```js
// jQuery
$(el).contents()


// Native
el.childNodes
```





#### 设置样式（css）

```js
// jQuery
$(el).css("color", "red")


// Native
el.style.color = "red"

----

// jQuery 多个样式
$(el).css({ color: "red", fontSize: "20px" })

// Native
const cssObj = { color: "red", fontSize: "20px" }
for (let k in cssObj) {
    el.style[k] = cssObj[k]
}
```





#### 清空元素（empty）

```js
// jQuery
$(el).empty()


// Native
el.innerHTML = "";
```





#### 过滤元素（filter）

```js
// jQuery
$(selector).filter(filterFn)


// Native
$$(selector).filter(filterFn)
```





#### 寻找元素（find）

```js
// jQuery
$(el).find(selector)


// Native
el.querySelectorAll(selector)
```




#### 寻找元素（parents）

```js
// jQuery
$(el).parents(selector)


// Native
function parents(el, selector = '*') {
    const matchesSelector = el.matches || el.webkitMatchesSelector || el.mozMatchesSelector || el.msMatchesSelector
    const parentsMatch = []
    while ((el = el.parentElement) !== null) {
        if (matchesSelector.call(el, selector)) {
            parentsMatch.push(el)
        }
    }
    return parentsMatch
}
```





#### 筛选元素（has）

```js
// jQuery
$(selector).has("div")


// Native
$$(selector).filter(el => el.querySelector("div") !== null)
```






#### 筛选元素（next）

```js
// jQuery
$(el).next()


// Native
el.nextElementSibling
```





#### 筛选元素（nextAll）

```js
// jQuery
$(el).nextAll()


// Native
const nextAll = []
while ( (el = el.nextElementSibling) !== null ) {
    nextAll.push(el)
}
```





#### 筛选元素（hasClass）

```js
// jQuery
$(el).hasClass(className)


// Native
el.classList.contains(className)
```





#### 设置 html 内容（html）

```js
// jQuery
$(el).html()


// Native
el.innerHTML
```





#### 获取元素属性，宽高等（innerHeight/innerWidth）

```js
// jQuery
$(el).innerHeight()

// Native
el.clientHeight


// jQuery
$(el).innerWidth()

// Native
el.clientWidth
```





#### 获取元素当前坐标（position）

```js
// jQuery
$(el).position()

// Native
left: el.offsetLeft

top: el.offsetTop
```




#### 删除元素（remove）

```js
// jQuery
$(el).remove()

// Native
el.parentNode.removeChild(el)
```




#### 替换元素（replaceWith）

```js
// jQuery
$(el).replaceWith("<div></div>")

// Native
el.parentNode.replaceChild(newEl, el)

// 标签的话用这个
el.outerHTML = "<div></div>"
```





#### 滚动条位置（scrollTop）

```js
// jQuery
$(el).scrollTop()

$(el).scrollTop(20)

// Native
el.scrollTop

el.scrollTop = 20

// 如果全局对象为 window
document.documentElement.scrollTop = 20

document.body.scrollTop = 20
```





#### 过滤元素（兄弟节点 siblings）

待续..




