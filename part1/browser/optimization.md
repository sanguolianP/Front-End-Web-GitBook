# 优化  

## 1.性能优化  

### 性能优化原则  
* 多使用内存、缓存或者其他方法  
* 减少CPU的计算、减少网络请求、减少IO  

<br/>

### 资源加载优化  
* 静态资源的压缩合并  
```html
<script src="a.js"></script>
<script src="b.js"></script>
<script src="c.js"></script>
=>
<script src="abc.js"></script>
```  
* 静态资源的缓存  
```html
//通过链接名字控制缓存
<script src="abc_1.js"></script>
//只有内容改变的时候，链接名字才会改变
<script src="abc_2.js"></script>
```
* 使用CDN让资源加载更快  
```html
//引入CDN
<script src="//cdn.bootcss.com/highlight.js/9.11.0/highlight.min.js"></script>
<script>hljs.initHighlightingOnLoad();</script>
```
* 使用SSR(服务端渲染)后端渲染，数据直接输出到HTML中  
  * Vue 和 React 提出的概念  
  * 其实 jsp php asp 都属于后端渲染  


### 渲染优化  

* CSS放前面，JS放后面  

* 懒加载(图片懒加载、下拉加载更多)  
```html
<img id="img1" src="preview.png" data-realsrc="abc.pnng" />
<script type="text/javascript">
    var img1 = document.getElementById(img1);
    img1.src = img1.getAttribute('data-realsrc');
</script>
```

* 减少DOM查询，对DOM查询做缓存  
```js
//未缓存DOM查询
for(let i=0; i < document.getElementsByTagName('p').length; i++){
    //todo something
}
//缓存了DOM查询
let pList = document.getElementsByTagName('p');
for(let i=0; i < pList.length; i++){
    //todo something
}
```

* 减少DOM操作，多个操作尽量合并  
```js
//合并DOM插入
let listNode = document.getElementById('list');
//要插入10个<li>标签
let frag = document.createDocumentFragment();
for(let i=0; i<10; i++){
    let li = document.createElement('li');
    li.innerHTML = `LisItem${i}`;
    frag.appendChild(li);
}
listNode.appendChild(frag);
```
* 事件节流  
```js
let textarea = document.getElementById('textArea');
let timer = null;
textarea.addEventListener('keyup', ()=>{
    if(timer)
        clearTimeout(timer);
    timer = setTimeout(()=>{
        //触发事件
    }, 100);
})
```

* 尽早执行操作（如DOMContentLoaded）

## 2.SEO优化  
### meta标签  
META标签用来描述一个HTML网页文档的属性，例如作者、日期和时间、网页描述、关键词、页面刷新等，针对搜索引擎和更新频度的描述和关键词。  
常用的meta标签  
```html
<!-- 字体编码 -->
<meta charset="utf-8" />
<!-- 关键字 -->
<meta name="keywords" content="" />
<!-- 说明 -->
<meta name="description" content="" />
<!-- 作者 -->
<meta name="author" content="" />
<!-- 设置文档宽度、是否缩放 -->
<meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no" />
<!-- 优先使用IE最新版本或chrome -->
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
<!-- 360读取到这个标签立即钱换到极速模式 -->
<meta name="renderer" content="webkit" />
<!-- 禁止百度转码 -->
<meta http-equiv="Cache-Control" content="no-siteapp" />
<!-- UC强制竖屏 -->
<meta name="screen-orientation" content="portrait" />
<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait" />
<!-- UC强制全屏 -->
<meta name="full-scerrn" content="yes" />
<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="ture" />
<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app" />
<!-- UC应用模式 -->
<meta name="browsermode" content="application">
<!-- window phone 点亮无高光 -->
<meta name="msapplication-tap-highlight" content="no" />
<!-- 安卓设备不自动识别邮件地址 -->
<meta name="format-detection" name="email=no" />
```