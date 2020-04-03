# Linux常用命令(2)



# 实用指令--搜索查找类

## 从指定目录向下递归地遍历其各个子目录，将满足文件的文件或者目录显示在终端 `find`



**基本语法：**

find [搜索范围] [选项]

搜索范围指的就是在哪个目录下查找

**选项说明**：

| 选项            | 功能                               |
| --------------- | ---------------------------------- |
| -name<文件名>   | 按照指定的文件名查找模式查找文件   |
| -user<用户名>   | 查找属于指定用户名所有文件         |
| -size<文件大小> | 根目录下按照指定的文件大小查找文件 |



**应用实例：**

案例1：按文件名：根据名称查找/home **目录下的所有hello3.txt文件**

使用指令 `find /home -name hello3.txt`

表示在/home目录下，查找名字为 `hello3.txt`文件



```shell
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  c.txt  dir2  hello3.txt  mochou5  mydate.txt  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home# find /home -name hello.txt
root@LAPTOP-UN694I4M:/home# find /home -name hello3.txt
/home/hello3.txt
/home/zwj/hello3.txt
root@LAPTOP-UN694I4M:/home# 
```

可以看出里面有2个 `hello3.txt`文件，一共是/home下，一个是/home目录下的子目录zwj目录下的`hello3.txt`文件



****

案例2： 按拥有者：查找 /opt目录下，用户名称为root的文件

使用指令 `find /opt -user root`,查找属于指定用户名所有文件



```shell
root@LAPTOP-UN694I4M:/home# find /opt -user root
/opt
root@LAPTOP-UN694I4M:/home# 
```



****

案例3： 查找整个操作系统(用WSL则会查找到W10下的文件本质上它们是一个操作系统)下大于20m的文件(+n 大于 -n小于  n等于)

```shell
mochou5@LAPTOP-UN694I4M:~$ find / -size +20M
find: ‘/etc/polkit-1/localauthority’: 权限不够
find: ‘/etc/ssl/private’: 权限不够
find: ‘/mnt/c/$Recycle.Bin/S-1-5-18’: 权限不够
find: ‘/mnt/c/$Recycle.Bin/S-1-5-21-1145459714-2005818636-2477645967-500’: 权限不够
find: ‘/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1000’: 权限不够
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$R03IYPL/PotPlayerSetup64.exe
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$R1NICHO/iBiliPlayer-bili.apk
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$R4Y6JQC/Evernote_6.18.14.753.exe
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$R5JSJFX.zip
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$R6447HO.exe
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$RCFG3KS.downloading
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$RFUN1JX.pdf
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$RG85UPU.downloading
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$RLYH3GI.avi
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$RRR028V/API文档
。。。。。。。。。。。。。
```

后面的都是windows系统下的。。。

直接`ctrl+c` 强制退出。。

这里是大于20MB，因此是 `find / -size +20MB`，如果是小于20MB，则是`find / -size -20MB`;如果是等于20MB就是 直接`20mb`

因为1mb =1024kb,因此也可以使用kb的形式来查找

使用指令 `find / -size +20480k`  这里的k是小写



```shell
root@LAPTOP-UN694I4M:/# find / -size +20480k
find: ‘/mnt/c/$Recycle.Bin/S-1-5-18’: 权限不够
find: ‘/mnt/c/$Recycle.Bin/S-1-5-21-1145459714-2005818636-2477645967-500’: 权限不够
find: ‘/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1000’: 权限不够
/mnt/c/$Recycle.Bin/S-1-5-21-4093857167-732970772-1568279726-1001/$R03IYPL/PotPlayerSetup64.exe
```





查询 `/home` 目录下，所有.txt的文件

使用指令 `find /home -name *.txt`

```shell
 root@LAPTOP-UN694I4M:/# find / -name * .txt
find: paths must precede expression: `boot'
find: possible unquoted pattern after predicate `-name'?
root@LAPTOP-UN694I4M:/# 
```

find:路径必须在表达式之前



**在*前面加\转义即可**

因此使用指令 `find /home -name \*.txt`

`*`是通配符 ，代表任意。因此 `*.txt`就表示任意txt文件

前面的 `fin /home -name `是之前说过的在指定范围内，**根据文件名查找文件路径**

```shell
root@LAPTOP-UN694I4M:/# find /home -name \*.txt
/home/a.txt
/home/aa.txt
/home/c.txt
/home/hello3.txt
/home/mydate.txt
/home/zwj/aaa.txt
/home/zwj/hello3.txt
/home/zwj/pig.txt
/home/看这里.txt
root@LAPTOP-UN694I4M:/# 
```



****

## 可以快速定位文件路径：`locate`

locate 指令利用系统中自带的**所有文件名称及路径的locate 数据库**实现快速定位给定的文件。

Locate 指令**无需遍历整个文件系统{而是搜索一共数据库 `/var/lib/mlocate/mlocate.d`}**，查询速度较快。为了保证查询结果的准确度，管理员必须定期更新 locate 时刻

**使用的locate数据库查找，而非遍历文件系统查找**

**locate命令要比find -name快得多，原因在于它不搜索具体目录**

因此在于用`whereis` 和  `locate`查找文件时，有时会找到已被删除的文件，或者刚刚建立的文件却无法查找到，原因就是**数据库文件没有被更新**，为了避免这种情况，，可以在使用 `locate`指令时，先使用 `updatedb`更新数据库，**手动更新数据库**



locate数据库中含有本地所有文件信息，Linux系统自动创建这个数据库，并且每天自动更新一次



**基本语法：**

locate 搜索文件



**特别说明：**

由于locate 指令基于数据库进行查询，所以第一次运行前必须使用`updatedb`指令更新locate数据库



**应用实例：**

查找hello3.txt文件

```shell
root@LAPTOP-UN694I4M:/# updatedb
root@LAPTOP-UN694I4M:/# locate hello3.txt
/home/hello3.txt
/home/zwj/hello3.txt
root@LAPTOP-UN694I4M:/# 
```



****

## 过滤查找和管道符号：`grep` 和`|`



刚才我们都是在系统内部查找文件的路径，有时候**我们有需求是在一个文件内部查找关键字**

grep 过滤查找 

 管道符`|`，表示将前一个命令的处理结果{返回值}输出传递给后面的命令处理。**也就相当于将两个指令通过一共管道指令连起来**



**基本语法：**

grep  [选项] 查找内容 源文件



**常用选项：**

| 选项 | 功能             |
| ---- | ---------------- |
| -n   | 显示匹配行及行号 |
| -i   | 忽略字母大小写   |



**应用实例**

案例1：在hello4.txt文件中，查找`yes` 所在行，并且显示行号

先将/home下的hello3.txt重命名为hello4.txt文件，再写入 `yes`

```shell
root@LAPTOP-UN694I4M:/# nano /home/hello3.txt
root@LAPTOP-UN694I4M:/# cd /home
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  c.txt  dir2  hello3.txt  mochou5  mydate.txt  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home# mv hello3.txt hello4.txt
root@LAPTOP-UN694I4M:/home# nano hello4.txt
root@LAPTOP-UN694I4M:/home# 
```

重命名**当前目录下的文件**需要的指令 `mv 原文件名 新文件名`

因此使用指令 `mv hello3.txt hello4.txt `



然后使用nano编辑器加上`yes`



然后查找 `yes`文件

```shell
root@LAPTOP-UN694I4M:/home# grep -n "yes" hello4.txt
15:yes
root@LAPTOP-UN694I4M:/home#  
```



添加 `yes`后的情况，**实际上是否有“”,在这里无影响**

```shell
root@LAPTOP-UN694I4M:/home# grep -n yes hello4.txt
11:yes
12:yes
18:yes
root@LAPTOP-UN694I4M:/home#
```



使用指令 `grep -n yes hello4.txt`

它表示在hello4.txt文件中查找 `yes`这个字符串，**并显示行号**





****

**另外一种显示方式**

后面在加上了2行`yes`

这里使用了 `|`和cat指令，通过管道符连接了2个指令。

`cat`指令浏览hello4.txt的结果交给`grep`指令处理

```shell
root@LAPTOP-UN694I4M:/home# cat hello4.txt | grep  yes
yes
root@LAPTOP-UN694I4M:/home# cat hello4.txt | grep -n  yes
15:yes
root@LAPTOP-UN694I4M:/home# nano hello4.txt
root@LAPTOP-UN694I4M:/home# cat hello4.txt | grep -n  yes
11:yes
12:yes
18:yes
root@LAPTOP-UN694I4M:/home# grep -n "yes" hello4.txt
11:yes
12:yes
18:yes
root@LAPTOP-UN694I4M:/home#
```

****

**不区分大小写**

再加上一个 `YES`

两种方式都展现一下

```shell
root@LAPTOP-UN694I4M:/home# nano hello4.txt
root@LAPTOP-UN694I4M:/home# grep -ni yes hello4.txt
11:yes
12:yes
18:yes
19:YES
root@LAPTOP-UN694I4M:/home# cat hello4.txt |grep -ni yes
11:yes
12:yes
18:yes
19:YES
root@LAPTOP-UN694I4M:/home#
```

**总结：推荐使用管道符方式，这样既可以减少记命令，可以通过组合命令来解决问题**



****

# 实用指令--压缩和解压类 

## 压缩文件和解压文件{方式1}： `gizp`和 `gunzip`

`gzip` 用于压缩文件， `gunzip`  用于解压的



**基本语法：**

| 用法                                      | 功能描述          |
| ----------------------------------------- | ----------------- |
| gizp 文件                                 | 压缩文件为*gz文件 |
| gunzip 文件.gz{文件.gz是压缩后的文件格式} | 解压缩文件命令    |





**应用实例：**

案例1：gizp压缩，将/home下的hello4.txt进行压缩

使用指令 `gzip hello4.txt`，将hello4.txt文件将进行了压缩。压缩成的文件是 `hello4.txt.gz`



```shell
root@LAPTOP-UN694I4M:/home# gzip hello4.txt
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  c.txt  dir2  hello4.txt.gz  mochou5  mydate.txt  tiger  zwj  看这里.txt
```

`gizp`和windows中平常压缩不一样的是，**这里是直接对源文件压缩**

在Linux中，**压缩文件的文件名，是在源文件的文件名后加上`.gz`**



****

案例2：gunzip解压，将/home下的hello.txt.gz文件进行解压

使用指令 `gunzip hello4.txt.gz`，对文件 `hello4.txt.gz`进行了解压

```shell
root@LAPTOP-UN694I4M:/home# gunzip hello4.txt.gz
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  c.txt  dir2  hello4.txt  mochou5  mydate.txt  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home#
```



****



## 压缩文件和解压文件{方式2}：`zip`和 `unzip`

`zip`用于压缩文件，而 `unzip`用于解压文件

**这个在项目打包发布中很有用的**



**基本语法：**

| 用法                              | 功能描述                      |
| --------------------------------- | ----------------------------- |
| zip [选项] XXX.zip 将要压缩的内容 | 将内容被压缩成XXX.zip         |
| unzip [选项] XXX.zip              | 将XXX.zip文件解压到默认目录下 |



**zip常用选项：**

-r: 递归压缩，即压缩目录



**unzip常用选项：**

-d<目录>：指令解压后文件存放的目录



**应用实例：**

案例1：将/home/tiger下的 所有文件进行压缩成**mypackage.zip**

```shell
root@LAPTOP-UN694I4M:/# zip -r mypackage.zip /home/tiger

Command 'zip' not found, but can be installed with:

apt install zip
```

**这里需要先安装zip,才能进行压缩**

```shell
root@LAPTOP-UN694I4M:/#  apt install zip
正在读取软件包列表... 完成
正在分析软件包的依赖关系树
正在读取状态信息... 完成
下列软件包是自动安装的并且现在不需要了：
  libdumbnet1
使用'apt autoremove'来卸载它(它们)。
将会同时安装下列软件：
  unzip
下列【新】软件包将被安装：
  unzip zip
升级了 0 个软件包，新安装了 2 个软件包，要卸载 0 个软件包，有 2 个软件包未被升级。

。。。。。。省略。。。。。。。。。。。
```



开始压缩

```shell
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  c.txt  dir2  hello4.txt  mochou5  mydate.txt  pig.txt  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home# zip -r mypackage.zip tiger
  adding: tiger/ (stored 0%)
  adding: tiger/pig.txt (deflated 35%)
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  c.txt  dir2  hello4.txt  mochou5  mydate.txt  mypackage.zip  pig.txt  tiger  zwj  看这里.txt
```



使用 `zip`进行压缩，和windows一样，**是对副本进行压缩，压缩完后源文件还在**





****



案例2：将mypackage.zip解压到/home/animal目录下

```shell
oot@LAPTOP-UN694I4M:/home# unzip -d animal mypackage.zip
Archive:  mypackage.zip
   creating: animal/tiger/
  inflating: animal/tiger/pig.txt
root@LAPTOP-UN694I4M:/home# cd  animal
root@LAPTOP-UN694I4M:/home/animal# ls
tiger
root@LAPTOP-UN694I4M:/home/animal# 
```



和 `zip`一样，**`unzip`也是解压的压缩文件的副本，源文件没有变**





****

## 打包/解包指令：`tar`   {三个中最常用--`tar -zcvf 压缩后的文件名 要压缩的 内容`}

tar 指令 是打包指令，最后打包后的文件是 .tar.gz 的文件



**基本语法：**和zip类似

| 用法                              | 功能描述                                                     |
| --------------------------------- | ------------------------------------------------------------ |
| tar [选项] XXX.tar.gz  打包的内容 | **将打包的内容压缩成名为XXX.tar.gz的文件**。其中压缩后的文件格式是.tar.gz |



**选项说明：**

| 选项 | 功能               |
| ---- | ------------------ |
| -c   | 产生.tar打包文件   |
| -v   | 显示详细信息       |
| -f   | 指定压缩后的文件名 |
| -z   | 打包同时压缩       |
| -x   | 解包.tar文件       |

**压缩式要带同时带前4个参数{-zcvf}，解压只要用x替换掉c,带四个参数{-zxcf}**

`-zcvf`是固定顺序

**-f一定要写在最后面，因为后面跟的是文件或者目录名，或者-f单独写**





```shell
root@LAPTOP-UN694I4M:/home# tar -cfvz a3.tar.gz aa.txt
tar: a3.tar.gz：无法 stat: 没有那个文件或目录
tar: 由于前次错误，将以上次的错误状态退出
root@LAPTOP-UN694I4M:/home# tar -zcvf a3.tar.gz aa.txt
aa.txt
root@LAPTOP-UN694I4M:/home# ls
a3.tar.gz  animal    a.txt  dir2        mochou5     pig.txt  vz   看这里.txt
aa.txt     a.tar.gz  c.txt  hello4.txt  mydate.txt  tiger    zwj
root@LAPTOP-UN694I4M:/home#
```



**应用实例：**

案例 1:	压缩多个文件，将  /home/aa.txt 和  /home/a.txt 压缩成	a.tar.gz

**压缩多个文件，和压缩一个是一样的。因为压缩内容中并没有指定有多少文件**



`tar -zcvf a.tar.gz a.txt aa.txt`中，`-zcvf`是固定参数，`a.tar.gz`是打包后的文件名，而 `a.txt aa.txt`是要打包的内容{这里的内容是两个文件}



```shell
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  c.txt  dir2  hello4.txt  mochou5  mydate.txt  pig.txt  tiger  vz  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home# tar -zcvf a.tar.gz a.txt aa.txt
a.txt
aa.txt
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.tar.gz  a.txt  c.txt  dir2  hello4.txt  mochou5  mydate.txt  pig.txt  tiger  vz  zwj  看这里.txt
```



****

案例 2:	将/home 的文件夹 压缩成 myhome.tar.gz

**一次性打包一个目录下的所有文件**

```
root@LAPTOP-UN694I4M:/home# ls
a3.tar.gz  animal    a.txt  dir2        mochou5     pig.txt  vz   看这里.txt
aa.txt     a.tar.gz  c.txt  hello4.txt  mydate.txt  tiger    zwj
root@LAPTOP-UN694I4M:/home# tar -zcvf myhome.tar.gz /home
tar: 从成员名中删除开头的“/”
/home/
/home/a.tar.gz
/home/a.txt
/home/a3.tar.gz
/home/aa.txt
/home/animal/
/home/animal/tiger/
/home/animal/tiger/pig.txt
/home/c.txt
/home/dir2
/home/hello4.txt
/home/mochou5/
/home/mochou5/.bash_history
/home/mochou5/.bash_logout
/home/mochou5/.bashrc
/home/mochou5/.local/
/home/mochou5/.local/share/
/home/mochou5/.local/share/nano/
/home/mochou5/.profile
/home/mochou5/.sudo_as_admin_successful
/home/mochou5/.viminfo
/home/mydate.txt
/home/myhome.tar.gz
/home/pig.txt
/home/tiger/
/home/tiger/pig.txt
/home/vz
/home/zwj/
/home/zwj/aaa.txt
/home/zwj/hello3.txt
/home/zwj/pig.txt
/home/看这里.txt
root@LAPTOP-UN694I4M:/home# ls
a3.tar.gz  animal    a.txt  dir2        mochou5     myhome.tar.gz  tiger  zwj
aa.txt     a.tar.gz  c.txt  hello4.txt  mydate.txt  pig.txt        vz     看这里.txt
root@LAPTOP-UN694I4M:/home#   
```



****



案例 3:	将  a.tar.gz	解压到当前目录

使用指令 `tar -zxvf a.tar.gz`  

前面 `tar -zxvf`代表解压，后面的 `a.tar.gz`代表要解压的文件名

解压到当前目录下，不用指定路径。和 `unzip`类似

```shell
root@LAPTOP-UN694I4M:/home# tar -zxvf a.tar.gz
a.txt
aa.txt
root@LAPTOP-UN694I4M:/home# 
```



****





案 例 4: 将 myhome.tar.gz	解压到 /opt/ 目录下 





```shell
root@LAPTOP-UN694I4M:/home# tar -zxvf myhome.tar.gz /opt/tmp
tar: /opt/tmp：归档中找不到
tar: 由于前次错误，将以上次的错误状态退出
```

 

这里的参数有问题，并不是 `解压指令 要解压的文件 要解压到的目录`

而是  `解压指令 要解压的文件 -C 要解压的目录` 这里的c是大写的 `C`

`-C`相当于 `-Change`,指定路径



因此指令为 `tar -zxvf myhome.tar.gz -C /opt/tmp`

```shell
root@LAPTOP-UN694I4M:/home# tar -zxvf myhome.tar.gz -C /opt/tmp
home/
home/a.tar.gz
home/a.txt
home/a3.tar.gz
home/aa.txt
home/animal/
home/animal/tiger/
home/animal/tiger/pig.txt
home/c.txt
home/dir2
home/hello4.txt
home/mochou5/
home/mochou5/.bash_history
home/mochou5/.bash_logout
home/mochou5/.bashrc
home/mochou5/.local/
home/mochou5/.local/share/
home/mochou5/.local/share/nano/
home/mochou5/.profile
home/mochou5/.sudo_as_admin_successful
home/mochou5/.viminfo
home/mydate.txt
home/myhome.tar.gz
home/pig.txt
home/tiger/
home/tiger/pig.txt
home/vz
home/zwj/
home/zwj/aaa.txt
home/zwj/hello3.txt
home/zwj/pig.txt
home/看这里.txt
root@LAPTOP-UN694I4M:/home# 
```



**指定解压到的那个目录，事先要存在才能成功，否则会报错。**

/opt/tmp是存在的

```shell
root@LAPTOP-UN694I4M:/home# cd /opt
root@LAPTOP-UN694I4M:/opt# ls
test  tmp
```



****



# 实用指令--组管理和权限管理(难点，重点)

## Linux组的介绍

在 linux 中的每个用户必须属于一个组，不能独立于组外。在 linux 中每个文件有所有者、所在组、其它组的概念。

**文件的四大属性**：**所有者，所在组，大小，文件名**

1) 所有者 ：*这个文件是谁的？*

2) 所在组 ： *这个文件在哪个组？*

3) 其它组 : *除去所在组的所有组就是其他组*

4)改变用户所在的组

![](C:\Users\fucker\Pictures\Linux19.png)





**文件/目录所有者**

一般为文件的创建者,谁创建了该文件，就自然的成为该文件的所有者



****

## 查看文件/目录 所有者 指令： `ls -ahl`



**应用实例：**

创建一个组police,再创建一个用户 `tom`,将 `tom`放在police 组，然后使用 `tom`来创建一个文件 `ok.txt`，看看情况如何



第1步，创建组police,使用指令 `groupadd police`

第2步，创建用户 `tom` 并放在 `police`组中。使用指令 `useradd -g police tom` 。类似于  `创建用户 武当 张无忌`。`useradd -g`是创建指令，`police`是对应的组，`tom`是用户名。这里没有指定创建用户的目录，**因此默认为当前目录下**

第3步，给 `tom`用户一个密码，并登入，用该用户在/home目录下创建一个 文件 `ok.txt`。分配密码，使用指令 `passwd tom`,切换登录，用 `su tom`

创建文件，使用 `touch ok.txt`

而且这个

`sudo` 允许一般用户使用 root 可执行的命令，不过只有在 /etc/sudoers 配置文件中添加的用户才能使用该指令。

```shell
root@LAPTOP-UN694I4M:/home/mochou5# groupadd police
root@LAPTOP-UN694I4M:/home/mochou5# useradd -g police tom
root@LAPTOP-UN694I4M:/home/mochou5# passwd tom
输入新的 UNIX 密码：
重新输入新的 UNIX 密码：
passwd: password updated successfully
root@LAPTOP-UN694I4M:/home/mochou5# su tom
$ cd /home
$ touch ok.txt
touch: 无法创建'ok.txt': 权限不够
$ sudo touch ok.txt
[sudo] tom 的密码：
tom 不在 sudoers 文件中。此事将被报告。
$ ls
a3.tar.gz  animal    a.txt  dir2        mochou5     myhome.tar.gz  tiger  zwj
aa.txt     a.tar.gz  c.txt  hello4.txt  mydate.txt  pig.txt        vz     看这里.txt
```

额。。。这里遇见了 一点小问题，创建的用户权限不够！

我们需要**给它提升权限，让其能够用管理员权限**



****

## 修改/etc/sudoers 文件，提升用户tom的权限



**首先我们找到sudoers文件的位置 **

使用 locate数据库查找

```shell
$ locate sudoers
/etc/sudoers
/etc/sudoers.d
/etc/sudoers.d/README
/mnt/c/Users/fucker/AppData/Local/Packages/CanonicalGroupLimited.Ubuntu16.04onWindows_79rhkp1fndgsc/LocalState/rootfs/etc/sudoers
。。。。分隔。。。。。。。。
```

/mnt下的文件都是Windows文件了，因此只有第一个满足



**然后需要切换到root用户，修改/etc/sudoers文件来提权**

之前也有普通用户试过了，但是编辑文件时提示权限不够

因此使用root用户来修改



打开文件后，有点懵，看不懂。。。

```shell
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
。。。。。。省略符。。。。。。。。。
```



搜索了一下，参考了这篇博客

https://blog.csdn.net/qq_38333529/article/details/79608224

 

同时参考了一下谷歌翻译

User privilege specification

翻译：用户权限规范

****

Members of the admin group may gain root privileges

翻译：管理组的成员可以获得root权限

****

Allow members of group sudo to execute any command

翻译：允许组 sudo 的成员执行任何命令



结合博客，大致意思应该是在 *用户权限规范*  下面进行增加用户的操作

也就是这样：

```shell
# User privilege specification
root    ALL=(ALL:ALL) ALL

tom     ALL=(ALL:ALL) ALL
```

选择了最省事的方式

****

然后又重新来创建文件

```shell
root@LAPTOP-UN694I4M:/etc# su tom
$ cd /home
$ sudo touch ok.txt
[sudo] tom 的密码：
$ ls -al
总用量 44
drwxr-xr-x 1 root    root     4096 2月  12 13:00 .
drwxr-xr-x 1 root    root     4096 2月  11 21:20 ..
-rw-r--r-- 1 root    root      292 2月  11 21:50 a3.tar.gz
-rw-r--r-- 1 root    root      465 2月  10 20:48 aa.txt
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 root    root      383 2月  11 21:48 a.tar.gz
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rw-r--r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  11 14:39 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root     8619 2月  11 21:56 myhome.tar.gz
-rw-r--r-- 1 root    root        0 2月  12 13:00 ok.txt
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
-rw-r--r-- 1 root    root    10240 2月  11 21:50 vz
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
```

可以看到/home目录下有了 `ok.txt`

```shell
-rw-r--r-- 1 root    root        0 2月  12 13:00 ok.txt
```

因为是借用的root权限，因此创建人是root???

****

使用其他管理员账户演示一下创建文件后，查看时会出现具体的创建者

这里创建的文件是hello5.txt

```shell
mochou5@LAPTOP-UN694I4M:/home$ cd mochou5
mochou5@LAPTOP-UN694I4M:~$ touch hello5.txt
mochou5@LAPTOP-UN694I4M:~$ ls -ahl
总用量 16K
drwxr-xr-x 1 mochou5 mochou5 4.0K 2月  12 13:44 .
drwxr-xr-x 1 root    root    4.0K 2月  12 13:44 ..
-rw------- 1 mochou5 mochou5  983 2月  12 13:41 .bash_history
-rw-r--r-- 1 mochou5 mochou5  220 2月   5 14:25 .bash_logout
-rw-r--r-- 1 mochou5 mochou5 3.7K 2月   5 14:25 .bashrc
-rw-rw-r-- 1 mochou5 mochou5    0 2月  12 13:44 hello5.txt
drwxrwxr-x 1 mochou5 mochou5 4.0K 2月   5 16:00 .local
-rw-r--r-- 1 mochou5 mochou5  946 2月   5 16:25 .profile
-rw-r--r-- 1 mochou5 mochou5    0 2月   5 14:30 .sudo_as_admin_successful
-rw------- 1 mochou5 mochou5 1.1K 2月  11 14:39 .viminfo
mochou5@LAPTOP-UN694I4M:~$       
```





****

## 修改文件所有者：`chown 用户名 文件名`

相当于是 **xxx用户的abc文件**，`chown`指令相当于是 "部分覆盖"，原来是yyy用户的abc文件，这时被覆盖成了xxx用户的abc文件

而且查询时 ，**也是先显示所有者 再显示所在组，最后显示文件名**



**应用实例：**

案例1：使用root创建一个 apple.txt ，然后将其所有者修改为mochou5





```shell
root@LAPTOP-UN694I4M:/home/mochou5# cd /home
root@LAPTOP-UN694I4M:/home# touch apple.txt
root@LAPTOP-UN694I4M:/home# ls -l
总用量 32
-rw-r--r-- 1 root    root      465 2月  10 20:48 aa.txt
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 root    root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rw-r--r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  12 13:44 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root        0 2月  12 13:00 ok.txt
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
-rw-r--r-- 1 root    root    10240 2月  11 21:50 vz
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home# chown mochou5 apple.txt
root@LAPTOP-UN694I4M:/home# ls
aa.txt  apple.txt  c.txt  hello4.txt  mydate.txt  pig.txt  vz   看这里.txt
animal  a.txt      dir2   mochou5     ok.txt      tiger    zwj
root@LAPTOP-UN694I4M:/home# ls -l
总用量 32
-rw-r--r-- 1 root    root      465 2月  10 20:48 aa.txt
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rw-r--r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  12 13:44 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root        0 2月  12 13:00 ok.txt
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
-rw-r--r-- 1 root    root    10240 2月  11 21:50 vz
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#
```



可以看到apple.txt的**所有者变成了mochou5，而所在组依旧是root组**

**所在组和所有者未必一致**

```
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
```



****

## 修改文件所在组：`chgrp 组名 文件名`



查询时 ，**是先显示所有者，再显示所在组，最后显示文件名**

因此这里可以看做是 xxx组的abc文件，覆盖了yyy组的abc文件



**应用实例：**

使用 root 用户创建文件 orange.txt ,看看当前这个文件属于哪个组，然后将这个文件所在组，修改到 police 组 



```shell
root@LAPTOP-UN694I4M:/home# touch  orange.txt
root@LAPTOP-UN694I4M:/home# chgrp police orange.txt
root@LAPTOP-UN694I4M:/home# ls -l
总用量 32
-rw-r--r-- 1 root    root      465 2月  10 20:48 aa.txt
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rw-r--r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  12 13:44 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root        0 2月  12 13:00 ok.txt
-rw-r--r-- 1 root    police      0 2月  12 14:21 orange.txt
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
-rw-r--r-- 1 root    root    10240 2月  11 21:50 vz
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#   
```



****

## 改变用户所在组: `usermod`  {前文已叙}



**基本语法：**

改变xxx组的用户a，为yyy组的用户a {这个之前提过   `shaolin zhangsanfeng` 变成了 `wudang zhangsanfeng`}

`usermod -g 组名 用户名`



`usermod -d 目录名 改变用户登录的初始目录`



****

## 权限的基本介绍



**ls -l 中显示的内容如下：**

`-rw-r--r-- 1 root    root      465 2月  10 20:48 aa.txt`



0-9 位说明

1)第 0 位确定文件类型(d, - , l , c , b)

2)第 1-3 位确定所有者（该文件的所有者）拥有该文件的权限。---User

3)第 4-6 位确定所属组（同用户组的）拥有该文件的权限，---Group

4)第 7-9 位确定其他用户拥有该文件的权限 ---Other

*解析一下：*

aa.txt是文件名

**文件类型**：最开头的 `-rw`中的 `-`代表普通文件，如果是 `d`代表是一个目录。如果是 `l`代表是软链接文件，有时候是 `c`代表字符设备{例如:键盘，鼠标}

如果是 `b`代表块文件{例如：硬盘}



**Linux系统中，一切皆文件**



第一个`-` 后面的`rw-`，代表**文件所有者拥有的权限** 为`rw`{ `-`代表空，也就是说额米有第3种权限，只要r和w两种权限}，表示这个文件可以被读写



`-rw-`后面的 `r--`又是一组，代表**所在组的用户的权限**为 `r--`，只有读的权限



`-rw-r--`后面的 `r--`有是一组，代表 **文件其他组的用户的权限**为 `r--`,只要读的权限



``-rw-r--r-- 1 `中的数字1，**如果是文件，表示硬链接的数;如果是目录则表示该目录的子目录的数**。文件一般都是1



后面的`root    root      465`中，第一个root表示文件所有者是root，第2个root表示文件所在是组为root组。最后的数字465表示文件的大小为465，单位是字符数{实际上是464个字符+一个C语言自带的`/0`结束符} 。**如果是目录则都是 4096**，4096代表的目录所在的空间



`2月  10 20:48 aa.txt`,文件最后修改的时间和文件名，不必多说





不服？尝试用普通用户修改 aa.txt文件

![](C:\Users\fucker\Pictures\Linux20.PNG)

其他用户只有 `r`权限，只能读，不能写



就算是 同组的管理员账户依旧不行，需要使用sudo借用root权限

```shell
mochou5@LAPTOP-UN694I4M:/home$ nano aa.txt
mochou5@LAPTOP-UN694I4M:/home$ sudo nano aa.txt
[sudo] mochou5 的密码：
mochou5@LAPTOP-UN694I4M:/home$ 
```



****



## 权限详解{非常重要的基操}

`r`，`w`,`x`是三种权限，很多文件本身就没有 `x`权限{并不是root用户的权限不够高。。}

### rwx作用到文件 {也就是有`r`，`w`,`x`三种权限的是文件}





1) **[ r ]代表可读(read):  可以读取,查看**

2) **[ w ]代表可写(write): 可以修改**

但是**不代表可以删除该文件,删除一个文件的前提条件是对该文件所在的目录有写权限，才能删除该文件。{对目录没有写的权限就只能将原来有内容的文件变成空文件，但是文件本身还在}**

3) **[ x ]代表可执行(execute):可以被执行**









****



### rwx作用到目录 {也就是有`r`，`w`,`x`三种权限的是目录}



1) [ r ]代表可读(read):  **可以读取，ls 查看目录内容**

2) [ w ]代表可写(write):  **可以修改,目录内创建+删除+重命名目录**

{是目录内删除，并不是说能删除这个目录。原理和上面的作用到文件是一样的}

[ x ]代表可执行(execute):**可以进入该目录**









****



### 文件及目录权限实际案例 

**ls	-l 中显示的内容如下：(记住)**

`-rwxrw-r-- 1 root root 1213 Feb 2 09:39 abc`



10 个字符确定不同用户能对文件干什么

第一个字符代表文件类型： 文件 (-),目录(d),链接(l)

其余字符每 3 个一组(rwx) 读(r) 写(w) 执行(x) 第一组 rwx : 文件拥有者的权限是读、写和执行

第二组 rw- :  与文件拥有者同一组的用户的权限是读、写但不能执行

第三组 r-- :	不与文件拥有者同组的其他用户的权限是读不能写和执行

**也可用数字表示为: r=4,w=2,x=1  因此 rwx=4+2+1=7** {论777权限的由来}



1	文件：硬连接数或	目录：子目录数(包括隐藏目录和`.`以及 `..`     {`.`表示当前目录，`..`表示父目录})



root	用户

root	组

1213	文件大小(字节/字符数)，如果是文件夹，显示 4096 字节

****

**关于文件大小**

可以看到ok.txt大小是6个字节 

```shell
-rw-r--r-- 1 root    root        6 2月  12 16:08 ok.txt
```

为什么是6个字节？打开看看

```shell
mochou5@LAPTOP-UN694I4M:/home$ sudo nano ok.txt
```



![](C:\Users\fucker\Pictures\Linux21.PNG)

里面有5个字符，**外加一个C语言自带的结束符/0**,刚好6个字节(字符)



****

Feb 2 09:39	最后修改日期

abc	文件名





****

## 修改文件或目录权限 `chmod`



**基本说明：**

通过 `chmod` 指令，可以修改文件或者目录的权限





### 第一种方式：+、-、=变更权限

`+`代表增加的权限

`-`代表取消权限

`=`代表附加权限{类似于赋值}



**几个字母，各自代表的意思：**

u:所有者	g:组内其他用户	o:其他人	a:所有人(u、g、o 的总和)



**中间要有`，`号隔开，而不是用空格隔开**

1) `chmod	u=rwx,g=rx,o=x	文件/目录名`

代表着给u(所有者)附加的权限为 `rwz`三种，

代表着给g(组内其他用户)附加的权限为 `rx`两种

代表着给o(不在这个组的其他用户)附加的权限为 `z`这一种

文件/目录名，代表**对某一个文件或目录进行操作**



2) `chmod	o+w	文件/目录名`

代表着给o(不在这个组的其他用户)增加的权限为 `w`

文件/目录名，代表**对某一个文件或目录进行操作**





3) `chmod	a-x	文件目录名`

代表着给a(所有用户)取消的权限为 `x`



****





**案例演示：**

1）给 dir2 文件 的*所有者{文件的主人}读写执行的权限*，给*所在组读写权限*，给其它组读权限

```shell
root@LAPTOP-UN694I4M:/home# chmod u=rwx g=rw o=r dir2
chmod: 无法访问'g=rw': 没有那个文件或目录
chmod: 无法访问'o=r': 没有那个文件或目录
```



**中间要用 `,`号隔开，而不是空格。不然只会执行第一条**



```shell
root@LAPTOP-UN694I4M:/home# ls -al
总用量 20
drwxr-xr-x 1 root    root     4096 2月  12 16:36 .
drwxr-xr-x 1 root    root     4096 2月  11 21:20 ..
-rw-r--r-- 1 root    root      478 2月  12 15:20 aa.txt
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rwxrw-r-- 1 root    root        0 2月  10 16:42 dir2
```

已修改，**以及修改文件的被访问权限也算修改文件，最后修改时间依旧会改变**

```shell
-rwxrw-r-- 1 root    root        0 2月  10 16:42 dir2
```



****



2）给 abc 文件的*所有者除去执行的权限*，增加组内用户执行的权限



```shell
root@LAPTOP-UN694I4M:/home# chmod u=rwx,g=rw,o=r abc
chmod: 无法访问'abc': 没有那个文件或目录
```

需要先有abc文件，才能再对文件进行操作

**`touch 文件名`是创建文件，`mkdir 目录名`是创建目录**

并把给dir2文件附加过的权限，给abc附加一遍

```shell
root@LAPTOP-UN694I4M:/home# touch abc
root@LAPTOP-UN694I4M:/home# ls -al
总用量 20
drwxr-xr-x 1 root    root     4096 2月  12 16:51 .
drwxr-xr-x 1 root    root     4096 2月  11 21:20 ..
-rw-r--r-- 1 root    root      478 2月  12 15:20 aa.txt
-rw-r--r-- 1 root    root        0 2月  12 16:51 abc
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rwxrw-r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  12 13:44 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root        6 2月  12 16:08 ok.txt
-rw-r--r-- 1 root    police      0 2月  12 14:21 orange.txt
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home# chmod u=rwx,g=rw,o=rw abc
root@LAPTOP-UN694I4M:/home# ls -al
总用量 20
drwxr-xr-x 1 root    root     4096 2月  12 16:51 .
drwxr-xr-x 1 root    root     4096 2月  11 21:20 ..
-rw-r--r-- 1 root    root      478 2月  12 15:20 aa.txt
-rwxrw-rw- 1 root    root        0 2月  12 16:51 abc
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rwxrw-r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  12 13:44 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root        6 2月  12 16:08 ok.txt
-rw-r--r-- 1 root    police      0 2月  12 14:21 orange.txt
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home# 
```



**然后修改权限：**



```shell
root@LAPTOP-UN694I4M:/home# chmod u-x,g+x abc
root@LAPTOP-UN694I4M:/home# ls -al
总用量 20
drwxr-xr-x 1 root    root     4096 2月  12 16:51 .
drwxr-xr-x 1 root    root     4096 2月  11 21:20 ..
-rw-r--r-- 1 root    root      478 2月  12 15:20 aa.txt
-rw-rwxrw- 1 root    root        0 2月  12 16:51 abc
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rwxrw-r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  12 13:44 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root        6 2月  12 16:08 ok.txt
-rw-r--r-- 1 root    police      0 2月  12 14:21 orange.txt
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#  
```



****

3）给 abc 文件的**所有的用户**添加执行的权限

```shell
root@LAPTOP-UN694I4M:/home# chmod a+x abc
root@LAPTOP-UN694I4M:/home# ls -al
总用量 20
drwxr-xr-x 1 root    root     4096 2月  12 16:51 .
drwxr-xr-x 1 root    root     4096 2月  11 21:20 ..
-rw-r--r-- 1 root    root      478 2月  12 15:20 aa.txt
-rwxrwxrwx 1 root    root        0 2月  12 16:51 abc
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rwxrw-r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  12 13:44 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root        6 2月  12 16:08 ok.txt
-rw-r--r-- 1 root    police      0 2月  12 14:21 orange.txt
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#
```



****



### 第二种方式：通过数字变更权限 {这种最常用}



规则：r=4 w=2 x=1   rwx=4+2+1=7，rw=4+2=6, rz=4+1=6 .....以此类推



 `chmod u=rwx,g=rx,o=x			文件目录名`

相当于  `chmod	751		文件目录名`



**案例演示：**

要求：将  /home/abc 文件的权限修改成	`rwxr-xr-x`, 使用给数字的方式实现：



首先把	`rwxr-xr-x`分解为 `rmx` 和`r-x`和 `r-x`

`rmx`=4+2+1=7

`r-x`=4+1=5

`r-x`=4+1=5

因此是755，指令为 `chmod 755 /home/abc`

```shell
root@LAPTOP-UN694I4M:/home# chmod 755 abc
root@LAPTOP-UN694I4M:/home# ls -al
总用量 20
drwxr-xr-x 1 root    root     4096 2月  12 16:51 .
drwxr-xr-x 1 root    root     4096 2月  11 21:20 ..
-rw-r--r-- 1 root    root      478 2月  12 15:20 aa.txt
-rwxr-xr-x 1 root    root        0 2月  12 16:51 abc
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rwxrw-r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  12 13:44 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root        6 2月  12 16:08 ok.txt
-rw-r--r-- 1 root    police      0 2月  12 14:21 orange.txt
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#
```

****

## 修改文件所有者： `chown`

**基本介绍**

改变文件的所有者 {前文已叙}

`chown	[选项] 新的用户名	文件名	`



**同时改变用户的所有者和所在的组   {比较常用}**

`chown [选项] 新的用户名:新的组名	文件名	`          **这里的：之间没有空格**

原来的

```shell
-rw-r--r-- 1 root    root       37 2月  11 19:47 pig.txt
```



改成 mohcou5为所有者，在mochou5这个组中

使用 `chown mochou5:mochou5 pig.txt`修改       **这里的：之间没有空格**

```shell
root@LAPTOP-UN694I4M:/home# chown mochou5:mochou5 pig.txt
root@LAPTOP-UN694I4M:/home# ls -al
总用量 20
drwxr-xr-x 1 root    root     4096 2月  12 16:51 .
drwxr-xr-x 1 root    root     4096 2月  11 21:20 ..
-rw-r--r-- 1 root    root      478 2月  12 15:20 aa.txt
-rwxr-xr-x 1 root    root        0 2月  12 16:51 abc
drwxr-xr-x 1 root    root     4096 2月  11 21:25 animal
-rw-r--r-- 1 mochou5 root        0 2月  12 14:06 apple.txt
-rw-r--r-- 1 root    root      117 2月  11 12:40 a.txt
-rw-r--r-- 1 root    root    17633 2月  11 19:58 c.txt
-rwxrw-r-- 1 root    root        0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root      566 2月  11 15:52 hello4.txt
drwxr-xr-x 1 mochou5 mochou5  4096 2月  12 13:44 mochou5
-rw-r--r-- 1 root    root        0 2月  10 22:15 mydate.txt
-rw-r--r-- 1 root    root        6 2月  12 16:08 ok.txt
-rw-r--r-- 1 root    police      0 2月  12 14:21 orange.txt
-rw-r--r-- 1 mochou5 mochou5    37 2月  11 19:47 pig.txt
drwxr-xr-x 1 root    root     4096 2月  11 19:48 tiger
drwxr-xr-x 1 root    root     4096 2月  11 20:10 zwj
-rwxr-xr-x 1 root    root      360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#
```







**-R	如果是目录 则使其下所有子文件或目录递归生效**      {改变该目录下的所有文件}   **R是大写的**

1) 请将 /home/animal 目录下**所有的**文件和目录的**所有者都修改成mochou5**



使用 `chown -R mochou5 animal`

```shell
root@LAPTOP-UN694I4M:/home# chown -R mochou5 animal
root@LAPTOP-UN694I4M:/home# cd animal
root@LAPTOP-UN694I4M:/home/animal# ls -l
总用量 0
drwxr-xr-x 1 mochou5 root 4096 2月  11 19:48 tiger
root@LAPTOP-UN694I4M:/home/animal# cd tiger
root@LAPTOP-UN694I4M:/home/animal/tiger# ls -l
总用量 0
-rw-r--r-- 1 mochou5 root 37 2月  11 19:54 pig.txt
root@LAPTOP-UN694I4M:/home/animal/tiger#
```

可以看到所有者都改成 mochou5了



****