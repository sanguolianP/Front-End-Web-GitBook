# HTTPS

## 1.HTTPS

起初是因为HTTP在传输数据时使用的是明文（虽然说POST提交的数据时放在报体里看不到的，但是还是可以通过抓包工具窃取到）是不安全的，为了解决这一隐患Netscape公司推出了SSL安全套接字协议层，SSL是基于HTTP之下TCP之上的一个协议层，是基于HTTP标准并对TCP传输数据时进行加密，所以HPPTS是HTTP+SSL/TCP的简称。

## 2.SSL：\( Secure Socket Layer, 安全套接字层 \)

位于可靠的面向连接的网络层协议和应用层协议之间的一种协议层。  
SSL通过互相认证、使用数字签名确保完整性、使用加密确保私密性，以实现客户端和服务器之间的安全通讯。该协议由两层组成：SSL记录协议和SSL握手协议。

## 3.TLS \( Transport Layer Security, 传输层安全协议 \)

安全传输层协议（TLS）用于在两个通信应用程序之间提供保密性和数据完整性  
该协议由两层组成： TLS 记录协议（TLS Record）和 TLS 握手协议（TLS Handshake）  
可以说TLS就是SSL的新版本

### 非对称加密原理

非对称加密算法是一种密钥的保密方法  
非对称加密算法需要两个密钥：公开密钥（publickey:简称公钥）和私有密钥（privatekey:简称私钥）。  
公钥与私钥是一对，如果用公钥对数据进行加密，只有用对应的私钥才能解密。  
因为加密和解密使用的是两个不同的密钥，所以这种算法叫作非对称加密算法。

## 4.网络攻击

### XSS\(Cross Site Script, 跨站脚本攻击\)

XSS又叫CSS（Cross Site Script），跨站脚本攻击：攻击者在目标网站植入恶意脚本（js / html），用户在浏览器上运行时可以获取用户敏感信息（cookie / session）、修改web页面以欺骗用户、与其他漏洞相结合形成蠕虫等。  
**XSS类型**

* 持久型XSS：将脚本植入到服务器上，从而导致每个访问的用户都会执行  
* 非持久型XSS：对个体用户某url的参数进行攻击  

**解决方法：**  
对特殊字符进行转译就好了（vue/react等主流框架已经避免类似问题，vue举例：不能在template中写script标签，无法在js中通过ref或append等方式动态改变或添加script标签）

* 现代大部分浏览器都自带 XSS 筛选器，vue / react 等成熟框架也对 XSS 进行一些防护
* 对用户输入内容和服务端返回内容进行过滤和转译
* 重要内容加密传输
* 合理使用get/post等请求方式
* 对于URL携带参数谨慎使用

### CSRF/XSRF\(Cross Site Request Forgery, 跨站请求伪造\)

攻击者盗用了你的身份，以你的名义发送恶意请求，对服务器来说这个请求是完全合法的，但是却完成了攻击者所期望的一个操作，比如以你的名义发送邮件、发消息，盗取你的账号，添加系统管理员，甚至于购买商品、虚拟货币转账等。

> 阐述 CSRF 攻击思想：（核心2和3）  
> 1.浏览并登录信任网站（举例：淘宝）  
> 2.登录成功后在浏览器产生信息存储（举例：cookie）  
> 3.用户在没有登出淘宝的情况下，访问危险网站  
> 4.危险网站中存在恶意代码，代码为发送一个恶意请求（举例：购买商品/余额转账）  
> 5.携带刚刚在浏览器产生的信息进行恶意请求  
> 6.淘宝验证请求为合法请求（区分不出是否是该用户发送）  
> 7.达到了恶意目标

**解决方法：**

* 请求地址添加 token ，使黑客无法伪造用户请求
* HTTP 头自定义属性验证（类似token）
* 涉及到数据修改操作严格使用 post 请求而不是 get 请求
* HTTP 协议中使用 Referer 属性来确定请求来源进行过滤（禁止外域）
* 显示验证方式：添加验证码、密码等  

**token机制**  
1.Token的引入  
Token是在客户端频繁向服务端请求数据，服务端频繁的去数据库查询用户名和密码并进行对比，判断用户名和密码正确与否，并作出相应提示，在这样的背景下，Token便应运而生。  
2.Token的定义  
Token是服务端生成的一串字符串，以作客户端进行请求的一个令牌，当第一次登录后，服务器生成一个Token便将此Token返回给客户端，以后客户端只需带上这个Token前来请求数据即可，无需再次带上用户名和密码。  
3.使用Token的目的  
Token的目的是为了减轻服务器的压力，减少频繁的查询数据库，使服务器更加健壮。  
4.token的使用方式

* 用设备号/设备mac地址作为Token（推荐）  
* 用session值作为Token  

### iframe

有些时候我们的前端页面需要用到第三方提供的页面组件，通常会以iframe的方式引入。典型的例子是使用iframe在页面上添加第三方提供的广告、天气预报、社交分享插件等等。  
因为iframe中的内容是由第三方来提供的，默认情况下他们不受我们的控制，他们可以在iframe中运行JavaScirpt脚本、Flash插件、弹出对话框等等，这可能会破坏前端用户体验。  
iframe中的域名可能因为过期而被恶意攻击者抢注，或者第三方被黑客攻破，iframe中的内容被替换掉了，从而利用用户浏览器中的安全漏洞下载安装木马、恶意勒索软件等等。

**解决方法：**  
1.如何让自己的网站不被其他网站的 iframe 引用？

```javascript
// 检测当前网站是否被第三方iframe引用
// 若相等证明没有被第三方引用，若不等证明被第三方引用。当发现被引用时强制跳转百度。
if(top.location != self.location){
    top.location.href = 'http://www.baidu.com'
}
```

2.如何禁用，被使用的 iframe 对当前网站某些操作？  
sandbox是html5的新属性，主要是提高iframe安全系数。iframe因安全问题而臭名昭著，这主要是因为iframe常被用于嵌入到第三方中，然后执行某些恶意操作。 现在有一场景：我的网站需要 iframe 引用某网站，但是不想被该网站操作DOM、不想加载某些js（广告、弹框等）、当前窗口被强行跳转链接等，我们可以设置 sandbox 属性。如使用多项用空格分隔。

> allow-same-origin：允许被视为同源，即可操作父级DOM或cookie等  
> allow-top-navigation：允许当前iframe的引用网页通过url跳转链接或加载  
> allow-forms：允许表单提交  
> allow-scripts：允许执行脚本文件  
> allow-popups：允许浏览器打开新窗口进行跳转  
> ""：设置为空时上面所有允许全部禁止

### opener

如果在项目中需要 打开新标签 进行跳转一般会有两种方式

```javascript
<a target='_blank' href='http://www.baidu.com'> // HTML
window.open('http://www.baidu.com') //JS
```

这两种方式看起来没有问题，但是存在漏洞。  
通过这两种方式打开的页面可以使用 window.opener 来访问源页面的 window 对象。  
场景：A 页面通过 `<a>` 或 window.open 方式，打开 B 页面。但是 B 页面存在恶意代码如下：

```javascript
 window.opener.location.replace('https://www.baidu.com') //此代码仅针对打开新标签有效
```

此时，用户正在浏览新标签页，但是原来网站的标签页已经被导航到了百度页面。  
恶意网站可以伪造一个足以欺骗用户的页面，使得进行恶意破坏。  
即使在跨域状态下 opener 仍可以调用 location.replace 方法。

**解决方法**  
1.通过 rel 属性进行控制

```markup
<a target="_blank" href="" rel="noopener noreferrer nofollow">a标签跳转url</a>
```

noopener：会将 window.opener 置空，从而源标签页不会进行跳转（存在浏览器兼容问题）  
noreferrer：兼容老浏览器/火狐。禁用HTTP头部Referer属性（后端方式）。  
nofollow：SEO权重优化，详情见 [https://blog.csdn.net/qq\_33981438/article/details/80909881](https://blog.csdn.net/qq_33981438/article/details/80909881)

2.设置window.open参数

```javascript
<button onclick='openurl("http://www.baidu.com")'>click跳转</button>

function openurl(url) {
    var newTab = window.open();
    newTab.opener = null;
    newTab.location = url;
}
```

### ClickJacking\(点击劫持\)

ClickJacking 翻译过来被称为点击劫持。一般会利用透明 iframe 覆盖原网页诱导用户进行某些操作达成目的。  
**解决方法**  
1.在HTTP投中加入 X-FRAME-OPTIONS 属性，此属性控制页面是否可被嵌入 frame 中  
【DENY：不能被所有网站嵌套或加载；SAMEORIGIN：只能被同域网站嵌套或加载；ALLOW-FROM URL：可以被指定网站嵌套或加载。】  
2.判断当前网页是否被 iframe 嵌套（详情在第一条 firame 中）

### HSTS\(HTTP Strict Transport Security, HTTP严格传输安全\)

网站接受从 HTTP 请求跳转到 HTTPS 请求的做法，例如我们输入`http://www.baidu.com`或`www.baidu.com`最终都会被302重定向到`https://www.baidu.com`。  
这就存在安全风险，当我们第一次通过 HTTP 或域名进行访问时，302重定向有可能会被劫持，篡改成一个恶意或钓鱼网站。  
HSTS：通知浏览器此网站禁止使用 HTTP 方式加载，浏览器应该自动把所有尝试使用 HTTP 的请求自动替换为 HTTPS 进行请求。用户首次访问时并不受 HSTS 保护，因为第一次还未形成链接。我们可以通过 浏览器预置HSTS域名列表 或 将HSTS信息加入到域名系统记录中，来解决第一次访问的问题。

### CND劫持

出于性能考虑，前端应用通常会把一些静态资源存放到CDN（Content Delivery Networks）上面，例如 js 脚本和 style 文件。这么做可以显著提高前端应用的访问速度，但与此同时却也隐含了一个新的安全风险。如果攻击者劫持了CDN，或者对CDN中的资源进行了污染，攻击者可以肆意篡改我们的前端页面，对用户实施攻击。  
现在的CDN以支持SRI为荣，script 和 link 标签有了新的属性 integrity，这个属性是为了防止校验资源完整性来判断是否被篡改。它通过 验证获取文件的哈希值是否和你提供的哈希值一样来判断资源是否被篡改。  
使用 SRI 需要两个条件：一是要保证 资源同域 或开启跨域，二是在`<script>`中 提供签名 以供校验。

