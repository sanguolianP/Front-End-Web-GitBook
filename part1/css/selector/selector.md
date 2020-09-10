# 优先级策略

## 选择器

| 行内样式 |  | class |
| :---: | :---: | :---: |
| 通配符 |  | \* |
| 标签选择器 |  | p\(标签名\) |
| 类选择器 |  | . |
| id选择器 |  | \# |
| 属性选择器 |  | \*\[title="aaa"\]{} |
| 组合选择器 |  | 如下 |
| 后代 |  | .main h2{} |
| 儿子 |  | .main&gt;h2{} |
| 相邻兄弟 |  | h2+p{} |
| 无需紧邻兄弟 |  | h2~p{} |

## 优先级策略

**选择器权重**

| 行内样式 | id | class | 标签 | \*通配符 |
| :---: | :---: | :---: | :---: | :---: |
| 1000 | 100 | 10 | 1 | 0 |

组合选择器权重数值相加比较

## 伪类/伪元素

正确的利用伪元素和伪类能够让我们的html结构更清晰合理，也能在一定程度上减少js对dom的操作。  
伪类包含两种：状态伪类和结构性伪类。

**状态伪类**是基于元素当前状态进行选择的。在与用户的交互过程中元素的状态是动态变化的，因此该元素会根据其状态呈现不同的样式。当元素处于某状态时会呈现该样式，而进入另一状态后，该样式也会失去。常见的状态伪类主要包括：

* :link 应用于未被访问过的链接
* :hover 应用于鼠标悬停到的元素
* :active 应用于被激活的元素
* :visited 应用于被访问过的链接，与:link互斥
* :focus 应用于拥有键盘输入焦点的元素

**结构性伪类**是css3新增选择器，利用dom树进行元素过滤，通过文档结构的互相关系来匹配元素，能够减少class和id属性的定义，使文档结构更简洁。常见的包括：

* :first-child 选择某个元素的第一个子元素
* :last-child 选择某个元素的最后一个子元素
* :nth-child\(\) 选择某个元素的一个或多个特定的子元素
* :nth-last-child\(\) 选择某个元素的一个或多个特定的子元素，从这个元素的最后一个子元素开始算
* :nth-of-type\(\) 选择指定的元素
* :nth-last-of-type\(\) 选择指定的元素，从元素的最后一个开始计算
* :first-of-type 选择一个上级元素下的第一个同类子元素
* :last-of-type 选择一个上级元素的最后一个同类子元素
* :only-child 选择的元素是它的父元素的唯一一个子元素
* :only-of-type 选择一个元素是它的上级元素的唯一一个相同类型的子元素
* :empty 选择的元素里面没有任何内容

**伪元素**是对元素中的特定内容进行操作，而不是描述状态。它的操作层次比伪类更深一层，因此动态性比伪类低很多。实际上，伪元素就是选取某些元素前面或后面这种普通选择器无法完成的工作。控制的内容和元素是相同的，但它本身是基于元素的抽象，并不存在于文档结构中！常见的伪元素选择器包括：

* :first-letter 选择元素文本的第一个字（母）
* :first-line 选择元素文本的第一行
* :before 在元素内容的最前面添加新内容
* :after 在元素内容的最后面添加新内容

有时你会发现伪类元素使用了两个冒号 \(::\) 而不是一个冒号 \(:\)，这是 CSS3 规范中的一部分要求，目的是为了区分伪类和伪元素，大多数浏览器都支持这两种表示方式。单冒号\(:\)用于 CSS3 伪类，双冒号\(::\)用于 CSS3 伪元素。对于 CSS2 中已经有的伪元素，例如 :before，单冒号和双冒号的写法 ::before 作用是一样的。

所以，如果你的网站只需要兼容 webkit、firefox、opera 等浏览器，建议对于伪元素采用双冒号的写法，如果不得不兼容 IE 浏览器，还是用 CSS2 的单冒号写法比较安全。

**伪类的应用**

* 清除浮动  

  ```css
  .clear:after {
    content: '';
    display: block;
    clear: both;
  }
  ```

* 画分割线  

  ```css
  <style>
    * {
      padding: 0;
      margin: 0;
    }
    .spliter::before, .spliter::after {
      content: '';
      display: inline-block;
      border-top: 1px solid black;
      width: 200px;
      margin: 5px;
    }
  </style>
  </head>
  <body>
  <p class="spliter">分割线</p>
  </body>
  ```

* 计数器

  ```css
  <style>
    .chooses {
      counter-reset: letters;
    }
    .chooses input:checked {
      counter-increment: letters;
    }

    .choose span:after {
      content: counter(letters);
    }
  </style>
  </head>
  <body>
  <div class="chooses">
    <input type="checkbox">a
    <input type="checkbox">b
    <input type="checkbox">c
    <input type="checkbox">d
    <input type="checkbox">e
    <input type="checkbox">f
    <input type="checkbox">g
    <input type="checkbox">h
    <input type="checkbox">i
    <input type="checkbox">j
  </div>
  <p class="choose">我选择了<span></span>个字母</p>
  </body>
  ```

* 形变  

  ```css
  .transform{
      position: absolute;
      top:50%;
      left: 50%;
      transform:translate(-50%,-50%);
      width: 160px;
      padding: 60px;
      text-align: center;
      color: white;
      font-size: 200%;
    }
    .transform::before{
      content:"";
      position: absolute;
      top: 0; right: 0; bottom: 0; left: 0;
      transform:perspective(40px) scaleY(1.3) rotateX(5deg);
      transform-origin: bottom;
      background:rgb(255, 145, 20);
      z-index:-1;
    }
  ```

* 增大点击热区  

  ```css
  .btn::before {
      content:"";
      position:absolute;
      top:-10px;
      right:-10px;
      bottom:-10px;
      left:-10px;
    }
  ```

