# Event Loop

## 消息队列与事件循环

JavaScript是通过JS引擎线程与浏览器中其他线程交互协作实现异步  
这就是消息队列和事件循环

* **栈**存储的是同步任务，就是那些能立即执行、不耗时的任务，如变量和函数的初始化、事件的绑定等等那些不需要回调函数的操作都可归为这一类
* **堆**用来存储声明的变量、对象
* **队列**就是消息队列，一旦某个异步任务有了响应就会被推入队列中。如用户的点击事件、浏览器收到服务的响应和setTimeout中待执行的事件，每个异步任务都和回调函数相关联  

JS引擎线程用来执行栈中的同步任务，当所有同步任务执行完毕后，栈被清空，然后读取消息队列中的一个待处理任务，并把相关回调函数压入栈中，单线程开始执行新的同步任务。

JS引擎线程从消息队列中读取任务是不断循环的，每次栈被清空后，都会在消息队列中读取新的任务，如果没有新的任务，就会等待，直到有新的任务，这就叫**事件循环**

## 微任务 宏任务

在浏览器环境下  
js执行为单线程（不考虑web worker），所有代码皆在执行线程调用栈完成执行。当执行线程任务清空后才会去轮询取任务队列中任务。

### 任务队列

**异步任务分为 task\(宏任务，macroTask\) 和 microTask\(微任务\) 两类**  
当满足执行条件时，task和microtask会被放入**各自的队列中**等待放入执行线程执行，我们把这两个队列称为**Task Queue\(也叫Macrotask Queue\)和Microtask Queue**。

* task: script / setTimeout / setInterval / I/O / UI render  
* microtask: promise / Obeject.observe / MutationObserver  

具体执行过程

> 1.执行完主线程中的任务  
> 2.取出 MicroTask Queue 中的任务执行直到清空  
> 3.取出 MacroTask Queue 中的一个任务执行  
> 4.取出 MicroTask Queue 中的任务执行直到清空  
> 5.重复 3 和 4

**即为同步执行完成，一个宏任务，所有微任务；一个宏任务，所有微任务**

注意

* 在浏览器页面中可以认为初始执行线程中没有代码，每一个script标签中的代码是一个独立的task，即会执行完前面的script中创建的microtask再执行后面的script中的同步代码。  
* 如果microtask一直被添加，则会继续执行microtask，“卡死”macrotask。  
* 即promise的then和catch才是microtask，本身的内部代码不是  

  ```javascript
  new Promise((resolve, reject) =>{console.log(‘同步’);resolve()})
  .then(() => {console.log('异步')})
  ```

测试代码

```javascript
function sleep(time) {
  let startTime = new Date()
  while (new Date() - startTime < time) {}
  console.log('1s over')
}

setTimeout(() => {
  console.log('setTimeout - 1')
  setTimeout(() => {
      console.log('setTimeout - 1 - 1')
      sleep(1000)
  })
  new Promise(resolve => resolve()).then(() => {
      console.log('setTimeout - 1 - then')
      new Promise(resolve => resolve()).then(() => {
          console.log('setTimeout - 1 - then - then')
      })
  })
  sleep(1000)
})

setTimeout(() => {
  console.log('setTimeout - 2')
  setTimeout(() => {
      console.log('setTimeout - 2 - 1')
      sleep(1000)
  })
  new Promise(resolve => resolve()).then(() => {
      console.log('setTimeout - 2 - then')
      new Promise(resolve => resolve()).then(() => {
          console.log('setTimeout - 2 - then - then')
      })
  })
  sleep(1000)
})
```

浏览器输出

```javascript
setTimeout - 1 //1为单个task
1s over
setTimeout - 1 - then
setTimeout - 1 - then - then 
setTimeout - 2 //2为单个task
1s over
setTimeout - 2 - then
setTimeout - 2 - then - then
setTimeout - 1 - 1
1s over
setTimeout - 2 - 1
1s over
```

