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

```javascript
// 除了 == null 之外，其他一律用 ===，例如：

const obj = { x:100 }
if (obj.a == null) {}
// 相当于：
// if (obj.a===null || obj.a===undefined)
```

###   

## 2. 手写 JS 深拷贝



## 3. 变量计算

### \(1\) 字符串拼接

**只要是在 + 两边有字符串的，都会转成字符串进行拼接**

```javascript
const a = 100 + 10    // 110
const b = 100 + '10'  // '10010'
const c = true + '10' // 'true10'
```

### \(2\) ==

**== 会进行类型转换**

```javascript
100 == '100'  // true
0 == ''  // true
0 == false  // true
false == ''  // true
null == undefined  // true
```

### \(3\) if 语句和逻辑运算

* **truly 变量：!!a === true 的变量**
* **faslely 变量：!!a === false 的变量**

```javascript
// 以下是 faslely 变量。除此之外都是truly变量
!!0 === false
!!NaN === false
!!'' === false
!!null === false
!!undefined === false
!!false === false
```

**在 if 语句和逻辑运算的时候会判断一个变量是 truely 还是 falsely**

```javascript
// falsely 变量
const c = ''
const d = null
let e
if (c) {}
if (d) {}
if (e) {}

console.log( 10 && 0 )  // 0 
console.log( '' || 'abc' )  // 'abc'
console.log( !window.abc )  // true
```

