# 前端面经  

## 头条核心广告部门
### **一面:**

自我介绍  

做项目的初衷  

CSS 垂直水平居中各种方法(写了各种包括absolute定位后未知宽高的垂直水平居中方法)  
问CSS 选择器优先级(答:按权重计算)  
又问CSS !Important 用过吗(什么玩意儿?我太菜了...)  

HTTPS 细节  
HTTP1.0/HTTP1.1/HTTP2.0 区别  
HTTP 状态码 204，各种开头的状态码的意义  

跨域方法介绍(说了jsonp和CORS就过了)  

详细说一下原生Ajax(没让手写但是讲出了详细的代码)  

JS基本数据类型  
简单类型和引用类型的区别  
如何检查一个对象是不是数组  
typeof  和 instanceof的区别  
手写深拷贝

原型链题目(问以下输出)
```js
function exampleFunc () {}  
exampleFunc.prototype.__proto__  
exampleFunc.__proto__  
exampleFunc.__proto__.__proto__  
exampleFunc.__proto__.__proto__.__protp__  
```

事件循环题目(先说事件循环机制，宏任务微任务，然后做题)  
```js
setTimeout(function() {
    console.log('setTimeout');
});
new Promise(function(resolve) {
    console.log('promise');
    for (var i = 0; i < 10000; i++) {
        if(i === 10) {
            console.log('for');
        }
        if (i === 9999) {
          resolve('resolve');
        }
    }
}).then(function(val) {
    console.log(val);
});
console.log('console');
```

算法题  
实现字符串四则运算：   
给定字符串类型的四则运算式子9+(3-1)*3+10/2 求计算结果（提示:后缀表达式，答:不会换一道）  

大数相加 ‘1000’ ‘34455678’  

Vue生命周期  
Vue组件传值  
v-model实现原理(双向绑定原理，答数据劫持，然后开始讲底层源码思路)  
又问底层具体怎么实现的(答实际上是一个发布者订阅者模式)  

手写Vue组件 封装一个类似alert()弹窗的组件  

一面结束(17:00~18:40)
***

### **二面:**

问 CSS3 了解哪些新的属性  
手写CSS3实现一个钟摆的效果  

问移动端适配，rem，媒体查询  

Vue 如何实现父组件监听子组件的生命周期钩子  

HTTP状态码 404/302/304  
HTTP 缓存（强缓存，协商缓存）机制  

手写函数防抖  

算法题 格式混乱字符串转二维数组  
给定一个字符串
```js
strInput = {
1   2      3
  4  5  6
7 8      9
}
strOutput = [
[1,2,3],
[4,5,6],
[7,8,9]
]
```
前端性能监控 Performance (没听过...)  

聊项目，问Vue Swiper 插件的实现原理 (???)  

问高校一般没有前端课程，为什么选择做前端?(答:前端牛逼不枯燥有发展前景有挑战性)  

问实习时间，只能实习暑期三个月嘛，不能一直实习吗  

二面结束(19:30~20:40)
***



