# 图文样式/响应式/CSS3

## 1. line-height 的继承问题

```markup
<!-- 如下代码，p 标签的行高是多少？ -->
<style type="text/css">
    body {
        font-size: 20px;
        line-height: 200%;
    }
    p {
        background-color: #ccc;
        font-size: 16px;
    }
</style>
<body>
    <p>这是一行文字</p>
</body>
```

* **如果父标签的 line-height 写的是具体数值，如30px，则直接继承该数值**
* **如果父标签的 line-height 写的是比例，如1.5/2，则用子标签的font-size乘该比例**
* **如果父标签的 line-height 写的是百分比，如200%，则用父标签的font-size乘该百分比**

## 2. rem是什么？

### rem是一个长度单位

* **px，绝对长度单位，最常用**
* **em，相对长度单位，相对于父元素，不常用**
* **rem，相对长度单位，相对于根元素（html），常用于响应式布局**

## 3. 如何实现响应式？

* **media-query，根据不同的屏幕宽度设置根元素font-size**
* **用rem，基于根元素的相对单位**

```markup
<!-- 媒体查询示例 -->
<style type="text/css">
    @media only screen and (max-width: 374px) {
        /* iphone5 或者更小的尺寸，以 iphone5 的宽度（320px）比例设置 font-size */
        html {
            font-size: 86px;
        }
    }
    @media only screen and (min-width: 375px) and (max-width: 413px) {
        /* iphone6/7/8 和 iphone x */
        html {
            font-size: 100px;
        }
    }
    @media only screen and (min-width: 414px) {
        /* iphone6p 或者更大的尺寸，以 iphone6p 的宽度（414px）比例设置 font-size */
        html {
            font-size: 110px;
        }
    }

    body {
        font-size: 0.16rem;
    }
    #div1 {
        width: 1rem;
        background-color: #ccc;
    }
</style>
<body>
    <div id="div1">
        this is div
    </div>
</body>
```

### vw 和 vh

* **rem 的弊端：媒体查询 + rem 是一种阶梯性的方式，不能对每种像素类型都适配**
* **网页视口尺寸：**
  * **window.screen.height  // 设备屏幕高度**
  * **window.innerHeight  // 网页视口高度**
  * **document.body.clientHeight  //  body的高度**

**vh：网页视口高度的 1/100**

**vw：网页视口宽度的 1/100**

**vmax：取 vh 和 vw 两者的最大值**

**vmin：取 vh 和 vw 两者的最小值**

## 4. 关于 CSS3 动画

