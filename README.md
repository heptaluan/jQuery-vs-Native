## 使用原生 js 来替代 jQuery




#### 获取元素

```js
function $(el) {
  return document.querySelector(el)
}

// 转换为数组
function $$(el) {
  return Array.prototype.slice.call(document.querySelectorAll(el))
}
```




#### 添加元素到匹配的元素集合（add）

```js
$$(el).push(newEl)
```




#### 添加类名（addClass）

```js
el.classList.add(className)
```




## DOM 相关


#### 插入元素（after）

```js
el.parentNode.insertBefore(newEl, el.nextSibling)
```




#### 插入元素（append）

```js
el.appendChild(newEl)
```




#### 插入元素（before）

```js
el.parentNode.insertBefore(newEl, el)
```




#### 获取/设置 元素属性（attr）

```js
// 获取
el.getAttributr("src")

// 设置
el.setAttribute("src", "../img/foo.png")
```




#### 深度拷贝（clone）

```js
el.cloneNode()
```




#### closest

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




#### 获取/设置 CSS

```js
// 获取
// 解决当 style 值为 auto 时，返回 auto 的问题
const win = el.ownerDocument.defaultView

// null 为不返回伪类元素
win.getComputedStyle(el, null).color

// 设置
el.style.color = "red";

// 一次性设置多个样式
const cssObj = {color: "red", font-size: "18px"}

for (let k in cssObj) {
    el.style[key] = cssObj[k];
}

// 方法二
const cssText = "color: red; font-size: 18px"

el.style.cssText += cssText;
```




#### 移除集合中匹配元素的所有子节点

```js
el.innerHTML = "";
```





## 筛选元素


#### 筛选元素（children）

```js
el.children
```





#### 筛选元素（find）

```js
el.querySelectorAll(selector)
```





#### 筛选元素（has）

```js
$$(selector).filter(el => el.querySelector("div") !== null)
```








#### 筛选元素（hasClass）

```js
el.classList.contains(className)
```








#### 获取/设置 元素的 html 内容（html()）

```js
el.innerHTML = htmlString
```








#### 获取第一个元素的当前计算高度值 （innerHeight）

```js
el.clientHeight
```
