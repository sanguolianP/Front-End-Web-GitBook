# ES 7  

## async & await

 async 是一个修饰符  
 async 定义的函数会默认的返回一个Promise对象resolve的值，因此对async函数可以直接进行then操作,返回的值即为then方法的传入函数  

await 也是一个修饰符  
await 关键字只能放在 async 函数内部， await 关键字的作用就是获取 Promise中返回的内容， 获取的是Promise函数中resolve或者reject的值  
如果await 后面并不是一个Promise的返回值，则会按照同步程序返回值处理  

关于async & await中的错误捕获  
既然.then(..)不用写了，那么.catch(..)也不用写，可以直接用标准的try catch语法捕捉错误  

```js
var sleep = function (time) {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            // 模拟出错了，返回 ‘error’
            reject('error');
        }, time);
    })
};

var start = async function () {
    try {
        console.log('start');
        await sleep(3000); // 这里得到了一个返回错误
        
        // 所以以下代码不会被执行了
        console.log('end');
    } catch (err) {
        console.log(err); // 这里捕捉到错误 `error`
    }
};
```