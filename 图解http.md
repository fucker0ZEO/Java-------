# 本书可做入门也可以作为工具书

# <补充>: 流程图比文字容易理解很多！！！（很多文字表述最后自己理解还是会变成流程图来消化）

# 在安全领域，三个关键点：窃听，伪装，篡改

# 每一种旧机制/方案，被代替都要清楚是为什么？ 例如HTTP缓存控制（过期）和缓存验证（失效）

**时间超过叫过期，值/内容改变则是失效**

****





****

新进入某一个领域，或者说是看这个领域的学习资料时，例如看某本书。可以**参考其他人写的笔记**，通过粗览他们的学习笔记，可以明白哪些是重点，哪些是非重点;可以**参考非API部分的笔记该怎么处理**，可以**参考API*部分该如何学习*

这是CYC2018这位大佬写的目录

- 一 、基础概念
  - [URI](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#uri)
  - [请求和响应报文](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#请求和响应报文)
- 二、HTTP 方法
  - [GET](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#get)
  - [HEAD](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#head)
  - [POST](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#post)
  - [PUT](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#put)
  - [PATCH](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#patch)
  - [DELETE](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#delete)
  - [OPTIONS](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#options)
  - [CONNECT](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#connect)
  - [TRACE](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#trace)
- 三、HTTP 状态码
  - [1XX 信息](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#1xx-信息)
  - [2XX 成功](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#2xx-成功)
  - [3XX 重定向](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#3xx-重定向)
  - [4XX 客户端错误](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#4xx-客户端错误)
  - [5XX 服务器错误](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#5xx-服务器错误)
- 四、HTTP 首部
  - [通用首部字段](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#通用首部字段)
  - [请求首部字段](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#请求首部字段)
  - [响应首部字段](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#响应首部字段)
  - [实体首部字段](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#实体首部字段)
- 五、具体应用
  - [连接管理](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#连接管理)
  - [Cookie](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#cookie)
  - [缓存](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#缓存)
  - [内容协商](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#内容协商)
  - [内容编码](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#内容编码)
  - [范围请求](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#范围请求)
  - [分块传输编码](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#分块传输编码)
  - [多部分对象集合](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#多部分对象集合)
  - [虚拟主机](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#虚拟主机)
  - [通信数据转发](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#通信数据转发)
- 六、HTTPS
  - [加密](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#加密)
  - [认证](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#认证)
  - [完整性保护](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#完整性保护)
  - [HTTPS 的缺点](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#https-的缺点)
- 七、HTTP/2.0
  - [HTTP/1.x 缺陷](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#http1x-缺陷)
  - [二进制分帧层](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#二进制分帧层)
  - [服务端推送](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#服务端推送)
  - [首部压缩](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#首部压缩)
- [八、HTTP/1.1 新特性](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#八http11-新特性)
- 九、GET 和 POST 比较
  - [作用](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#作用)
  - [参数](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#参数)
  - [安全](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#安全)
  - [幂等性](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#幂等性)
  - [可缓存](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#可缓存)
  - [XMLHttpRequest](https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md#xmlhttprequest)



脱离了堆砌API的部分，就不用再缓慢的一次看一小段，然后对每一小段做笔记了。**这时的上下文之间开始有联系了**

****

**入门的部分确实讲的不错**，但是有些地方的翻译还是有点绕，需要念好几遍才能够理解。

**工具书部分**。。。emmmm，果然全天下的工具书都是一样让人昏昏欲睡（真的感觉回到某些课堂上，真的想睡觉），很消耗精力！！！

这本书的第6章就是工具书的部分，**强烈建议这个部分对着抓包来看，不然真的容易睡着的。。。字段和头部建议对着抓包得到的信息来看。**虽然这本书，在这里插图很多，**但是没有实操且少用的概念性的知识是非常难记住的，就和学API一样！！！总体上就是看着是 一堆散沙一样的知识！非常容易学着后面忘了前面，这样是最不易吸收的！！！**

124页，创建请求xx秒，客户端再发送请求？？？还是说客户端接收到服务器端的请求后XX秒，客户端再次发送请求！

API的部分还是啃的慢啊，啃了一天，20多页。要记的笔记太多了。。。不然就如浮沙筑高台！！！所谓的把薄书读厚应该就是这个意思吧。通过自己对浓缩过的干货知识用大量的笔记进行解读，薄书也就渐渐的厚起来了。相对的，再把厚书读薄，应该指的就是将知识进行浓缩！前面的厚，大部分都是自己为了便于理解和记忆加上去的脚手架，但是当自己已经能够完全理解其中的内容时，这些脚手架就没有多少意思，甚至能够超越作者的表述，认为作者的表达上面也不够精炼，自己有着更为精炼的理解。这就是又将厚书读薄



《图解HTTP》中的一些常见的单词，知道这些词的意思，**可以对首部字段，见名知意**

Accept :接收

Content:内容

etag:标签

location:位置

encoding：编码方式

headers: 标头

range: 范围



https://www.bilibili.com/blackboard/bnj2020.html?bsource=2020bnjdd&spm_id_from=333.999.b_696e7465726e6174696f6e616c486561646572.8&aid=78976165

****

# HTTP是什么？

经典问答：**HTTP是一个在计算机领域里专门在两点之间传输文字，图片，音频，视频等超文本数据的约定和规范**

*上面这段，熟读并背诵*







****

# 如何证明双方能够进行通信？

**HTTP协议的3次握手就是在证明双方是否都具备接受+发送信息的能力**

发送端-->发出包1

接收端-->接受包1，并发送包a【这里证明了发送端能够发包，以及接收端能够接受包】

发送端-->接受包a，并发送包2【这里证明能够接受端能够发包，以及发送端能够接受包】



# 状态码



## 302状态码--请求重定向

![](C:\Users\fucker\Pictures\http.1.PNG)



**我们可以看到General中的Request  URL：**

```http
Request URL:https://unpkg.zhimg.com/@cfe/sentry-script@latest/dist/init.js
```

它表示**发出请求时的URL**

而**Response Headers中的location：**

```http
location: /@cfe/sentry-script@0.0.10/dist/init.js
```

*它使用的是相对路径的格式，前面的使用/代替了*

**这个响应头表示的就是重定向的路径为：**

```http
https://unpkg.zhimg.com/@cfe/sentry-script@0.0.10/dist/init.js
```

****

## 504状态码

在《图解HTTP》一书中，多次出现504状态码，前文却没有具体介绍504状态码。

书中出现504状态码：

1.*发生请求缓存服务器的本地缓存无响应则返回504*

2.*代理服务器无法连接通源服务器再次获取有效资源，缓存必须给客户端返回504*

504代表着网关超时，**也就是说未能及时从上游服务器（URI标识的服务器，如：HTTP,FTP,LDAP）或者辅助服务器(例如DNS)收到响应**

****

## 502状态码

和504状态码类似，但却不同。

502代表着响应无效，**也就是说作为网关或者代理工作的服务器尝试执行请求时，从上游服务器接收到无效的响应**

****

## 412状态码

同样是在《图解HTTP》中，出现了多次

412**表示客户端没有满足请求信息的先决条件**

```http
412 precondition failed
```

常见于**对于含有条件的请求，如：If-Xxxx   做出的 响应**。**也就是客户端请求信息的先决条件错误，然后服务器端不接受请求，返回412**



## 304状态码

在抓包时，经常遇见，同时在《图解HTTP》中，出现了多次。**而且容易和302的请求重定向混淆**

如果客户端发送了一个带条件的GET 请求且该请求已被允许，而文档的内容（自上次访问以来或者根据请求的条件）并没有改变，则服务器应当返回这个304状态码。

简单的表达就是：**服务端已经执行了GET，但文件未变化**

当你发出一个GET请求的时候**服务器会从缓存中调用你要访问的内容**，这个时候服务器就可以**判断这个页面是不是更新过**了，如果**未更新过那么则会返回304状态码**。

****

## 307状态码

抓百度首页最开头就是307

****

##  405状态码

当服务器端接收到不支持的HTTP方法时，会以状态码405 Method Not Allowed作为响应返回。与此同时 ，还会吧所有能支持的HTTP方法写入首部字段Allow后返回

也就是说：

**当客户端以服务器端不支持的方式发请求给服务器端时，服务器端会返回405这个状态码以及所有能够支持的HTTP方法给客户端**



**说人话：表示请求的方式不对**

****

##  403 状态码

HTTP 403 状态码 表示**服务器理解请求客户端的请求，但是拒绝执行此请求**，一般是因为**目录权限问题导致禁止访问**

------

403 Forbidden

服务器已经理解请求，但是拒绝执行它。与401响应不同的是，身份验证并不能提供任何帮助，而且这个请求也不应该被重复提交。如果这不是一个 HEAD 请求，而且服务器希望能够讲清楚为何请求不能被执行，那么就应该在实体内描述拒绝的原因。当然服务器也可以返回一个404响应，假如它不希望让客户端获得任何信息。【[HTTP 401 状态码](http://www.php.cn/web/web-http401.html)】



****

## 401 状态码

需要认证身份

****



## 301 状态码

请求的资源已分配到新的URL中，URL地址改变了

****

## 303 状态码

与302相同功能，但明确客户端采用GET方式来获取资源

****

## 503 状态码

服务器繁忙



****





# 缓存的Cache-Control字段，特别是Expires和max-age的区别。ETag验证场景

## HTTP缓存

### 缓存是什么？

**缓存是指代理服务器或客户端本地内存或磁盘内保存的资源副本**，web缓存分为三类：**浏览器缓存（其中有一种机制是HTTP缓存），代理服务器缓存以及网关缓存**



**过期！=失效**

### 为什么要用缓存？

- **降低延迟**：缓存离客户端更近（例如浏览器缓存，它存在浏览器中），因此，从缓存请求内容比从源服务器所用时间更少。
- **缓解服务器压力**：副本被重复使用，减少了用户对服务器的访问



### 缓存是如何实现的？

- 让代理服务器进行缓存
- 让客户端浏览器进行缓存

### **缓存在本地的什么地方？**

从内存中读取数据

200（from memory cache）

从硬盘中读取数据

`200（from diks cache）`

然后它们的先后顺序是**先从内存读取**，再从**硬盘中读取**

它们都属于`200(from cache)`，都表示的是从缓存中取数据。



出现这种情况，则要关注Expires和Cache-control。也就是关注**缓存的验证和操作缓存的工作机制**

****

### 缓存控制--Cache-Control



HTTP/1.1 通过 Cache-Control 首部字段来控制缓存。

而Expires 是 HTTP 1.0 的东西，现在默认浏览器均默认使用 HTTP 1.1，所以它的作用小了很多。



**Cache-Control**这个头有多个指令参数可选，用，隔开。例如：

```
Cache-Control: private,max-age=0,no-cache
```

#### 禁止缓存

```
Cache-Control:no-store
```

no-strore指令规定**不得存储关于客户端请求和服务器端响应的任意内容**

#### 强制确认缓存

```
Cache-Control:no-cache
```

no-cache指令规定**缓存服务器收到客户端发出的此请求时:**

**每次在释放缓存副本之前都强制发送请求给源服务器进行验证是否过期，**{因为是验证，一般该请求还会带有和本地缓存相关的验证字段}



no-cache指令规定**缓存服务器收到源服务器返回的此响应时：**

**缓存服务器会向源服务器进行有效期确认后处理资源。**

****

#### **验证结果:**过期后验证是否失效！

**过期+失效 200**

**过期+未失效 304**

当浏览器通过 `Expires` 或者 `Cache-control` 判断出缓存已经过期，那么就需要重新发送请求到服务器，让服务器判断当前缓存**是否可以继续使用**。{这里是过期后，判断是否失效}

当服务器判断**该缓存已经失效，那么就会返回新数据**，HTTP **状态码为 200**；

*返回新数据，不是在缓存服务器上获取的，因此是200。如果是从缓存中获取的，就又被重定向到了缓存服务器，返回304*



当浏览器判断该缓存还未失效，那么就会返回 HTTP 状态码为 304 (无需包体，节省流量)，告知浏览器继续使用缓存。

****

#### **公有缓存和私有缓存**

```http
Cache-Control:private
Cache-Control:public
```

private英文为私有，public因为为公有。

public该指令参数**表示可以被任何人缓存，一般存储在代理服务器中**

private该指令参数表示**只能被单个用户使用，一般存储在用户浏览器中**



#### 缓存过期机制

##### Cache-Control:max-age   ---缓存时间   

mag-age指令出现在**源服务器返回的响应报文中**



```
Cache-Control: max-age=15811200
```

max-age指令表示**从该指令的值后多少秒就会重新请求新数据**，重新请求新数据时已经过期。**因此max-age的值算是过期时间**。**而过期时间内请求直接从缓存中读取数据，返回200(from cache)**。

这里的max-age值表示缓存时间，也就是说当**它请求成功后内都是有效的15811200秒**



mag-age指令出现在**客户端发送的请求报文中**

```
Cache-Control:max-age=604800
```

这里的max-age表示的是：指定的缓存时间数值

如果**所请求资源的缓存时间，比max-age指定时间数值更小**，那么**客户端接收缓存资源**。

****

##### **Expires--有效期**

Expires的中文意思是“有效期”。它就是**告诉浏览器缓存的有效期**。如果过期，它会**转向源服务器请求该资源**。*（然后又继续缓存本次请求）*

```
Expires: Wed, 04 Jul 2019 08:26:05 GMT
```

Expires头唯一有效值是HTTP时间。

这里的时间是**格林威治时间(GMT),而不是本地时间**。

可以看到这里的时间是，2019-7-04 08:26:05  。到**这个时间之后该资源就过期**了。而我们请求的时间是Date头中的值，也就是说Date头的值小于Expires头的值，就继续从缓存中读取数据，同时返回200(from cache)

因此，如果源服务器不**希望缓存服务器对该资源进行缓存**，最好在**Expires字段内写入与首部字段Date相同的时间值**。

在HTTP/1.1版本中，**优先处理max-age，忽略Expires**  {和缓存失效的版本迭代不同}

在HTTP/1.0版本中，则会优先Expires,忽略max-age

****

##### 为什么有了Expires,还要使用max-age？

相对Expires而言，max-age是距离请求发起的时间的秒数。

针对应用中**那些不会改变的文件**，通常可以手动**设置一定的时长以保证缓存有效**，例如图片、css、js等静态资源。

而**给每一个资源设置一个特定时间，麻烦且容易忘记！**

如果返回内容的时候没有更新这个过期时间，则每个请求都是上访到服务器，反而增加了负载和响应时间。



****

#### 缓存验证

##### **ETag** ---强校验器 {校验值}

ETag是缓存的一种强校验器（HTTP/1.1上新加入的）。它用来唯一**标识资源，以及缓存过期后验证资源是否失效**。

例如：中文版和英文版的谷歌搜索的某次页面的ETag分别如下：【服务器响应的ETag头】



中文版：

```http
ETag: usagi-abcd
```

英文版：

```http
ETag: usagi-efgh
```

此时就会**分别进入不同的页面**

因为两者的ETag值不一样！当两者的URI相同时，凭借URI返回指定的资源/页面，是非常困难。**这个时候为了提高区分度，使用ETag值来确认URI相同的资源**。

**ETag头的值的使用：将缓存资源所对应的ETag头的值，放入if-None-Match中，然后源服务器通过验证if-None-Match头的ETag值和最新的该资源的ETag是否一致**。如果一致则表示缓存资源有效，返回 304 Not Modified**。否则如前文所述的结果验证阶段！当服务器判断**该缓存已经失效，那么就会返回新数据**，HTTP **状态码为 200**。

请求

```http
Request URL: https://www.jianshu.com/shakespeare/v2/notes/c70278f133ed/audio
Request Method: GET
if-none-match: W/"e39f603a5ebcff23859d200f9c9dc20f"
```

响应

```http
etag: W/"e39f603a5ebcff23859d200f9c9dc20f"
server: Tengine
status: 304
```

****

##### Last-Modified  ---弱校验器  {也是校验时间的}

*ETag优先于Last-Modified*



Last-Modified 响应头可以**作为一种弱校验器，因为它只能精确到1秒**。

如果响应头里含有这个信息，客户端可以在**后续的请求**中带上 `If-Modified-Since` 来验证缓存

*Last-Modified-Since中指定的时间，可以看做是缓存失效的时间。{是缓存失效时间，不是缓存过期时间}当缓存超过这个时间，按照失效处理，向源服务器获取最新资源。未超过这个时间，算是未失效，使用缓存*

**弱校验器验证缓存：**

当资源过期时(使用Cache-Control标识的max-age),客户端在后续请求中带上**if-Modified-Since，表示指定的时间**。

响应：

Response Headers中

```http
Date: Sat, 01 Feb 2020 12:25:54 GMT
EagleId: 3a31e19615805599584152927e
Etag: 3bcab93a396a2a97b3c7b1cea658c562de44c83e
Expires: Sat, 01 Feb 2020 20:34:50 GMT
Last-Modified: Mon, 20 Jan 2020 15:42:22 GMT
```









请求：

Request Headers中

```http
Host: s1.hdslb.com
If-Modified-Since: Mon, 20 Jan 2020 15:42:22 GMT
If-None-Match: 3bcab93a396a2a97b3c7b1cea658c562de44c83e
```









源服务器收到请求后发现有if-Modified-Since，则**用if-Modified-Since与请求资源最后修改时间进行比对**。看**指定时间之后，资源是否修改{也就是指定时间是否大于资源最后修改时间。相等，也代表未修改}**

资源被修改{可能失效}：从**源服务器返回新的资源内容**（写在响应消息包体内），HTTP 200

资源未修改{也就是未失效}：响应 HTTP 304 (无需包体，节省流量)，**告知浏览器继续使用缓存**



****

##### 为什么有了Last-Moidfied，还要使用ETag? {两者都是服务器响应回来的}

- Last-Modified 标注的最后修改**只能精确到秒级**。如果某些文件在**1秒钟以内，被修改多次**，它将**不能准确标注文件的修改时间**。

  *{这条最关键}*

- 如果某些文件会被定期生成，当有时内容并没有任何变化（**只是改变了部分**，而**弱ETag值则不会变，因此使用弱ETag时可以进行使用缓存**），但Last-Modified却改变了，导致文件没法使用缓存。

- 有可能存在服务器**没有准确获取文件修改时间**，或者**与代理服务器时间不一致**等情形。

**Last-Modified 与 ETag 是可以一起使用的（两者经常搭配使用），服务器会优先验证 ETag{也就是忽略Last-Modified}，一致的情况下，才会继续比对 Last-Modified，最后才决定是否返回 304。**



****

# 字段 if-Xxxx

形如if-xxx这种形式的 请求首部字段，都可称为条件请求。服务器接受到附加条件的请求后 ，**只判断指定条件为真时，才会执行请求**。





## if-Match

首字段if-Match ：它会告知服务器匹配资源所用到的实体标记(ETag)值。

**说人话：服务器有一个叫ETag的标记，这个标记是一个值。**

服务器：如果客户端发的请求能符和条件，则接受请求

**说人话：当if-Match后面的哪个字段值和ETag值一致，服务器才会接受客户端的请求**

例如：

客户端发的请求：

```http
GET/index.html
If-Match:"123456"
```

服务器端的实体标记的值也为123456，**两者一致**

则会返回

```http
200 OK
```

**表示能够成功接受请求**



如果服务器端的实体标记的值为654321，**两者不一致**

则**服务器端不执行请求，会返回**

```http
412 precondition failed
```

**表示接受请求失败**





## if-Modified-Since



如果在if-Modified-Since字段指定的日期时间后，资源发生了更新，服务器会接受请求。

**说人话：if-Mondified-Since 是一个请求头字段。它的值是一个日期时间，也就是说这个请求头所绑定的要请求的资源，被这个请求头所指定了一个日期时间。如果这个资源在指定的日期时间后没有更新，则不接受请求。**





例如：

**客户端的请求：**

```http
GET/index.html
if-Modified-Since:Thu,15  Apr 2019 00:00:00 GMT
```

它的日期是：

Thu,15  Apr 2019 00:00:00 GMT



而index.html这份资源的更新时间是

 Sun, 29 Aug 2019 14:03:05 GMT



**更新资源的时间在指定的时间之后，可以接受请求**



**因此服务器端的响应是：**

```http
200 OK
Last-Modified: Sun, 29 Aug 2019 14:03:05 GMT
```



**如果更新资源的时间在指定的时间之前，则不接受请求**

**因此服务器端的响应为**

```http
304 NOt Modified
```







****

## if-None-Match 【常见，经常和ETag值一起用】

与if-Match相反。if-Match是它所对应的值和服务器端的ETag值一致，就接受请求！

**if-None-Match则是它所对应的值和服务器端的ETag值不一致**，就接受请求！





例如：

请求

```http
Request URL: https://www.jianshu.com/shakespeare/v2/notes/c70278f133ed/audio
Request Method: GET
if-none-match: W/"e39f603a5ebcff23859d200f9c9dc20f"
```

响应

```http
etag: W/"e39f603a5ebcff23859d200f9c9dc20f"
server: Tengine
status: 304
```



或者 

客户端的请求：

```http
PUT/sample.html
If-None-Match: *
```



*也可以指定字段值。

如果服务器端不存在sample.html，可以接受请求

```http
200 OK
```

**因为资源不存在，所以对应的ETag也不存在**



**在GET或HEAD方法中使用头字段If-None-Match还可获得最新的资源。**

**因此，这与使用首部字段if-Modified-Since有的类似（它是按照指定的时间，获取该时间之后更新的最新资源）**



****



## if-Range

If-Range字段若是跟**ETag的值或更新的日期时间**匹配一致，就作为范围请求处理。

if-Range和Range**这两个字段经常一起使用**，if-Range**指定接受服务器端接受请求的条件。**而**Range指定请求影响的范围**

if-Range和前面的if-Match、if-Modified-Since类似，**它们都是指定条件。它们后面的值就是条件，可能是时间也可能是实体标记(ETag)的值。满足条件才能接受请求。**

if-Range后面的值：

如果和服务器端的ETag的值一致则类似于If-Match，**服务器端就接受下一行的Range范围请求**。

如果和时间日期的值类似（或者说看着像是时间日期格式），则类似于If-Modified-Since，**服务器端的资源在这个时间之后更新就接受下一行的Range范围请求**



**反之，则忽略Range中的范围，返回全部资源，以及Etag的值，**

例如：

客户端的请求

```http
GET/index.html
If-Range: "123456"
Range: bytes=5001-10000
```

**如果实体标记的值为123456**

则服务器端返回 [相当于成功]

```http
206  Partial Content
Content-Range:bytes 5001-10000/10000
Content-Length:5000
```



**如果实体标记的值为654321**

则服务器端返回 [相当于失败]

```http
200 OK
ETag: "654321"
```

**如果没有使用这个字段，服务器端的资源更新，客户端持有资源中的一部分也会随无效，这时Range这个范围请求作为前提已经无效了**

**（要的部分资源已经没有了，范围的资源又不能为无效资源，只能返回412让客户端再次发送请求）**

****

## Range

```http
GET/
Range: bytes=5001-10000
```

和上面的if-Range相比，它少了一重判断（if-Range增加了判断方式，也就增加了**区分度**。不符合if-Range增加的条件，**依旧会是无视请求范围**）！

Range**无需验证ETag的值或者指定时间**，直接就可以**接收请求获取请求范围的资源，以及状态码206**。

如果**无法处理请求(例如请求范围不存在)，则返回状态码200，以及无视掉范围请求返回全部资源。**

例如：上面的请求范围是5001-10000，如果最大的范围只有2000

这时和if-Range类似，**但不返回ETag的值**

```http
200 OK
```











****

## if-Unmodified-Since

它和if-Modified-Since的关系就像if-Match和if-None-Match之间的关系

**两者的效果刚好相反**

if-Modified-Since**的作用是告诉服务器只有在字段值（所指定是时间）之后，发生更新，才能处理请求**，*否则返回304*。

而if-Modified-Since**的作用是告诉服务器只有在字段值（所指定的时间）之后，未发生更新，才能处理请求**，*否则返回412*。

****







#  其他字段

## Max-Forwards

该字段后的值为**十进制整数**

这个数字表示：**每次在服务器中转发请求，值减1。当值减到0时，会返回请求！**

【问，请求转发是否会值减1？？？】

**该字段主要用来“定位”请求，如果中途出现问题，不返回请求，则可以通过该字段得知是最终请求到达的地方。“定位”问题出现的地方**

例如：

通信图：

客户端---> 代理服务器A<--->代理服务器B    源服务器

**我们可以看到代理服务器A和代理服务器B之间请求陷入了循环。从A到B，由B到A，不断循环。此时的源服务器不会接收到来自代理服务器B的请求**

*如果这里使用的Max-Forwards这个字段，当其中的数字变为0时，直接返回！至此可以跳出循环（本来是到源服务器再返回，这个时候已经到不了源服务器了，多了一个"保险机制"，到0直接返回响应）*





****

## Referer  【常见的字段，和302一起出现，抓包有时显示的是其小写形式referer】

Referer后面的值是**请求发起处的原始URI**

【特别是在请求重定向时，两次请求中都会存在Referer】

它的作用是**查看Referer就可以知道请求的URI是哪个Web页面发起的**

例如：

客户端的请求

```http
GET/
Referer: https://www.zhihu.com/signin?next=%2F
```

我们可以看到Referer的值是：

```http
https://www.zhihu.com/signin?next=%2F
```

也就是说https://www.zhihu.com/signin?next=%2F是**请求的URI是由这里发起的**



客户端一般都会发送Referer首部字段给服务器，但当直接在浏览器的地址栏输入URI（也就是get方式请求），或**出于安全性的考虑，也可以不发送该首部字段**

*因为原始页面的URI中的查询字符串可能含有ID和密码等保密信息！*

要是写进Referer转发给其他服务器，可能会导致泄密



另外，Referer的正确拼写为Referrer，但不知为何，大家一直沿用这个错误的拼写。

****

## TE



```
TE:gzip,deflate;q=0.5
```

TE和首部字段Accept-Encoding的功能很像，**但是用于传输编码**

q=0.5也是表示的权重值为0.5。

它有两个作用：**指定传输编码方式和指定伴随trailer字段的分块传输编码方式**

1.TE会告诉服务器，**客户端能够处理的传输编码方式以及相对优先级**

2.指定伴随trailer字段的分块传输编码方式。应用时**只需把trailers赋值给该字段值**。如下：

```http
TE:trailers
```



****

## User-Agent [常见，基本就在最后一行的位置]

例如：

```http
user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.53 Safari/537.36 Edg/80.0.361.33
```

User-Agent的作用是 ：将创建请求的**浏览器和用户代理名称等信息**传给服务器

由网络爬虫发起请求时，有可能会在字段内添加爬虫作者的地址。

此外，如果请求经过代理，那么中间也可能被添加上代理服务器的名称

User-Agent表示**客户端代理**，使得服务器能够**识别客户使用的操作系统及版本、CPU 类型、浏览器及版本、浏览器渲染引擎、浏览器语言、浏览器插件等**。这样服务器就能区别不同种类的客户端，做出不同的数据返回操作

****

# 响应头

## Accept-Ranges[图片资源文件中常见]

例如：

在百度首页**中的资源文件(png，gif，jpg等格式的图片)**

```http
Accept-Ranges: bytes
Cache-Control: max-age=0
Content-Length: 0
Content-Type: image/gif
Date: Tue, 21 Jan 2020 13:09:53 GMT
Etag: "4280832337"
Expires: Tue, 21 Jan 2020 13:09:53 GMT
Last-Modified: Fri, 23 Oct 2009 08:06:04 GMT
Pragma: no-cache
Server: BWS/1.0
```





这个响应头，看着就和Accept和Range这两个字段有关

和Range有关，也就和范围请求有关了。



Accept-Ranges它有两个值，bytes和none。

**这个响应头 是响应给客户端，服务器是否能处理范围请求(例如上面的Range头中的请求范围)，以指定获取服务器端某部分的资源。**

可以处理则返回：

```http
Accept-Range: bytes
```

不能处理则返回 ：

```http
Accept-Range: nones
```

****

## Age [常见的响应头]

响应头Age能告诉客户端，源服务器在多久前创建了响应。字段值的单位为秒。

**说人话：服务器创建了响应，到客户端接收到响应这个过程过了多少秒**

若创建该响应的服务器是缓存服务器，Age值是**缓存后响应再次创建，到响应被客户端接收的时间。**

**代理服务器创建响应时必须加上首部字段Age**

例如：

```http
Age: 600
```

表示的是**从响应创建到接收用了600秒**

****

## ETag [常见+面试重点]



*ETag这个字段能告知客户端实体标识，它是一种可以将资源以字符串形式做唯一标识的方式*

bilibili的favicon.ico （页面最左侧的小图标）的Etag

```http
ETag: "57974352-10be"
```

**服务器会为每份资源分配对应的ETag值**,*上面说的各类图片资源，以及js,css文件大多都是抓包就肉眼可见。*[至于没有格式后缀的文件，直接抓包很多就不能肉眼可见ETag值了。。]

*所以说：抓包出来的文件被分为三类了？？？ 图片资源，代码文件，无后缀名文件？？？*

例如：中文版和英文版的谷歌搜索的某次页面的ETag分别如下：

中文版：

```http
ETag: usagi-abcd
```

英文版：

```http
ETag: usagi-efgh
```

当资源更新的时候，ETag值也需要更新。ETag的值生成仅仅是由服务器来分配，没有统一的算法，仅仅是由服务器来分配。

**资源被缓存时，就会被分配唯一性标识**。我们使用中文版的浏览器访问

```http
http://www.google.com/
```

就会返回中文版的页面。

而我们使用英文版的浏览器，同样的访问

```http
http://www.google.com/
```

则会返回英文版的页面

**why???**

因为两者的ETag值不一样！当两者的URI相同时，凭借URI返回指定的资源/页面，是非常困难。**这个时候为了提高区分度，使用ETag值来确认URI相同的资源**。即使下载/接收响应过程中出现连接中断，再连接的情况，依旧会按照ETag的值来指定资源。



**强ETag的值和弱ETag的值**

强ETag的值：**不论实体发生多么细微的变化都会改变其值**

```http
ETag: "57974352-10be"
```

弱ETag的值：**只用于提示是否相同 。只有资源发生了根本改变，产生差异时才会改变ETag值。这时，会在字段值最开始处附加w/**

```http
etag: W/"9b04-166e2db7c58"
```

**每个ETag值必然有强/弱这一属性，可以用来区分资源是否需要更新/过期**

**源服务器通过判断缓存资源的ETag值和最新的该资源的ETag是否一致。如果一致则表示缓存资源有效，返回 304 Not Modified**



案例源码

```http
Request URL: https://unpkg.zhimg.com/@cfe/sentry-script@0.0.10/dist/init.js
Request Method: GET
Status Code: 200  (from disk cache)
Remote Address: 119.96.207.98:443
Referrer Policy: no-referrer-when-downgrade
access-control-allow-origin: *
age: 1014885
ali-swift-global-savetime: 1578473304
cache-control: public, max-age=31536000
content-encoding: br
content-length: 14236
content-type: application/javascript
date: Wed, 08 Jan 2020 08:48:24 GMT
eagleid: 7760cf4d15794881896164511e
etag: W/"9b04-166e2db7c58"
server: Tengine
status: 200
timing-allow-origin: *
vary: Accept-Encoding
via: cache11.l2cn1816[0,200-0,H], cache1.l2cn1816[0,0], cache3.cn1337-1[0,200-0,H], cache1.cn1337-1[2,0]
x-backend-response: 0.002
x-cache: HIT TCP_MEM_HIT dirn:5:385192870
x-idc-id: 1
x-lb-timing: 0.003
x-powered-by: Express
x-secng-response: 0.003000020980835
x-swift-cachetime: 31104000
x-swift-savetime: Sat, 18 Jan 2020 21:32:00 GMT
Provisional headers are shown
Referer: https://www.zhihu.com/signin?next=%2F
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.53 Safari/537.36 Edg/80.0.361.33

```



来一个**不靠谱的 抓包经验规律**：

**图片这类的文件**，基本都**是强ETag值**

而**js,css这类的代码文件**，**可能是弱ETag值**

可能是图片这类，略有改变会直接影响页面，而代码文件的改变未必会影响页面（例如代码中添加空格）



可以**将缓存资源的 ETag 值**放入 If-None-Match 首部，服务器**收到该请求**后，**判断缓存资源的 ETag 值和资源的最新 ETag 值是否一致**，如果**一致则表示缓存资源有效**，返回 304 Not Modified。

```
If-None-Match: "82e22293907ce725faf67773957acd12"
```





****

## Location [常见，有302的地方就有它]

Location这个响应头的值就是**重定向后的URL**，**或者说是客户端接收到这个响应头后，根据它指定的URL，然后重新向服务器端发送请求，找到对应的资源**

例如：

客户端第一次发送请求

```http
Request URL: https://unpkg.zhimg.com/@cfe/sentry-script@latest/dist/init.js
Request Method: GET
referer: https://www.zhihu.com/signin?next=%2F
```

服务器A接收请求并做出响应

```http
location: /@cfe/sentry-script@0.0.10/dist/init.j
server: Tengine
status: 302
```

客户端第2次发送了请求

```http
Request URL: https://unpkg.zhimg.com/@cfe/sentry-script@0.0.10/dist/init.js
Request Method: GET
Referer: https://www.zhihu.com/signin?next=%2F
```

服务器端B做出了响应

```http
etag: W/"9b04-166e2db7c58"
server: Tengine
status: 200
```



基本上，该字段会配合3xx：Redirection的响应，提供重定向的URI

几乎所有的浏览器接收到Location这个响应头后，都会**强制性地尝试对已提示的重定向资源进行访问**

****

## Proxy-Authenticate

响应头Proxy-Authenticate的值是**代理服务器所要求的认证信息**

它与客户端和服务器之间的HTTP访问认证的行为相似，不同之处在于其认证行为是在客户端与代理之间进行的。

而客户端与服务器之间进行认证时，请求头WWW-Authorization有着相同的作用。

****

**Retry-After **

响应头Retry-After后面的值表示：**客户端在多久之后再次发送请求。**主要配合状态码503使用！

有时也配合3xx使用

字段值可以指定为**具体的日期时间**，也可以是**接收响应后的秒数**

例如：

响应为

```http
Retry-After: 120
```

表示接收响应后**120秒**，**客户端将再次发送请求**



****

## Server [基本是每个响应都必有的]



server后面的值表示：**服务器上安装的HTTP服务器应用程序的信息。不单单会标出服务器上的软件应用名称，还有可能包括版本号和安装时启用 的可选项**

*这里的server中的信息，可能有时候并不太标准。省略，缩写，没注意大小写的请求都存在*

**一个写的比较好的server响应头：**

```http
server: JSP3/2.0.14
```

来自百度首页

居然还在用JSP？？？

当然，其中也有自研的web服务器

```http
Server: BWS/1.1
```

至于省略版本号的，挺多的

```http
Server: Apache
```

****

## Vary[常见的响应头 貌似还是前端关于http中的一个坑]

参考资料：【看看就可以了】

https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Vary

http://www.ccc5.cc/2375.html

https://blog.csdn.net/josjiang1/article/details/82147948

这时从哔哩哔哩中抓包得到的响应头：

```http
vary: Origin,Accept-Encoding
```

而在《图解HTTP》一书中，给的例子是

```http
Vary:Accept-Language
```

通过判断 自然语言(Accept-Language)是否相同，来对代理服务器进行操作。而在我抓包的过程中，没有直接**在代理服务器和客户端中找到vary对应的值**。

*说人话：没有找到Origin和Accept-Encoding这两个头*

于是只能求助各类博客，结果好像更难理解。。。。

最后还是看图，图旁的文字还是比较容易理解一点，下面的文字就。。。

![](C:\Users\fucker\Pictures\http.2.PNG)

一会儿是返回缓存，一会儿是进行缓存。。。真的是。。。

大致捋一捋

*Vary这个响应头，从源服务器发送到代理/缓存服务器，然后代理/缓存服务器接收到客户端发的请求时，根据Vary的值（分号后面的那个字段）所对应的值（分号后面的那个字段所对应的值）进行比较：*

*两者相同则返回缓存的资源返回给客户端*

*两者不相同则必须从源服务器重新获取资源*



**这里的 实际应用中，Accept-Encoding所对应的值：**

*Request Headers*中的该字段

```http
Accept-Encoding: gzip, deflate, br
```

三个值按照自然顺序，权重依次是gzip>deflate>br

也就是说当缓存服务器返回的Accept-Encoding中，和这三个不一致就必须从源服务器重新获取资源。

这篇博客靠谱一点

https://blog.csdn.net/qq_29405933/article/details/84315254

> 不同的客户端可能支持的压缩编码方式不同，可能有的客户端不支持压缩，那么服务器端返回的数据就不能压缩，有的支持gzip编码，那么服务器端就可以进行gzip编码返回给客户端，客户端获取到数据之后，做相应的gzip解码。
>
>  
>
> Accept-Encoding表示客户端支持的编码格式，常见的编码格式有gzip/compress/deflate/identity，服务器端会根据客户端提供的Accept-Encoding对返回的内容进行编码，并通过添加响应头Content-Encoding表明服务器端使用的编码格式。详解请参考我的另一篇博客[连接]；
>
> 
>
> User-Agent表示客户端代理，使得服务器能够识别客户使用的操作系统及版本、CPU 类型、浏览器及版本、浏览器渲染引擎、浏览器语言、浏览器插件等。这样服务器就能区别不同种类的客户端，做出不同的数据返回操作。

另外还有一段也讲的很好

> Vary存在于响应头中，它的内容来自于请求头中相关字段，Vary头的内容如果是多条则用“,”分割。缓存服务器会将某接口的首次请求结果缓存下来（包括响应头中的Vary），后面在发生相同请求的时候缓存服务器会拿着缓存的Vary来进行判断。比如Vary: Accept-Encoding,User-Agent，那么Accept-Encoding与User-Agent两个请求头的内容，就会作为判断是否返回缓存数据的依据，当缓存服务器中相同请求的缓存数据的编码格式、代理服务与当前请求的编码格式、代理服务一致，那就返回缓存数据，否则就会从服务器重新获取新的数据。当缓存服务器中已经缓存了该条请求，那么某次服务器端的响应头中如果Vary的值改变，则Vary会更新到该请求的缓存中去，下次请求会对比新的Vary内容。

这里的

> 当缓存服务器中已经缓存了该条请求，那么某次服务器端的响应头中如果Vary的值改变

其中的缓存服务器缓存的该条请求，**指的是Vary**

例如：

```http
Vary:Accept-Language
```

而这里某次服务器端的响应头中的Vary的值改变，指的是源服务器返回响应给缓存服务器时，**返回的响应头中的Vary的值发生改变**

*（我们都知道，缓存服务器终究只是一个“中转站”，而终点始终是源服务器。起点与终点的通信始终不会断，因此通信的过程中源服务器会不断发送响应的）*

**如Accept-Language变成Accept-Encoding**，那么缓存服务器中的Vary**也会更新**，下次请求时会**对比新的Vary内容**



*这里写博客时可以举出具体的例子，好好水一波*



最后的一部分

> 官方解释Vary头：告知下游的代理服务器，应当如何对以后的请求协议头进行匹配，以决定是否可使用已缓存的响应内容而不是重新从原服务器请求新的内容。
>
> Vary: * ，这个我不太理解，我个人的理解是，当Vary的值为“*”时，意味着请求头中的那些字段的值不能用来区分当前请求是从缓存服务拿还是重新请求获取，在Android的OkHttp框架中，客户端接收到服务器的响应数据，进行缓存处理时，一旦判断响应头有Vary:*时，就不缓存该条数据。所以我猜想缓存服务器会不会也是这样，当Vary的值为“*”时，不做缓存。

**重点是官方解释中的两个作用中的前一个：**

**告知下游的代理服务器，应当如何对以后的请求协议头进行匹配**

其他博客中写的Vary头的大致作用也是**在相同的url下进行有区别的返回不同的缓存结果。**

例如前面的例子：

*两个浏览器，一个旧，一个新，它们请求了相同的缓存资源。旧的浏览器不支持压缩，而新的浏览器支持压缩。我们可以通过给不同的浏览器返回的不同Vary值来区分。*

*（也就是：缓存服务器会将某接口的**首次请求结果**缓存下来[包括响应头中的Vary]，后面在发生相同请求的时候缓存服务器会拿着缓存的Vary来进行判断）*

*然后当新，旧两种浏览器来请求资源时，缓存服务器根据缓存的不同Vary值来比对两种浏览器中的**对应的字段的值是否和Vary值一致，如果一致则讲缓存的资源返回给浏览器，如果不一致则缓存服务器会从源服务器重新获取资源。***

**所以说：缓存服务器从源服务器重新获取资源时，也将客户端的请求带了过去吗？因此才会有对首次请求结果的缓存？？？如果缓存服务器中没有该数据，对于源服务器应该也是可以视作首次请求吧？？？**

****

## WWW-Authenticate [不常见，但和401相伴]

响应头WWW-Authenticate用于HTTP访问认证。

它会告诉客户端*适用于访问请求URI所指定资源的认证方案(Basic或是Digest)和带参数提示的质询（challenge）*

**说人话： 这个有点难翻译啊。。。而且不算多常见。。。也搁置吧**

需要知道的 ：**状态码401Unauthorized响应中，肯定带有首部字段WWW-Authenticate**

例如：

```http
WWW-Authenticate: Basic realm="Usagidesign Auth"
```

****

# 实体首部字段

> 实体首部字段是包含在请求报文和响应报文中的实体部分所使用的首部。用于补充内容的更新时间和与实体相关的信息。

说人话：就是请求体和响应体中的“头部”。HTTP协议中基本都是这种：

**头部：值**

请求体和响应体自然也就不例外。

****





## Allow [不常见，但是和405在一起出现]

首部字段Allow的作用是：

告诉客户端，**所能够支持的请求资源的所有HTTP方法**。

当服务器返回405（客户端请求的方式不对）时，就返回这个首部字段。

*（请求方式不对，就提示所有对的方式）*

关于它和405的部分，详见405。

****



## Content-Encoding [常见+重要]

content这个单词在英文中的意思为：内容

而Encoding这个单词在英文中的意思为:编码方式

首部字段Content-Encoding会告知客户端，服务器端对实体的主体部分选用的内容编码（**压缩**）方式。

**内容编码方式：**

不丢失实体信息的前提下所进行的压缩

主要采用以下4种内容编码的方式：(压缩方式和Accept-Encoding一样，都是那几种)

- gzip
- deflate
- compress
- identity

抓包中常见的：

Request Headers中的：

```http
Accept-Encoding: gzip, deflate, br
```

Accept-Encoding表示的是：

**客户端支持的内容编码格式（解压/压缩）**



而在Response Headers中的：

```http
content-encoding: br
```

Content-encoding表示的是：

**服务器端（对响应实体）采用的内容编码格式（压缩/解压）**

****

## Content-Language

Content在英文中的意思 ：**内容**

而Language在英文中的意思：**语言**

和Content-encoding相似

Content-Encoding表示的是：**服务器端（对响应实体）采用的内容编码格式（压缩/解压）**



而Content-Language则表示的是：

**服务器端（对响应实体）采用的自然语言**

例如：

```http
Content-Language: zh-CN
```

****

## Content-length [基本每个响应实体都有]

Content在英文中的意思 ：内容

length在英文中的意思 ：长度

也是和Content-encoding相似

Content-length表示的是：

**实体主体部分的长度（单位是字节）**

**具体的实体主体大小的计算方式略复杂，可参考RFC2616的4.4**

Content-length的指是多少，就表示多少字节

例如：

来自抓的CSDN中的某个页面的包

```http
content-length：42
```

这里就表示这个资源的实体主体部分是42字节

****



## **Content-Location**

content这个单词在英文中的意思为：内容

而Location这个单词在英文中的意思为: 位置



Content-Location表示的是：**报文主体返回的资源对应的URI**



**当返回的页面内容与实际请求的对象不同时**，首部字段Content-Location内会写明URI

(访问http://www.hackr.jp/ 返回的对象却是http://www.hackr.jp/indenx-ja.html)

例如：

```http
Content-Location: http://www.hackr.jp/indenx-ja.html
```



****

## Content-MD5（其中也是有坑）

采用的MD5算法，对报文主体进行计算，得出128位二进制数。然后**对二进制数（而不是字符串）**进行Base64编码，最后将结果写入Content-MD5字段值。

**由于HTTP首部无法记录二进制值**，所有要通过Base64编码处理。

为了确保时效性，客户端**接收报文主体时会再执行一次MD5算法，并将其二进制值进行Base64编码**，最后将这个值和Content-MD5的字段值进行比对。

即可**判断出报文主体的准确性**

参考博客:

https://www.ituring.com.cn/article/74167

例子：

```http
 Content-MD5: Q2hlY2sgSW50ZWdyaXR5IQ==
```

缺陷为：

1.对内容上的偶发性改变无从查证

2.无法检测出恶意篡改

3.内容如果能够被篡改，最初计算出的Content-MD5的字段值也就是**已经被改变了**。因此客户端接收时，**无法意识到报文主体以及首部字段Content-MD5的值已经被篡改了**。

****

## Content-Range



****

## Content-Type[基本每个响应都有]

首部字段Content-Type的值表示：

**实体主体内对象的媒体类型**

和首部字段Accept一样，字段值的形式为：type/subtype



Request  Headers中的

```http
Accept: image/webp,image/apng,image/*,*/*;q=0.8
```

Response Header中的

```http
Content-Type: image/gif
```

/前面的是文件类型，gif是文件格式

有时也可能有编码方式 

```http
Content-Type: text/html; charset=UTF-8
```

****

## Expires[基本每个响应都有+重要]

Expoires的值表示：

**资源失效日期**

客户都接收了首部字段Expires，也就知道了资源失效的日期。

**而当缓存服务器接收到首部字段Expires时，就会将该请求缓存**

当时间在Expires字段指定的**时间**之前 ，**缓存的请求副本**就会一直被保存。

而**当超过了指定时间后**，当缓存服务器**再次接受客户端请求该资源**时，它会**转向源服务器请求该资源**。*（然后又继续缓存本次请求）*

如果源服务器不**希望缓存服务器对资源进行缓存**，最好在**Expires字段内写入与首部字段Date相同的时间值**。

但是，当**首部字段Cache-Control有指定max-age指令时**，比起首部字段Expires,**会优先处理max-age指令**

它们都属于**缓存过期机制**

> **3.4 缓存过期机制**
>
> max-age 指令出现在请求报文，并且缓存资源的缓存时间小于该指令指定的时间，那么就能接受该缓存。
>
> max-age 指令出现在响应报文，表示缓存资源在缓存服务器中保存的时间。
>
> ```
> Cache-Control: max-age=31536000
> ```
>
> Expires 首部字段也可以用于告知缓存服务器该资源什么时候会过期。
>
> ```
> Expires: Wed, 04 Jul 2012 08:26:05 GMT
> ```
>
> - 在 HTTP/1.1 中，会优先处理 max-age 指令；
> - 在 HTTP/1.0 中，max-age 指令会被忽略掉。



参考：cyc2018的http部分

https://github.com/CyC2018/CS-Notes/blob/master/notes/HTTP.md

****

## Last-Modified

首字段Last-Modified表示**资源最终修改时间**

或者说是**资源上一次被更新的时间**

但类似使用CGI脚本进行动态数据处理时，该值可能变成数据报最终修改的时间。

****

# 具体应用

## 连接管理

### 1.短连接与长连接

浏览器加载一个页面，很多时候除了请求访问HTML页面资源，还会请求很多其他资源，例如图片，js,css 。这些通过抓包就可以直接看出来，抓包中就有很多资源，也就是说**在一次TCP连接中建立了多次HTTP通信**。

而如果每一次进行HTTP通信就要新建一个TCP连接，那么开销就很大。

像这种建立一次TCP连接，就能进行多次HTTP通信的连接方式，我们称为**长连接**

与之相对的**短连接：每进行一次HTTP通信则新建一次TCP连接**



**HTTP与长/短连接：**

- HTTP/1.1之前**默认的是短连接**，如果需要使用长连接，则使用 `Connection : Keep-Alive`。keep-Alive在中文中的意思是活着
- 从HTTP/1.1开始**默认的是长连接**，如果需要断开连接（每次TCP连接结束自然也需要断开连接。长连接在每次HTTP通信结束时断开连接，自然就变成短连接了），需要**客户端或服务器端提出**断开，则需要使用`Connection : close`。

### 2.流水线 {在计算机领域很多地方都用到这个}

**默认情况**：HTTP请求是**按顺序发出**，想要发下一个请求则**需要上一个请求收到响应后**才会发出。

理论上这种方式没有什么不好，但**受到网络延迟和带宽的限制**，在**下一个请求被发送到服务器前**，可能要很长时间等待。

**流水线方式**：在**同一条长连接上连续发出请求**(这时的这一条长连接就可以看做是一条流水线)，而**不用等待响应返回**，这样可以减少延迟。









****



## Cookie

### **Cookie是什么？**

Cookie是**服务器端发送到浏览器端并保存在的一小块数据**，浏览器会在之后向同一个服务器请求时携带上Cookie,此时可用来**告知服务器，浏览器的“身份”**{告诉服务器这次的请求和上一次的请求来自同一个浏览器}

**缺点：**

但这样**每次都会需要携带Cookie**,因此会带来**额外的性能开销** (尤其是在移动环境下)

****

### 为什么要用Cookie？

**作用:用户识别及状态管理**

虽然Cookie没有被编入标准化HTTP/1.1的RFC2616中，但在Web网站方面得到了广泛的应用。

*说人话：HTTP是无状态的协议，无法保存信息。HTTP/1.1引入Cookie来保存信息*



Cookie 曾一度用于客户端数据的存储，因为当时并没有其它合适的存储办法而作为唯一的存储手段，但现在随着现代浏览器开始支持各种各样的存储方式，Cookie 渐渐被淘汰。新的浏览器 API 已经允许开发者直接将数据存储到本地，如使用 Web storage API（本地存储和会话存储）或 IndexedDB

****

### **Cookie有什么具体的用途？**

- 会话状态管理（如用户的登录状态，购物车）
- 个性化设置(如用户自定义设置，主题)
- 浏览器行为跟踪（如跟踪分析用户行为）

****

### Cookie怎么用？

**创建/使用过程**：Cookie使用的流程图

1. 服务器向**发送客户都的响应报文中含有Set-Cookie首部字段**

   ```http
   HTTP/1.0 200 OK
   Content-type: text/html
   Set-Cookie: yummy_cookie=choco
   Set-Cookie: tasty_cookie=strawberry
   
   [page content]
   ```

2. 客户端接收到响应后，**把Cookie的值保存在浏览器**中

3. 客户端再次向同一个服务器发送请求时，**取出浏览器中的Cookie**
   **信息**，**通过Cookie请求头发送**给服务器端

   ```http
   GET /sample_page.html HTTP/1.1
   Host: www.example.org
   Cookie: yummy_cookie=choco; tasty_cookie=strawberry
   ```

4. 服务器端通过**客户端发的Cookie识别用户和其认证状态**



### Cookie的分类

**会话期Cookie:**

浏览器**关闭之后它会自动删除**，也就是说仅在会话期有效



**持久性Cookie:**

对于会话期的Cookie，**在Set-Cookie中指定过期时间（Expires）或有效期（max-age）**之后，就成为了就持久性的Cookie

```http
Set-Cookie: id=a3fWa; Expires=Wed, 21 Oct 2015 07:28:00 GMT;
```



****

### Cookie的作用域：{作用范围}

`Domain` 和 `Path` 标识定义了Cookie的*作用域：*即**Cookie应该发送给哪些URL。**

**Set-Cookie下的参数----Domian**

**Domian属性的作用：**代表发送的

Domain属性的值**指定了哪些主机可以发送Cookie**。

如果**不指定Domain的值**，则**默认当前文档的主机**。

如果**指定了Domain的值**，则**一般包含子域名（即只要含有这段域名的都可以发送Cookie）**



例如：设置Domain=examople.com，**除examople.com此外**，www.examople.com或www2.examople.com等这些**包括  examople.com 的都可以发送Cookie**。



因此，除了针对**具体指定的多级域名**{也就是那种非常的具体的域名}发送Cookie之外，**不指定domain更安全**



总结：大多数情况下，**发送Cookie的是创建Cookie的主机**



****

**Set-Cookie下的参数 -----Path**

**Path属性的作用：**代表接受的

Path 标识**限制指定了主机下的哪些路径可以接受**Cookie(该URL路径必须存在于请求URL中)。

但另有办法可以避开这项限制

**若不指定则默认为文档所在文件的目录**

以字符%x2F("/")作为路径分隔符，子路径也会被匹配。

例如，设置Path=/docs,则以下地址都会匹配

- /docs
- /docs/Web/
- /docs/Wed/HTTP

****

**总结:Domain代表哪些主机可以发送Cookie,{也就是说发送Cookie是以主机为单位的}。而Path则代表主机可以在什么目录/路径下接受的Cookie**

****

### JavaScript与Cookie

#### JavaScript通过Document.cookie访问Cookie

通过`Document.cookie`这个属性可以创建Cookie,也可以通过该属性访问非HttpOnly标记的Cookie

```javascript
document.cookie = "yummy_cookie=choco";
document.cookie = "tasty_cookie=strawberry";
console.log(document.cookie);
```

****

#### HttpOnly

刚才说过JS可以通过`Document.cookie`这个属性访问非HttpOnly标记的Cookie。

也就是说**被HttpOnly标记的Cookie不能被JS脚本调用**

而跨站点脚本攻击(XSS)常常用JS的`document.cookie`这个属性调用{窃取}用户的Cookie信息，因此**HttpOnly标记可以在一定程度上避免XSS攻击**

用HttpOnly标识的例子：

```http
set-Cookie: id=a3fwa; Expires=Wed, 21 Oct 2015 07:28:00 GMT; Secure; HttpOnly
```

****

### 如何限制Cookie{只在使用HTTTPS连接时}的发送？

**secure**属性



我们知道HTTP协议很多时候不安全，而且会自动发送Cookie。

**那如何限制页面只在使用HTTPS安全连接时发送Cookie?**

我们只需要在Set-Cookie这个响应头中加上**secure属性**

因为是在响应头中限制，也就是说是告诉浏览器，让**浏览器在非HTTPS安全连接时，不能发送Cookie**

```http
Set-Cookie: name=value; secure
```



就算是域名相同，但是使用的连接不同，一样不能发送Cookie。

例如：https: //www.baidu.com  和http://www.baidu.com 

只有前面使用HTTPS连接的，才能发送Cookie



但即便设置了 Secure 标记，**敏感信息也不应该通过 Cookie 传输**，因为 Cookie 有**其固有的不安全性**，Secure 标记也**无法提供确实的安全保障**。

****



### Cookie安全性

当机器处于不安全环境时，切记*不能*通过HTTP Cookie存储、传输敏感信息

****

### 浏览器禁用Cookie时，怎么办？



此时无法使用 Cookie 来保存用户信息，只能使用 Session。除此之外，不能再将 Session ID 存放到 Cookie 中，而是**使用 URL 重写技术，将 Session ID 作为 URL 的参数进行传递。**



****

## Session

### **Session是什么？**

Session ---被称为“会话控制”

除了可以将用户信息通过Cookie存在客户端中，还可以使用Session存储在服务器端。**存储在服务器端的信息更安全**



> Sesssion是另一种记录浏览器状态的机制。不同的是Cookie保存在浏览器中，而Session保存在服务器中。
>
> 用户使用浏览器访问服务器时，服务器把用户的信息以某种形式记录在服务器，这就是Session



Cookie像是“自报家门”的名片，来“主动告知”服务器用户的身份。

Session则像是“老师查考勤 ”的花名册，服务器根据“花名册”来核对客户端的身份。

****

### 为什么要使用Session？

-  **可存储性：**   Cookie 只能存储 ASCII 码字符串，而 Session 则可以存储任何类型的数据，因此在考虑数据复杂性时首选 Session；
- **安全性：**    Cookie 存储在浏览器中，容易被恶意查看。如果非要将一些隐私数据存在 Cookie 中，可以将 Cookie 值进行加密，然后在服务器进行解密；



同时，Cookie也有其优势

- 对于大型网站，如果用户所有的信息都存储在 Session 中，那么开销是非常大的，因此不建议将所有的用户信息都存储到 Session 中。

****

### Session的存储

Session 可以存储在服务器上的文件，数据库或者内存中。也可以将Session存储在Redis这种内存型数据库中，效率更高。

****

### Session的原理--Session是如何工作的？{流程图}

使用Session维护用户登录的过程如下：

1. 用户登录时，将包含密码和用户名的表单放入HTTP请求报文中发给服务器
2. 服务器接收到请求后，开始校验用户名和密码。如果正确则会把用户信息存储到Redis中，它在Redis中的Key称为Session D
3. 接着服务器将Set-Cookie这个响应头中放入Session ID，并将响应报文返回给客户端。客户端收到响应报文后，将这个Cookie值存入浏览器
4. 当客户端再次向同一个服务器发出请求时，会取出浏览器中的Cookie值，放入请求头Cookie中，并将请求报文发送给服务器
5. 服务器再次收到请求后，提取出Cookie头中的Session ID{也就是Cookie值}，校验Session ID。校验通过，则从Redis中取出用户信息，继续之前的业务操作



### Session ID的安全性

Session ID很重要！如果被第三方盗走，对方就可以用这个身份进行恶意操作！！

因此，Session ID应该是比较难猜的字符串，且**服务器端需要对Session ID进行有效期管理，保证其安全性**

而在安全性要求极高时，涉及金钱交易时，除了Session ID进行身份验证外，还需要短信验证码、邮箱验证码、甚至是生物信息验证等方式来再次验证用户省身份。



****

# HTTPS

## HTTPS是什么？

披着SSL的HTTTP协议。实质是：**HTTP的通信接口被SSL协议所取代**。

原本是**HTTP协议直接TCP通信**，现在是**HTTP协议先和SSL协议通信，然后由SSL协议和TCP协议进行通信**。

****

## HTTP与HTTPS的区别： {常见面试题}

1. HTTP的URL是以HTTP://开头的，而HTTPS的开头则是以HTTPS://开头的
2. HTTP的标准端口是80，而HTTPS的端口是443
3. 在OSI网络模型中，HTTP工作于应用层，**而HTTPS的安全传输机制工作在传输层**
4. HTTP是不安全的，而HTTPS是安全的  {引出安全性问题 加密，证书，完整性保护}     **为什么不安全？**
   - HTTP在传输时是以明文的形式传输的，而HTTPS则是加密传输的
   - HTTP无需证书，而HTTPS需要CA机构颁发的SSL证书







****

## 补充：HTTPS相关名词解释

### 1.公钥&私钥：

公钥与私钥组合起来是**一对密钥**

公钥：密钥中公开的部分

私钥：密钥中不公开的部分 



### 2.对称加密&非对称加密：

对称加密：加密原文（时）与解密密文（时）所使用的密钥为**同一个密钥**的加密方法

对称加密的原理：**加密算法是公开的**，靠的是密钥来加密数据，使用**一个密钥加密，用相同的密钥才能解密**

*常见的对称加密算法：DES,3DES,AES*，三者加密强度依次提高。DES相对最容易破，3DES是用DES算法加密了3次的产物，现在用的是最多的是AES，强度也最高。

对称加密算法**优点：计算量相对较小，加密和解密的速度比较快，适合加密比较大的数据  **

对称加密算法**缺点：密钥的传输容易泄露，一个用户需要对应一个密钥，服务器管理密钥比较麻烦**



****

非对称加密：加密原文（时）与解密密文（时）所使用的密钥为**一对密钥**（公钥与私钥）

*这里比较有意思的一点，非对称是加密和解密时使用的不是同一个密钥 ，按照正常逻辑理解时，可能**有点难以接受**。这里推荐分别实现**用代码实现对称加密和非对称加密***

非对称加密的原理：算法公开，有一个**公钥(public key)**有一个**私钥(private key)**

**公钥**加密只能**私钥**解密

**私钥**加密只能**公钥**解密

**加密和解密使用不同的钥匙**，因此称为非对称加密



**公钥加密，私钥解密：代码演示**





**公钥加密，公钥解密：代码演示**







**非对称加密的流程图：**













非对称加密常用的算法：**RSA**

非对称加密的**优点：加密和解密使用的不同的钥匙，可以传输公钥，数据传输是安全的**

非对称加密的**缺点：计算量大，加密和解密的速度比较慢**



****

### 3.HTTP&HTTPS

HTTP: 超文本传输协议

HTTPS: 超文本传输安全协议。在HTTP基础上加上SSL层



### 4.SSL

SSL:为网络通信**提供安全及数据报完整性的一种完全协议**



### 5.SSL证书

SSL证书： SSL协议的一个典型应用，具有服务器身份验证和数据传输加密的功能



### 6.CA

 CA：即证书颁发机构，正常情况下我们所说的CA是指被信任的证书颁发机构。该机构负责证书申请者的资质审查，证书颁发，证书吊销等证书维护工作。



****

## HTTPS如何使用/使用场景  {不是重点}

应用场景：**金融机构**，**政务系统**，**APP接口**，**行业/门户网站**

**总结：在大公司强推的潮流之下，HTTPS应用的非常广泛**

****

## 证书分类：从使用的终端上分类  {证书与加密无关，只是启验证作用}

1.**S/MIME**  {不怎么常见}

![](C:\Users\fucker\Pictures\http.3.PNG)

这个证书的目的：

- 向远程计算机（服务器）证明你的身份
- 保护电子邮件

**U盾中用的就是这个证书**



**2.Server SSL证书** 【主要】

下面还可以细分为三类：

**DV： 域名认证（验证该证书是否是自己的，签发时间非常快，几分钟即可。成本也最低）**



**OV: 组织验证。需要验证组织（例如企业，公司）的合法性，包括营业执照、税务信息等验证。签发时间稍长，成本略高，单域名每年上千**



**EV：最高级的认证（应该也是用于组织验证）。除了需要OV的全部信息，还需要律师函等证明文件，还需要提供邓白氏的证明。签发时间最长，价格最高。 **



**代码签名证书： web领域不常见，但是各类软件中常见（例如QQ桌面版）**

主要用于软件的代码签名

**目的：**

- 确保软件来自于软件发布者
- 保护软件在发行后不被更改

如图：腾讯QQ的证书  {证书正常，表示软件发布后未被修改过}

![](C:\Users\fucker\Pictures\http.5.PNG)



![](C:\Users\fucker\Pictures\http.4.PNG)

**被修改后：这样就表示软件在发布之后被修改了（未必是修改了里面的代码。例如修改了发布者）**

![](C:\Users\fucker\Pictures\http.6.PNG)

![](C:\Users\fucker\Pictures\http.7.PNG)







****































****



## 什么要有HTTPS？

### **HTTP协议在安全方面的缺陷：**

1.**通信使用明文（不加密），内容可能会被窃听**



2.**HTTP协议无法确定通信方（Web服务器和客户端都可能被伪装，以及无法划分出接受信息的权限用户。）**

*这里还可能因对无意义的请求做出响应，受到海量DoS攻击（拒绝服务攻击）*

3.**无法验证报文的完整性，所以可能已遭篡改**

*这里还可能遭攻击者拦截并篡改内容，也就是受到MITM攻击（中间人攻击）*

****

**HTTPS和HTTP的区别：** {第3点才是重点，前2点前文已述}

1.HTTP协议需要的CA证书，一般收费，免费的很少

2.HTTP是超文本传输协议，信息是明文传输，连接很简单，HTTPS协议是由SSL+HTTP协议构建的可进行加密传输，身份认证的网络协议，比HTTP协议安全。

3.HTTP和HTTPS使用的是**完全不同的连接方式**，用的端口也不一样，**前者是80端口，后者是8443端口**





****

### **HTTPS的优势：**

**加密（防窃听），认证（防伪装），完整性保护（防篡改）**

#### 1.加密:HTTPS采用**混合加密机制**



##### **HTTPS是如何采用混合加密机制的？**

**过程：**

交换密钥环节使用公开密钥加密，之后的建立通信交换报文阶段则用共享密钥加密的方式。（公钥加密比共享密钥**加密更复杂**，因此**通信交换报文阶段则使用共享密钥加密**）

见HTTPS的工作原理部分

****

#### 3.完整性保护

认证，使用数字证书的验证完成。同样可以看HTTPS工作原理部分

****

**SSL 提供报文摘要功能来进行完整性保护**

虽然在HTTP中也提供了MD5报文摘要，但是不安全。当HTTP内容被篡改后，重新计算MD5值，通信接收方就意识不到报文被篡改了。



而HTTPS的报文摘要更安全，因为**它结合了加密和认证两个操作**！如果加密的报文被篡改，也**很难重新计算报文摘要**，因为无法轻易获取明文（**只有获取明文才能重新计算报文摘要**）

****





****



### HTTPS的工作原理 {why?这类问题中，基本都含有原理性问题}



1.**对称加密**：加密与解密使用的是同样的密钥，所以速度快，但由于需要将密钥在网络传输，**所以安全性不高**

2.**非对称加密**:加密使用了一对密钥，公钥与私钥，所以安全性高，**但加密与解密速度慢**



**HTTPS加密、解密以及验证流程图**

![](C:\Users\fucker\Pictures\http.20.png)

**HTTPS加密的本质：对称加密的密钥，使用非对称加密的公钥形式传输**



**文字描述：**

1. 服务器上面有SSL数字证书，其中SSL证书中公钥。而且**服务器有这个公钥对应的私钥**。

2. 浏览器向服务器发送请求

3. 服务器给浏览器返回的**响应会携带“数字证书”**

4. 浏览器会开始**解析数字证书，并验证其中的公钥**

5. 如果**验证通过则生成一个随机码，这个随机码也就是后续的对称加密的密钥{这个密钥很重要}**。如果验证不通过，**浏览器显示https警告**。

6. 浏览器使用**公钥加密随机码{也就是非对称加密的密钥，一般用RSA加密}**。浏览器在**传输对称加密的密钥及其之前阶段没有进行解密（没有密钥，不能解密）！！！**

7. 消息体产生后，对它的摘要进行MD5(或者SHA1)算法加密，此时就得到了RSA签名，并发送给服务器端

8. 服务器使用**(RSA)私钥对公钥加密后的随机码{也就是非对称加密的密钥}进行解密，得到随机码{密钥}**。这里的**私钥解密是关键**。

9. 然后服务器使用**随机码{对称加密的密钥}来进行对称加密传输数据**

10. 浏览器使用**随机码{对称加密的密钥}来进行对称加密后的数据的解密**，得到数据

   。。。。。。。。。。。

   之后浏览器和服务器就用这个随机码进行着一次次的加密和解密

****

### HTTPS的缺点

- 因为需要进行加密解密等过程，因此速度会更慢
- 证书授权需要费用颇高

****

# HTTP/1.1新特性  {版本比较，重点。--主要是增加了长连接和管道化}



1. 默认是长连接

2. 支持流水线/管线化

3. 支持同时打开多个TCP连接

4. **支持虚拟主机**

   HTTP/1.1 使用虚拟主机技术，使得一台服务器拥有多个域名，并且在逻辑上可以看成多个服务器。

5. 新增状态码100

   100 （继续） 请求者应当继续提出请求。 服务器返回此代码表示已收到请求的第一部分，正在等待其余部分

   

6. 断点续传/支持分块传输编码

   **实际上就是利用HTTP消息头使用分块传输编码，将实体主体分块传输。**

   Chunked Transfer Encoding，可以把数据分割成多块，让浏览器逐步显示页面

7. 新增缓存处理指令max-age 并设为默认

****

# GET与POST比较： 作用，参数，安全性，幂等性，可缓存

| 比较                       | GET                                                          | POST                                                         |
| -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 作用                       | 用于获取资源                                                 | 用于传输实体主体/提交数据                                    |
| 参数                       | 字符串形式出现在URL中，而URL只支持ASCII码。因此GET参数存在中文就需要先进行编码。**且参数长度受到URL限制不能超过2048字符**{这个2048是IE8的对于URL的限制，不同浏览器，甚至不同版本对URL的限制都不同。例如IE11貌似就是2047} | 存储在实体主体中。**不能因为POST参数存储在实体中就认为它的安全性更高，因为照样有一些抓包工具（Fiddler）可查看**，还是用HTTPS吧。**参数最大是8mb** |
| 安全性{准确的说是无副作用} | GET方法是安全的。**安全的HTTP方法不会改变服务器状态，也就是说它只是可读的** | POST是不安全的。因为POST方式是传送实体主体内容。上传后，**服务器可能把这个数据存储到数据库中，因此服务器的状态也就改变了** |
| 幂等性                     | 所有安全的方法都是幂等的。**因为幂等方法执行一次和多次的效果是一样的（也就是没有改变服务器状态）**因此GET方法是幂等的 | POST方法自然也就是不幂等的。**因为上传数据给服务器后，服务器的状态改变了。执行多次的结果自然也就和一次不一样** |
| 可缓存                     | **请求报文的HTTP方法本身是可缓存的**。包括GET和HEAD          | POST在多数情况下不可缓存。        响应报文的首部字段Cache-Conntrol没有指定，就不进行缓存。响应报文的状态码是可以缓存的，包括：200，203,204,206,300,301,404,405,410,414,301 |

**还有一点：**

- 在使用XMLHttpRequest 中GET 方法时， Header 和 Data 会一起发送。

- 而使用 POST 方法时，浏览器会先发送 Header 再发送 Data。但并不是所有浏览器会这么做，例如火狐就不会。

   

至于什么是XMLHttpRequest,回忆一下Ajax

> XMLHttpRequest 是一个 API，它为客户端提供了在客户端和服务器之间传输数据的功能。它提供了一个通过 URL 来获取数据的简单方式，并且不会使整个页面刷新。这使得网页只更新一部分页面而不会打扰到用户。XMLHttpRequest 在 AJAX 中被大量使用。

类似于HTTP的管道化，一次性发多个请求/响应，再慢慢处理



****

**下面是解惑＋补充：**

****

关于安全性和幂等性。。。。这个真的有点坑！实际上一个GET和POST差别不会特别大!还有安全性和幂等性的关系来自何处？

这个坑有点深!

这里的安全性和通常理解的安全性不同！

这里的安全指的是RFC7231中定义的HTTP方法的性质----Safe -安全

更准确的说是，不引起服务器端任何状态的变化就是无害的{准确的说是无副作用}。引入这个概念应该是为了方便网络爬虫和缓存，以免调用或缓存某些不安全的方法时在引起某些意外的后果。

而且这个也只是规范，甚至是规范相对应服务器端来说的，GET方法中参数在URL中泄露**是对于客户端的不安全**，**因为是在客户端出现了泄露**。

对于规范的实现也并不能保证安全，更别说整体的，大范围的安全了。



RFC7231中的方法的三大特性：**安全，幂等，可缓存**

其中的三大特性一直在强调：**协议不等于实现**

协议规定幂等/不幂等，可缓存/不缓存 不等于现实实现时幂等或缓存。



例如：江湖传说中，百度贴吧某次将GET方法被实现为有副作用时，出现了一个很大的bug---使用GET请求可以修改管理员权限

而将POST实现为幂等，很多时候可以上前后的交互更流畅



知乎的这个帖子写得非常nice

https://www.zhihu.com/question/28586791

****







****

# HTTP/2.0

**现在实际应用的HTTP/2.0都是基于HTTPS基础之上的**

## HTTP/1.x的缺陷

缺陷：**HTTP/1.X的简单实现的背后是性能的牺牲**

1. 客户端需要使用**多个连接才能实现并发和缩短延迟**

2. 不会**压缩请求和响应头的首部**，有了不必要的网络流量开销

3. 不支持**有效的资源优先级**，致使TCP连接的利用率低下

   *分道机制？？？*

## HTTP1.1和HTTP2.0的区别    面试题

两者最主要的区别就是HTTP2**解决了线头阻塞问题！**其中的最重要的改动是：**多路复用**

### **1.多路复用**:

允许通过单一的HTTP/2连接**发起的多重的请求-响应消息**，合并为一个的优化将不再适应。

{在HTTP/1.1中就是将多个请求合并为一个请求，然后一个TCP连接进行处理}

主要**借助着二进制分帧层中的标识符进行区分，实现链路的复用**。

****

而所有性能的核心是**新的二进制分帧层**{不再以文本格式来传输了}

### 2.二进制分帧层

将所有传输信息**分割成消息和帧**，并**采用了二进制格式的编码**。每个帧中都**含有数据和标识符**。

二进制分帧层在不修改请求方法和语义的基础上，**重新设计了编码机制**

**真正的用一个TCP连接来处理（一个客户端的）多个HTTP请求！**



在通信过程中，**只会有一个 TCP 连接存在，它承载了任意数量的双向数据流**（Stream）。**而之前是多个TCP连接来承载数据流**。

- 一个数据流（Stream）都有一个唯一标识符和可选的优先级信息，用于承载双向信息。
- 消息（Message）是与逻辑请求或响应对应的完整的一系列帧。
- 帧（Frame）是最小的通信单位，来自不同数据流的帧可以交错发送，然后再根据每个帧头的数据流标识符重新组装。

二进制分帧层就像是用一条**高速公路**{一个TCP连接}，设定两个方向，然后让数据分解成帧这个最小的通信单位来传输，**就像是车行驶在高速公路上**。而**消息就像是多辆车组成的车队**，即是整体又是个体。**一个车队或者多个车队就组成了数据流**。

****

**重点：二进制分帧是如何做的？分成帧的数据是如何传输的？**

总之，HTTP/2.0将数据分解成**相互独立的**二进制编码帧进行**互不影响地交互传输**，每个帧对应着**特定数据流**中的**特定消息**，最后再在对端根据**帧头中的流标识符**把它们**重新组装**。  ----这即是**多路复用的实现原理**又是**二进制分帧的具体应用**



**所有帧和流都在一个连接内复用，不必再进行多次连接了**。

****

### 3.服务端推送

HTTP/2.0 在客户端请求一个资源时，**会把相关的资源一起发送给客户端**，客户端就**不需要再次发起请求**了。例如客户端请求 page.html 页面，服务端就把 script.js 和 style.css 等与之相关的资源一起发给客户端。

**推送式交互中服务器可以对客户端的一个请求发送多个响应！**而不是传统C/S架构中的**一问一答式**

这种**主动推送额外资源 **的方式在实际应用中很有效！可以**有效减少额外的延迟时间**，因为**服务器可以知道客户端下一步要请求什么资源**！

****

### 4.首部压缩

**为什么要有首部压缩？**

HTTP/1.1 的首部带有大量信息，而且每次都要重复发送。



HTTP/2.0 要求**客户端和服务器同时维护和更新**一个**包含之前见过的首部字段表**，从而**避免了重复传输**。这个首部字段表**也是key-value结构的**，发生**变化则更新传输**，否则不传输。这样相当于**首次建立连接时全量传输之后增量更新传输**。

不仅如此，HTTP/2.0 也使用 Huffman 编码对首部字段进行压缩。

****

# HTTP优化方案

1. **TCP连接复用：**

   **TCP连接复用：将多个客户端的HTTP请求，复用到一个服务器端TCP连接上。**

   **HTTP复用：一个客户端的多个HTTP请求，通过一个TCP连接进行处理。**

   **前者是负载均衡设备的独特功能，而后者是HTTP/1.1所支持的新功能**

2. **内容缓存:**

   将客户端经常用到的内容进行缓存起来，那么客户端就可以直接在内存/磁盘中获取相应的数据，而不用去找源服务器了 。

   **具体的见HTTP缓存部分**

3. **压缩：将文本数据进行压缩，减少带宽**

4. SSL加速：用SSL协议对HTTP协议进行加密，**在通道内加密并加速**

5. **TCP缓冲：**使用该技术，可以**提高服务器响应时间和处理效率**，**减少由于通信链路问题给服务器造成的连接负担**。

   这是管道化？？？











# 散沙一样的知识，如何吸收？？？

**细嚼慢咽，慢慢琢磨，让自己理解**





**结构化思维&跳跃性思维**



**读一本书，手旁要有5本资料**