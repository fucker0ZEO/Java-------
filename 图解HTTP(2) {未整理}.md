# 图解HTTP(2)



# XSS攻击{重点}--脚本监听盗号



XSS攻击又被称为跨站脚本攻击



**流程图：**

![](C:\Users\fucker\Pictures\http.21.PNG)





**Cookie中有会话ID，接着就可以直接会话劫持**

![](C:\Users\fucker\Pictures\http.22.PNG)



![](C:\Users\fucker\Pictures\http.23.PNG)

****



# 不正确的错误消息处理

![](C:\Users\fucker\Pictures\http.24.PNG)

**返回的错误信息，不要显示的太完整！**

还有各类系统软件的错误信息，**要好好处理，不要抛出到页面上**

![](C:\Users\fucker\Pictures\http.25.PNG)



{黑客通过这样的错误信息，一样可以得到有用的信息}



****

# 会话劫持

![](C:\Users\fucker\Pictures\http.26.PNG)

XSS+会话劫持，简直酸爽

**勘误：要明确的一点不是会话ID中有Cookie，而是Cookie中有会话ID**

**会话ID是管理认证{会话}状态的关键，有了Cookie可能就有了会话ID**

![](C:\Users\fucker\Pictures\http.27.PNG)



****

# 会话固定攻击

![](C:\Users\fucker\Pictures\http.28.PNG)

**前2年很有名的QQ链接诈骗，就和它类似吧(?)。先发一个链接，提示要输入QQ号和密码，然后QQ认证后，攻击者也获得了密码 **



这个比单纯的辣鸡链接 ，然后输入错误密码/账户，得到的用户信息靠谱多了。

哪个还要慢慢甄别用户密码账户，这个直接就是能正确登录。。。


区别QQ链接哪个是得到密码，这个是得到会话ID。每次会话的ID都会变，但是密码是不变的！

****

# CSRF攻击{重点}---借刀杀人



![](C:\Users\fucker\Pictures\http.28.PNG)



**CSRF攻击，中文是跨站点请求伪造**----借刀杀人

**它是准备好要执行的代码，然后等待着用户登录，登录的用户就会用自己的身份替攻击者执行已经写好的代码，也就是说完成了借刀杀人**

# 

# 密码破解





![](C:\Users\fucker\Pictures\http.29.PNG)



![](C:\Users\fucker\Pictures\http.30.PNG)



彩虹表和类推+穷举法 ·字典攻击{类似于a先求出它的加密形式，b求出加密形式。。。然后整合起来}

****

# Dos和DDOS攻击{重点}--ping包攻击的高级版

发送无意义次的N多次请求，来让服务器瘫痪

当然也有升级版，无限次攻击安全漏洞

上面这些是Dos攻击，而DDos攻击就是多台计算机来发请求，升级版。第一个D代表分布式，后面的就是Dos



![](C:\Users\fucker\Pictures\http.31.PNG)





