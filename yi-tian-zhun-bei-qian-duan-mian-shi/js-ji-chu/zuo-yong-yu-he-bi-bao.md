# 作用域和闭包

## 知识点

### 作用域和自由变量

**作用域**

* 全局作用域
* 函数作用域
* 块级作用域（ES6新增）

**自由变量**

* 一个变量在当前作用域没有定义，但被使用了
* 向上级作用域，一层一层依次寻找，直到找到为止
* 如果到全局作用域都没找到，则报错 xx is not defined

### 闭包

**作用域应用的特殊情况，有两种表现：**

* **函数作为参数被传递**
* **函数作为返回值被返回**

```javascript
// 函数作为返回值
function create() {
    const a = 100
    return function () {
    console.log(a)
    }
}

const fn = create()
const a = 200
fn() // 100

// 函数作为参数被传递
function print(fn) {
    const a = 200
    fn()
}
const a = 100
function fn() {
    console.log(a)
}
print(fn) // 100

// 所有的自由变量的查找，是在函数定义的地方，向上级作用域查找
// 不是在执行的地方！！！

```

### this

* **作为普通函数**
* **使用 call apply bind** 
* **作为对象方法被调用**
* **在 class 方法中调用**
* **箭头函数**

## 面试题

### this 的不同应用场景，如何取值

### 手写 bind 函数

### 实际开发中闭包的应用场景，举例说明

```javascript
// 闭包隐藏数据，只提供 API
function createCache() {
    const data = {} // 闭包中的数据，被隐藏，不被外界访问
    return {
        set: function (key, val) {
            data[key] = val
        },
        get: function (key) {
            return data[key]
        }
    }
}

const c = createCache()
c.set('a', 100)
console.log( c.get('a') )
```

### 创建10个\`&lt;a&gt;\`标签，点击的时候弹出来对应的序号

```javascript
let a
for (let i = 0; i < 10; i++) {
    a = document.createElement('a')
    a.innerHTML = i + '<br>'
    a.addEventListener('click', function (e) {
        e.preventDefault()
        alert(i)
    })
    document.body.appendChild(a)
}

```



