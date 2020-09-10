# DOM交互

### DOM本质

浏览器把浏览器拿到的html代码，结构化出一个浏览器能识别并且可进行js操作的一个模型  
该结构类似数据结构中的树

### DOM节点操作

**获取DOM节点**

* getElementById\(\)  
* getElementsByTagName\(\)  
* getElementsByClassName\(\)  
* querySelectorAll\(\)

**property**  
表述DOM对象的属性，它属于Js里对象的范畴

**Attribute**  
表述HTML标签的特性集合  
getAttrbute / setAttribute  
**attributes是属于property的一个子集**

### DOM结构操作

**新增节点**  
`document.createElement`  
`div.appendChild('p')`

**删除节点**  
`父元素.removeChild('p')`

**修改节点**  
innerHTML\(非表单元素\) / value\(表单元素\)

**查找节点**  
获取父节点  
parentElement / parentNode

获取子节点  
childNodes / children  
firstChild / firstElementChild \(前为IE，后为火狐谷歌写法，下同\)  
lastChild / lastElementChild  
nextSibling / nextElementSibling  
previousSibling / previousElementSibling

## 事件代理

冒泡/捕获

**两种监听方法**  
onclick事件在同一时间只能指向唯一对象，如果绑定多个同类型的事件,前边的会被覆盖

addEventListener ：

* addEventListener它允许给一个事件注册多个监听器
* addEventListener对任何DOM都是有效的，而onclick仅限于HTML
* addEventListener可以控制listener的触发阶段，（捕获/冒泡）。对于多个相同的事件处理器，不会重复触发，不需要手动使用removeEventListener清除
* IE9使用attachEvent和detachEvent

## BOM

navigator

```javascript
var ua = navigator.userAgent
var isChrome = ua.indexOf('Chrome')
```

screen

```javascript
screen.width()
screen.height()
```

location

```javascript
console.log(location.href) //整个url
console.log(location.protocol) //协议 'http' 'https'
console.log(location.host) //域名
console.log(location.pathname) //域名后的文件路径 '/learn/133'
console.log(location.search) //查询字符串 比如？后面的
console.log(location.hash) // 哈希 #后面的
```

history

```javascript
history.back()
history.forward()
```

**检测浏览器的类型**  
通过navigator.userAgent

**拆解url的各部分**  
通过location

## 表单管理

