# 定位

## 1. absolute 和 relative 分别依据什么定位？

* **relative 依据自身定位**
* **absolute 依据最近一层的已定位元素定位**
  * **已定位元素包括**
    * **absolute / relative / fixed**
    * **body**

## 2. 居中对齐有哪些实现方式？

### 水平居中

| 情况 | 方法 |
| :--- | :--- |
| inline 元素 | 父元素设置 text-align: center |
| block 元素 | margin: auto |
| absolute 元素 | left: 50%  +  margin-left 负值 |

### 垂直居中

| 情况 | 方法 |
| :--- | :--- |
| inline 元素 | 设置 line-height = height |
| block 元素 | block 元素垂直居中必须设置absolute |
| absolute 元素 | top: 50%  +  margin-top 负值 |

### 未知宽高

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x60C5;&#x51B5;</th>
      <th style="text-align:left">&#x65B9;&#x6CD5;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">absolute &#x5143;&#x7D20;</td>
      <td style="text-align:left">
        <p>transform: translateX(-50%) &#x6C34;&#x5E73;
          <br />transform: translateY(-50%) &#x5782;&#x76F4;&#x65B9;&#x5411;</p>
        <p>transform: translate(-50%, -50%) &#x4E24;&#x4E2A;&#x65B9;&#x5411;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">absolute &#x5143;&#x7D20;</td>
      <td style="text-align:left">top, left, right, bottom=0 + margin:auto</td>
    </tr>
  </tbody>
</table>



|  |
| :--- |


