# 响应式 

## 响应式布局概念  
Responsive design，意在实现不同屏幕分辨率的终端上浏览网页的不同展示方式。  
通过响应式设计能使网站在手机和平板电脑上有更好的浏览阅读体验。  

**优势**  
* 一个页面适应各种显示屏  
* 具有良好的SEO  
* 较大缩短开发周期  
* 给用户更多的选择，更好的用户体验  

## 响应式知识点
1.**流体网格**  
一个简单的网格系统，将每个格子使用百分比单位来控制网格大小，其优势是网格随着屏幕大小作出对于的比例缩放。  

2.**弹性图片**  
弹性图片是指不给图片设置固定尺寸，而更具流体网格进行缩放来适应不同的尺寸。  
```css
    img{
        max-width:100%;
    }
```
注：IE8中会使图片不显示，所以需在IE8中增加对于hack样式。  

3.**CSS3 Media Queries**  
它是响应式设计最关键的一个应用，它可以根据浏览器窗口的大小、方向、屏幕规格选择对于的样式文件。  

4.**主要断点**  
断点是为min-width和max-width服务的。@media (min-width:320px){}

5.**自适应布局盒响应式布局区别**  
自适应布局：就是我们常见的百分比布局，它可以让你的布局在不同分辨率下适应其大小，但这种布局需要一个最小宽度来辅助实现，不然在一定尺寸下，整个布局会乱掉，只不过这种不固定值是%而不是px。  
响应式布局：是一个多列流体布局，其利用的是媒体查询来实现web页面在不同分辨率下的完美呈现，和自适应布局还是有本质上的差别。  

6.**常用css单位**  
常用有三种：px em %  
* px：浏览器的度量单位，相对于物理像素，1px在高清屏幕下可能占用2个物理像素、甚至3个物理像素。  
* em：相对于父元素的font-size，如父元素font-size设置为16px，子元素font-size设置为0.75em，那么转换为px就是0.75 * 16px = 12px;  
* %：相对于父元素的长度高度，position:fixed 、absolute 除外（fixed将相对于窗口、absolute相对于递归父元素知道 第一个设置了position的元素）  
* rem：相对于根节点(一般为html节点)的font-size，如果html节点设置font-size = 100px，那么文档中的元素设置为0.3rem，则计算为：0.3 * 100px = 30px  
* vh/vw：相对于设备的可视范围，在移动端中经常会用到，比如：设计师经常要求，banner占满首屏高度既：100vh。如iphone6 （375px * 677px）= (100vw * 100vh) ，而iphone6 plus （414px * 736px） = (100vw * 100vh) 两种屏幕下的vw、vh是不一样的。  
* clac：css3中的长度计算语法，支持+、-、*、/的计算。  


## 响应式的设计步骤  
1.设置meta标签  

大多数移动浏览器将HTML页面放大为宽的视图（viewport）以符合屏幕分辨率。可以使用视图的meta标签来进行重置。下面的视图标签告诉浏览器，使用设备的宽度作为视图宽度并禁止初始的缩放。在`<head>`标签里加入这个meta标签。
```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
```
user-scalable = no 属性能够解决 iPad 切换横屏之后触摸才能回到具体尺寸的问题。  


第三步、媒体查询  
1、一般用min-width和max-width来检查各种设备的分辨率大小  
@media screen and (min-width : 768px) {}  
@media screen and (max-width : 1024px) {}  
@media screen and (min-width : 768px)  and (max-width : 1024px) {}  

2、设备宽度device-width主要用在苹果产品上  
@media screen and (min-device-width : 768px)  and (max-device-width : 1024px) {}  

3、调用独立样式表   
常用模板：  
>1024px显示屏：@media screen and (max-width : 1024px) {}  
ipad横屏：@media screen and (max-device-width : 1024px) and (orientation:landscape) {}  
ipad竖屏：@media screen and (max-device-width : 768px) and (orientation:portrait) {}  
iphone和smartPhone:@media screen and (min-width : 320px)  and (max-width : 480px) {}  

大屏幕、中屏幕、小屏幕的划分：  
>小屏幕：<769px；@media only screen and (min-width : 769px) {}  
中屏幕：769~1366px或者769~1440px；@media only screen and (min-width : 769px) and (max-width:1366px){}  
大屏幕：1366~1920px；@media only screen and (min-width : 1367px) {}  


**响应式布局的成型方案**  
现在的css，UI框架等都已经考虑到了适配不同屏幕分辨率的问题，实际项目中我们可以直接使用这些新特性和框架来实现响应式布局。可以有以下选择方案：    
* 利用上面的方法自己来实现，比如CSS3 Media Query,rem，vw等  
* Flex弹性布局，兼容性较差  
* Grid网格布局，兼容性较差  
* Columns栅格系统，往往需要依赖某个UI库，如Bootstrap  

**响应式布局的要点**  
在实际项目中，我们可能需要综合上面的方案，比如用rem来做字体的适配，用srcset来做图片的响应式，宽度可以用rem，flex，栅格系统等来实现响应式，然后可能还需要利用媒体查询来作为响应式布局的基础，因此综合上面的实现方案，项目中实现响应式布局需要注意下面几点：  
* 设置viewport
* 媒体查询
* 字体的适配（字体单位）
* 百分比布局
* 图片的适配（图片的响应式）
* 结合flex，grid，BFC，栅格系统等已经成型的方案












