# 异步

## 知识点

单线程和异步

应用场景

callback hell 和 Promise

## 面试题

### 同步和异步的区别是什么

* **基于 JS 是单线程语言**
* **异步不会阻塞代码执行**
* **同步会阻塞代码执行**

### 手写 promise 加载一张图片

```javascript
const url = ''

function loadImg (src) {
    return new Promise ((resolve, reject) => {
        const img = document.createElement('img')
        img.onload = () => {
            resolve(img)
        }
        img.onerror = () => {
            const err = new Error(`图片加载失败 ${src}`)
            reject(err)
        }
        img.src = src
    })
}


loadImg(url).then(img => {
    console.log(img.width)
    return img
}).then(img => {
    console.log(img.height)
}).catch(ex => {
    console.log(ex)
})

```

### 前端使用异步的场景有哪些

* **网络请求，如ajax图片加载**
* **定时任务，如setTimeout**

### 事件循环场景题

