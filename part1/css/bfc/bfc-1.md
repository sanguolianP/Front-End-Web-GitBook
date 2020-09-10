# margin合并与塌陷

BFC \(Block formatting context\) 块级格式化上下文  
根据W3C的标准，在页面中元素都一个隐含的属性叫做Block Formatting Context 简称BFC，该属性可以设置打开或者关闭，默认是关闭的。  
当开启元素的BFC以后，元素将会具有如下的特性：

* 父元素的垂直外边距不会和子元素重叠
* 开启BFC的元素不会被浮动元素所覆盖
* 开启BFC的元素可以包含浮动的子元素

**如何开启BFC**  
1.将overflow设置为hidden是副作用最小的开启BFC的方式。

> overflow: hidden;

但是在IE6及以下的浏览器中并不支持BFC，所以使用这种方式不能兼容IE6。在IE6中虽然没有BFC，但是具有另一个隐含的属性叫做hasLayout，属性的作用和BFC类似  
直接将元素的zoom设置为1即可

* zoom表示放大的意思，后边跟着一个数值，写几就将元素放大几倍
* zoom:1表示不放大元素，但是通过该样式可以开启hasLayout
* zoom这个样式，只在IE中支持，其他浏览器都不支持

所以最终兼容性方案

```css
.clearfix{
      overflow: hidden; 
      zoom:1;
  }
```

2.通过在高度塌陷的父元素的最后，添加一个空白的div,然后在对其进行清除浮动,但会在页面中添加多余结构

```css
.clearfix{
    clear: both;
}
```

通过after伪类在高度塌陷的父元素的最后,添加一个空白的块元素，然后对其清除浮动，不会再页面中添加多余结构

```css
.clearfix{
    zoom:1;
}
.clearfix:after{
    // 添加一个内容
    content: "";
    // 转换为一个块元素
    display: block;
    // 清除两侧的浮动
    clear: both;
}
```

子元素和父元素相邻的垂直外边距会发生重叠，子元素的外边距会传递给父元素,使用空的table标签可以隔离父子元素的外边距，阻止外边距的重叠

```css
.clearfix{
    zoom: 1;
}
.clearfix:before,
.clearfix:after{
    content: "";
    display: table;
    clear: both;
}
```

## 高度塌陷

在文档流中，父元素的高度默认是被子元素撑开的，也就是子元素多高，父元素就多高。但是当为子元素设置浮动以后，子元素会完全脱离文档流，此时将会导致子元素无法撑起父元素的高度，导致父元素的高度塌陷。由于父元素的高度塌陷了，则父元素下的所有元素都会向上移动，这样将会导致页面布局混乱。

**开启BFC即可解决高度塌陷问题**  
一般设置 overflow: hidden 即可

## margin合并与塌陷

**margin合并**  
块元素的上外边距和下外边距有时会合并为一个外边距，其大小取其中的最大者  
称为外边距折叠\(合并\)  
解决margin合并

* 使用padding  
* 设置定位或者浮动  内层元素绝对定位 position: absolute或float  
* 改变盒子模型  display:inline-block  

**margin塌陷**  
子元素设置margin父元素也被margin了  
解决margin塌陷

* 父元素设置 overflow: hidden  
* 设置定位或者浮动  内层元素绝对定位 position: absolute或float  
* 改变盒子模型  display:inline-block  

## 元素水平垂直居中

| 元素居中 | 水平居中 | 垂直居中 |
| :---: | :---: | :---: |
| 文本居中 | 父元素添加 text-align: center | 父元素的行高等于父元素\(容器\)高度 |
| div居中 | 自身添加  margin: 0 auto | 设置左上各50%    再将margin设为自身宽高一半的负值 |
| 图片居中1 | 父元素添加 text-align: center | 父元素添加     display: table-cell    vertical-align: middle |
| 图片居中2 | 父元素text-align: center | lineheight==height   图片vertical-align: middle |

## float以及清除float

css的浮动float，会使元素向左或者向右移动，其周围的元素也会重新排列

浮动的作用

* 实现排版布局
* 行内元素都会支持宽高
* 所有元素都会支持宽高

特点

* 脱离文档流
* 浮动有方向
* 块元素宽度尽可能的窄\(不加flaot块元素会独占一行\)
* 行内元素会变成块元素\(支持宽高\)
* 宽度不够会掉下来\(ul里包含多个li，ul宽度不够li会被挤下去\)  

清除浮动  
overflow: hidden 加给父级 不适合内容超出

clear: both 同级元素 最后添加空标签

clearFix: after 加给父级的class适用于各种情况

```css
//伪元素方法(推荐)
clearFix:after{
content: ''
display: block
clear: both
}
clearFix{
zoom: 1
}//兼容IE 6 7
```

浮动三要素

* 同级元素都要加float  
* 用到浮动的时候必须要清除浮动  
* 浮动后最好给宽度  

## position 嵌套 & 覆盖

定位的四种方式

> position: relative/absolute/fixed/static

1.relative

* 相对于自己应该在的位置定位
* 不脱离文档流\(依然占着网页里实际的位置\)
* 不会改变元素的类型
* 设置relative时，不能再同时设置左右或者上下，只能设置四个角  

2.absolute

* 根据父级定位，如果父级没有定位则根据上一个已定位的父级定位
* 完全脱离文档流\(文档流无视div的存在\)
* 会让块元素宽度尽可能的窄
* 行内元素\(span\)变成块元素  

3.fixed

* 固定定位，根据可视区定位
* 脱离文档流
* 会让块元素宽度尽可能的窄   
* 行内元素\(span\)变成块元素

4.static

* 默认值。通常是在覆盖absolute或者relative样式时使用。

