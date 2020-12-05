# 布局

## 盒子模型的宽度如何计算？

```markup
<!-- 如下代码，请问 div1 的 offsetWidth 是多大？ -->
<style>
    #div {
        width: 100px;
        padding: 10px;
        border: 1px solid #ccc;
        margin: 10px;
    }
</style>

<div id="div1"></div>
```

offsetWidth = \(内容宽度 + 内边距 + 边框\)，无外边距。因此**答案是122px**

如果要让offsetWidth等于100px该怎么做？  加上 box-sizing: border-box \(转换成诡异盒模型\)

## margin纵向重叠的问题

```markup
<!-- 如下代码, AAA 和 BBB 之间的距离是多少？-->
<style>
    p {
        font-size: 16px;
        line-height: 1;
        margin-top: 10px;
        margin-bottom: 15px;
    }
</style>

<p>AAA</p>
<p></p>
<p></p>
<p></p>
<p>BBB</p>
```

* 相邻元素的 margin-top 和 margin-bottom 会发生重叠，取两者最大值
* 空白内容的 &lt;p&gt;&lt;/p&gt; 也会重叠
* **答案：15px**

## margin负值的问题

**对 margin 的 top left right bottom 设置负值，有何效果？**

* **margin-top 和 margin-left 负值，元素向上向左移动**
* **margin-right 负值，右侧元素向左移动，自身不受影响**
* **margin-bottom 负值，下侧元素向上移动，自身不受影响**

## BFC的理解和应用

**什么是BFC？ 何如应用？**

* **Block format context , 块级格式上下文**
* **一块独立的渲染区域，内部元素的渲染不会影响边界以外的元素**

**形成 BFC 的常见条件**

* **float 不是 none**
* **position 不是 absolute 或 fixed**
* **overflow 不是 visible**
* **dispaly 是 flex/inline-block 等**

**BFC 的常见应用**

* **清除浮动 \(常设置overflow: hidden\)**

## float布局的问题，以及clearfix

**如何实现圣杯布局和双飞翼布局**

圣杯布局和双飞翼布局的目的

* 三栏布局，中间一栏最先加载和渲染（内容最重要，所以center要放在left和right的前面）
* 两侧内容固定，中间内容随着宽度自适应
* 一般用于 PC 网页

圣杯布局和双飞翼布局的技术总结

* 使用 float 布局
* 两侧使用 margin 负值，以便和和中间内容横向重叠
* 防止中间内容被两侧覆盖，一个用 padding 一个用 margin

**手写 clearfix**

```css
.clearfix:arfter {
    content: '';
    display: table;
    clear: both;
}
.clear {
    *zoom: 1;
}
```

## flex 布局问题（画骰子）

**flex 实现一个三点的骰子**

**flex 常用语法回顾**

* **flex-direction   主轴的方向**
* **justify-content   主轴对齐方式**
* **align-items   交叉轴对齐方式**
* **flex-wrap   是否换行**
* **align-self   子元素在交叉轴的对齐方式**

```markup
<!DOCTYPE html>
<html id="画骰子">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>画骰子</title>
        <style type="text/css">
            .box {
                width: 200px;
                height: 200px;
                margin: 20px;
                padding: 20px;
                border: 2px solid #ccc;
                border-radius: 10px;

                display: flex;
                justify-content: space-between;

            }
            .item {
                width: 40px;
                height: 40px;
                border-radius: 50%;
                background-color: #666;
            }
            .item:nth-child(2) {
                align-self: center;
            }
            .item:nth-child(3) {
                align-self: flex-end;
            }
        </style>
    </head>
    <body>
        <div class="box">
            <div class="item"></div>
            <div class="item"></div>
            <div class="item"></div>
        </div>
    </body>
</html>
```

