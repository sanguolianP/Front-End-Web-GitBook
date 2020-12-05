# 变量类型和计算

## 1. 值类型和引用类型的区别

### 值类型和引用类型的区别

**基本数据类型保存在栈内存，引用类型保存在堆内存中**

根本原因在于保存在栈内存的必须是**大小固定**的数据，引用类型的大小不固定，只能保存在堆内存中，但是可以把它的地址写在栈内存中以供我们访问

* 如果是基本数据类型，则按值访问，操作的就是变量保存的**值** 
* 如果是引用类型的值，我们只是通过保存在变量中的引用类型的**地址**来操作实际对象

```javascript
// 常见值类型
let a                 // undefined
const s = 'abc'       // String
const n = 100         // Number
const b = true        // Boolean
const s = Symbol('s') // Symbol, ES6新类型

// 常见引用类型
const obj = { x:100 } // 对象
const arr = ['a', 123, {c:'456'}] // 数组

const n = null   // 特殊引用类型，指针指向空地址
function fn() {} //  特殊引用类型，但不能用于存储数据，所以没有“复制拷贝函数”一说
```

### typeof 能判断哪些类型

typeof 返回的是一个小写字符型的值

* **识别所有值类型**
* **识别函数**
* **判断是否是引用类型（不可再细分）**

```javascript
// 判断所有值类型
let a                 // undefined
const str = 'abc'       // string
const n = 100         // number
const b = true        // boolean
const s = Symbol('s') // symbol, ES6新类型

typeof a    // 'undefined'
typeof str  // 'string'
typeof n    // 'number'
typeof b    // 'boolean'
typeof s    // 'symbol'

// 判断函数
typeof console.log  // 'function'
typeof function () {} // 'function'

// 能判断是否是引用类型
typeof null      // 'object'
typeof ['a','b'] // 'object'
typeof { x:100 } // 'object'
```

### 何时使用 === 何时使用 ==



###   

## 2. 手写 JS 深拷贝



## 3. 变量计算

