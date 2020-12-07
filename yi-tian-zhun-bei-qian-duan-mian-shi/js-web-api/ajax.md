# Ajax

## 知识点

XMLHttpRequest

```javascript
const xhr = new XMLHttpRequest()
xhr.open('GET', '/data/test.json', true)
xhr.onreadystatechange = function () {
    if (xhr.readyState === 4) {
        if (xhr.status === 200) {
            alert (xhr.responseText)
        } else {
            alert (`其他情况`)
        }
    }
}
xhr.send(null)
```

状态码

跨域：同源策略，跨域解决方案

## 面试题

手写一个简易的 ajax

跨域的常用实现方式

