# 前端知识体系


---
* [前端基础](part1/README_part1.md)  
    * [浏览器](part1/browser/README.md)  
        * [渲染机制](part1/browser/render.md)  
            * [DOM](part1/browser/render.md)  
            * [重绘/回流](part1/browser/render.md)  
            * [shadow DOM](part1/browser/render.md)  
            * [渲染阻塞](part1/browser/render.md)  
        * [浏览器缓存](part1/browser/cache.md)  
            * [HTTP缓存](part1/browser/cache.md)  
                * [强缓存]()  
                * [协商缓存]()  
            * [缓存机制](part1/browser/cache.md)  
            * [本地存储](part1/browser/cache.md)  
                * [Cookie]() 
                * [Storage]() 
                * [IndexDB]() 
        * [同源策略](part1/browser/OriginPolicy.md)  
            * [跨域访问方法](part1/browser/OriginPolicy.md)  
        * [优化](part1/browser/optimization.md)  
            * [性能优化](part1/browser/optimization.md)
                * [资源加载优化]() 
                * [渲染优化]() 
            * [SEO优化](part1/browser/optimization.md)
                * [meta标签]() 
        * [安全](part1/browser/safety.md)  
            * [HTTPS](part1/browser/safety.md) 
            * [SSL](part1/browser/safety.md)  
            * [TLS](part1/browser/safety.md)  
                * [非对称加密原理]() 
            * [网络攻击](part1/browser/safety.md) 
                * [XSS]() 
                * [CSRF]() 
                * [iframe]() 
                * [opener]() 
                * [ClickJacking]() 
                * [HSTS]() 
                * [CDN劫持]() 
    * [HTML](part1/htmlcontent/README.md)  
        * [HTML5](part1/htmlcontent/README.md)  
            * [语义化标签](part1/htmlcontent/semanticTag.md)  
            * [canvas & svg](part1/htmlcontent/canvasSvg.md)    
            * [响应式 meta](part1/htmlcontent/responsive.md)  
    * [CSS](part1/CSS/README.md)  
        * [盒模型](part1/CSS/boxmodel.md)  
        * [选择器](part1/CSS/selector.md)  
            * [优先级策略](part1/CSS/selector.md)  
            * [伪类/伪元素](part1/CSS/selector.md)  
        * [样式表继承](part1/CSS/cssinherit.md)  
        * [CSS3](part1/CSS/css3.md)  
            * [Flex & Grid](part1/CSS/css3.md)  
            * [filter](part1/CSS/css3.md)  
            * [reset.css & rem](part1/CSS/css3.md)  
            * [Transform & Animation](part1/CSS/css3.md)  
        * [BFC](part1/CSS/bfc.md)  
            * [高度塌陷](part1/CSS/bfc.md)  
            * [margin合并与塌陷](part1/CSS/bfc.md)  
            * [元素水平垂直居中](part1/CSS/bfc.md)  
            * [float以及清除float](part1/CSS/bfc.md)  
            * [position 嵌套 & 覆盖](part1/CSS/bfc.md)  
    * [JavaScript](part1/JavaScript/README.md)  
        * [ECMAScript](part1/JavaScript/es/es5.md)  
            * [ES5](part1/JavaScript/es/es5.md)  
                * [基本数据类型](part1/JavaScript/es/es5.md)  
                * [函数级作用域](part1/JavaScript/es/es5.md)  
                * [闭包](part1/JavaScript/es/es5.md)  
                * [方法调用/函数调用](part1/JavaScript/es/es5.md)  
                * [高阶函数](part1/JavaScript/es/es5.md)  
                * [模块加载](part1/JavaScript/es/es5.md)  
            * [ES6](part1/JavaScript/es/es6.md)  
                * [新的变量声明方式](part1/JavaScript/es/es6.md)  
                * [变量的解构赋值](part1/JavaScript/es/es6.md)  
                * [模板字符串](part1/JavaScript/es/es6.md)  
                * [扩展运算符](part1/JavaScript/es/es6.md)  
                * [数组新方法](part1/JavaScript/es/es6.md)  
                * [ES6数据结构](part1/JavaScript/es/es6.md)  
                * [迭代器](part1/JavaScript/es/es6.md)  
                * [箭头函数](part1/JavaScript/es/es6.md)  
                * [Class](part1/JavaScript/es/es6.md)  
                * [Promise](part1/JavaScript/es/es6.md)  
                * [Proxy与数据劫持](part1/JavaScript/es/es6.md)  
            * [ES7+](part1/JavaScript/es/es7.md)  
                * [async & await](part1/JavaScript/es/es7.md)  
            * [原型链](part1/JavaScript/es/protolink.md)  
                * [new 操作符](part1/JavaScript/es/protolink.md)  
                * [bind/call/apply](part1/JavaScript/es/protolink.md)  
                * [深浅拷贝](part1/JavaScript/es/protolink.md)  
        * [BOM](part1/JavaScript/bom/domevent.md)  
            * [DOM交互](part1/JavaScript/bom/domevent.md)  
                * [事件代理](part1/JavaScript/bom/domevent.md)  
                    * [冒泡/捕获](part1/JavaScript/bom/domevent.md)  
                    * [两种监听方法](part1/JavaScript/bom/domevent.md)  
            * [表单管理](part1/JavaScript/bom/form.md)  
                * [如何提交一个表单](part1/JavaScript/bom/form.md)  
        * [History API](part1/JavaScript/history.md)  
        * [XHR API](part1/JavaScript/xhr.md)  
        * [异步机制](part1/JavaScript/async.md)  
            * [Event Loop](part1/JavaScript/async.md)  
                * [MacroTask/MicroTask](part1/JavaScript/async.md)    
        * [垃圾回收机制](part1/JavaScript/trash.md)  
            * 标记清除/引用计数  


---
* 前端核心  
    * 前后端数据交互  
        * RESTFUL API  
        * Ajax 库封装  
        * Fetch 库封装  
        * 跨域实现  
    * 移动端开发  


---
* 前端进阶  
    * 前端工作流  
    * 流行框架  
        * Vue  
            * 生命周期流程  
            * HTML模板
            * 组件通信机制  
            * 高阶组件  
            * Router原理  
            * VueX状态管理  
                * Action/Mutation
            * 双向绑定原理  
            * Virtual Dom
                * Diff 原理
        * React  
            * 生命周期  
            * JSX  
            * Redux  
            * 组件状态管理  
        * Angular  
    * 工程实践  
        * 模块化  
            * ES5  
                * CommonJs/AMD/CMD 思想  
            * ES6  
                * Class
                    * Polyfill  
        * 用户鉴权  
            * OAuth  
        * 组件化  
        * 依赖构建  
            * WebPack  
            * Glup  
        * 版本管理  
            * Git
                * 分支机制
        * 包管理  
        * 性能优化  
            * base64编码/精灵图  
            * 懒加载/预加载  
            * 静态资源的渲染阻塞  
            * CSS选择器优化/表达式优化  
            * CDN  
    * Node.js  


---
* 计算机基础  
    * [计算机网络](part4/computerBasic/network.md)  
        * OSI七层模型  
        * HTTP  
            * 1.0/1.1/2.0  
                * 1.0
                * 1.1 持久化  
                * 2.0 管线/服务端推送  
            * 状态码  
            * 缓存控制策略  
        * TCP  
            * 3次握手/4次挥手  
            * 滑动窗口  
                * 慢启动/拥塞控制  
            * 可靠通信  
                * TCP状态机  
        * UDP  
        * WebSocket  
    * [操作系统](part4/computerBasic/os.md)  
        * 进程/线程  
            * 资源共享
            * 通信方式
            * 死锁与互斥  
        * Linux 指令  
    * [数据库](part4/computerBasic/database.md)  
        * MySQL  
        * Redis  
        * MongoDB  


---
* 算法与数据结构  
    * 数据结构  
        * 数组  
        * 字符串  
        * 链表  
        * 栈  
        * 队列  
        * 树  
            * 二叉树  
            * B树/B+树  
        * 哈希表  
    * 算法  
        * 递归  
        * DFS/BFS  
        * 动态规划(DP)  
        * 排序  
        * 位运算  
        * 滑动窗口  


---
* 设计模式  
---
* [前端面试经验](mj.md)