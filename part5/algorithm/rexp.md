# 正则匹配

### 1. 创建正则对象

```text
var patt=new RegExp(pattern,modifiers)

// 或更简单的方法
var patt = /pattern/modifiers;
```

### 2. 选项

```text
// 例如
(/pattern/modifiers) => (/pattren/ig)
```

| 选项 | 含义 | 描述 |
| :--- | :--- | :--- |
| i | ignore - 不区分大小写 | 将匹配设置为不区分大小写，搜索时不区分大小写: A 和 a 没有区别。 |
| g | global - 全局匹配 | 查找所有的匹配项。\(只匹配第一行\) |
| m | more - 多行匹配 | 使边界字符 ^ 和 $ 匹配每一行的开头和结尾，记住是多行，而不是整个字符串的开头和结尾。 |
| s | 特殊字符圆点 . 中包含换行符 \n | 默认情况下的圆点 . 是 匹配除换行符 \n 之外的任何字符，加上 s 修饰符之后, . 中包含换行符 \n。 |

### 3. 正则特性

[正则表达式元字符对照表](https://www.runoob.com/regexp/regexp-metachar.html)

#### 转义

| 字符 | 描述 |
| :--- | :--- |
| . |  匹配除换行符（\n、\r）之外的任何单个字符。要匹配包括 '\n' 在内的任何字符，请使用像"**\(.\|\n\)**"的模式 |
| \s | 匹配任何空白字符，包括空格、制表符、换页符等等。等价于 \[ \f\n\r\t\v\]。 |
| \d | 匹配一个数字字符。等价于 \[0-9\] |
| \w | 匹配字母、数字、下划线。等价于'\[A-Za-z0-9\_\]' |
| \n | 匹配一个换行符。等价于 \x0a 和 \cJ |
| \t | 匹配一个制表符。等价于 \x09 和 \cI |
| \. | 匹配 . |
| \r | 匹配一个回车符。等价于 \x0d 和 \cM |
| \b | 匹配一个单词边界，也就是指单词和空格间的位置。例如， 'er\b' 可以匹配"never" 中的 'er'，但不能匹配 "verb" 中的 'er' |

注意大写的表示匹配非，例如：\D匹配非数字字符。等价于\[^0-9\]。\W匹配非字母、数字、下划线。等价于 \[^A-Za-z0-9\_\]。

#### 量词

| 字符 | 描述 |
| :--- | :--- |
| {n,m} | m 和 n 均为非负整数，其中n &lt;= m。最少匹配 n 次且最多匹配 m 次。例如，"o{1,3}" 将匹配 "fooooood" 中的前三个 o。'o{0,1}' 等价于 'o?'。请注意在逗号和两个数之间不能有空格。 |
| {n} | n 是一个非负整数。匹配确定的 n 次。例如，'o{2}' 不能匹配 "Bob" 中的 'o'，但是能匹配 "food" 中的两个 o。 |
| {n,} | n 是一个非负整数。至少匹配n 次。例如，'o{2,}' 不能匹配 "Bob" 中的 'o'，但能匹配 "foooood" 中的所有 o。'o{1,}' 等价于 'o+'。'o{0,}' 则等价于 'o\*'。 |
| + | {1,} 匹配前面的子表达式一次或多次 |
| ？ | {0,1} 匹配前面的子表达式零次或一次 |
| \* | {0,} 匹配前面的子表达式零次或多次 |

#### 范围

| 字符 | 描述 |
| :--- | :--- |
| \[xyz\] | 字符集合。匹配所包含的任意一个字符。例如， '\[abc\]' 可以匹配 "plain" 中的 'a'。 |
| \[a-z\] | 字符范围。匹配指定范围内的任意字符。例如，'\[a-z\]' 可以匹配 'a' 到 'z' 范围内的任意小写字母字符。 |

#### 修饰

| 字符 | 描述 |
| :--- | :--- |
| ^ | 匹配输入字符串的开始位置。如果设置了 RegExp 对象的 Multiline 属性，^ 也匹配 '\n' 或 '\r' 之后的位置。 |
| $ | 匹配输入字符串的结束位置。如果设置了RegExp 对象的 Multiline 属性，$ 也匹配 '\n' 或 '\r' 之前的位置。 |

### 4. 常用正则方法

#### test\(\)

test\(\)方法搜索字符串指定的值，根据结果并返回真或假。

```text
var patt1=new RegExp("e")
document.write(patt1.test("The best things in life are free"))
// true
```

```text
<script>
var str = 'runoob';
var patt1 = new RegExp('\\w', 'g'); // 有转义作为正则表达式处理
var patt3 =/\w+/g;  // 与 patt1 效果相同
document.write(patt1.test(str)) //输出 true
document.write(patt3.test(str)) //输出 true
</script>
```

#### exec\(\)

exec\(\) 方法检索字符串中的指定值。返回值是被找到的值。如果没有发现匹配，则返回 null。

```text
var patt1=new RegExp("e");
document.write(patt1.exec("The best things in life are free"));
```

### 5. JS 常用正则函数

#### split\(\)

```text
string.split(separator,limit)
```

| 参数 | 描述 |
| :--- | :--- |
|  _separator_ | 可选。字符串或正则表达式，从该参数指定的地方分割 string Object。 |
|  _limit_ | 可选。该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度。 |
| 返回值 | Array。一个字符串数组。该数组是通过在 separator 指定的边界处将字符串 string Object 分割成子串创建的。返回的数组中的字串不包括 separator 自身。 |

#### replace\(\)

```text
string.replace(searchvalue,newvalue)
```

| 参数 | 描述 |
| :--- | :--- |
|  _searchvalue_ | 必须。规定子字符串或要替换的模式的 RegExp 对象。 请注意，如果该值是一个字符串，则将它作为要检索的直接量文本模式，而不是首先被转换为 RegExp 对象。 |
|  _newvalue_ | 必需。一个字符串值。规定了替换文本或生成替换文本的函数。 |
| 返回值 | String。一个新的字符串，是用 replacement 替换了 regexp 的第一次匹配或所有匹配之后得到的。 |

#### match\(\)

```text
string.match(regexp)

var str="The rain in SPAIN stays mainly in the plain"; 
var n=str.match(/ain/g);

// n是个数组 [ain,ain,ain]
```

#### search\(\)

```text
var str="Visit Runoob!"; 
var n=str.search("Runoob");

// n为6，查找并返回第一个匹配到的索引值
// 如果没有找到任何匹配的子串，则返回 -1。
```

### 6. 常见正则应用

#### 敏感词过滤

```text
replace(正则, function (str) { 
  // 对 str(匹配到的东西) 进行处理
  return 替换成的东西 
})
```

#### 座机校验 \(**0311-1234567**\)

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x533A;&#x53F7;</th>
      <th style="text-align:left">&#x7535;&#x8BDD;&#x53F7;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>&#x7B2C;&#x4E00;&#x4F4D; &#x5FC5;&#x987B;&#x662F;0</p>
        <p>&#x7B2C;&#x4E8C;&#x4F4D; &#x4E0D;&#x80FD;&#x662F;0</p>
        <p>&#x5171;3-4&#x4F4D; &#x540E;&#x9762;&#x4E0D;&#x4F5C;&#x8981;&#x6C42;</p>
      </td>
      <td style="text-align:left">
        <p>&#x7B2C;&#x4E00;&#x4F4D;&#x4E0D;&#x80FD;&#x662F;0</p>
        <p>&#x540E;&#x9762;&#x968F;&#x610F;&#xFF0C;&#x5171;7&#x5230;8&#x4F4D;</p>
      </td>
    </tr>
  </tbody>
</table>

```text
let re = /^0[1-9]\d{1,2}-[1-9]\d{6,7}/
re.test(0311-132165488) //正确返回true，错误返回false
```



#### 邮箱校验

前缀部分 

> * 纯数字 123456@qq.com
> * 纯字母 ewqrer@qq.com 
> * 字母数字混合 12erq56@qq.com 
> * 带点的 1qr.e4@qq.com 
> * 带下划线 12\_e256@qq.com
> * 带连接线 12-dwq56@qq.com
> * 123465@vip.qq.com

```text
/^[0-9A-Za-z\.\_\-]+@[0-9A-Za-z\-]+(\.[a-zA-Z]+){1,2}$/
```



剑指offer题目： 请实现一个函数用来判断字符串是否表示数值（包括整数和小数）。例如，字符串“+100”、“5e2”、“-123”、 “3.1416”及“-1E-16”都表示数值，但“12e”、“1a3.14”、“1.2.3”、“+-5”及“12e+5.4”都不是。

