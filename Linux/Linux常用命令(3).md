# 复杂的文档，看几分钟看不懂时，请直接看完整个课程后，再写笔记--写笔记的第2种方式



# Ubuntu是`apt-get`代替了 CentOS的`yum`





****

# 定时任务调度 `crond`



![](C:\Users\fucker\Pictures\Linux22.png)

图画的有点迷，看看就可以了。 图中的`=》机制`表示的是，**执行**

**这个指令后，就会让系统(机制)去进行定时调用**

使用crontab 进行定时任务的设置 {也就是说定时调度}



**概述：**

任务调度：是指系统在某个时间执行的特定的命令或程序。

**任务调度分类：**

1.系统工作：有些重要的工作必须周而复始地执行。如病毒扫描等

2.个别用户工作：个别用户可能希望执行某些程序，比如对 mysql 数据库的备份。



**常用选项：**

| 参数 | 功能描述                      |
| ---- | ----------------------------- |
| -e   | 查询crontab定时任务           |
| -l   | 查询crontab任务               |
| -r   | 删除当前用户所有的crontab任务 |



## **快速入门**

**任务的要求**

设置任务调度文件：/etc/crontab

设置个人任务调度。执行 crontab –e 命令。接着输入任务到调度文件

如：*/1 * * * * ls –l	/etc/ > /tmp/to.txt

意思说每小时的每分钟执行 ls –l /etc/ > /tmp/to.txt 命令



****

 **步骤如下**

-1）写shell脚本

0）给脚本文件添加被允许访问的权限

1) cron -e   {定时任务调度启动，执行完后进行编辑页面，写具体的如何进行任务调度}

2) */ 1 * * * * ls -l /etc >> /tmp/to.txt  {具体的如何定时任务调度}

3) 当保存退出后就程序。

4) 在每一分钟都会自动的调用 ls -l /etc >> /tmp/to.txt



****



# 磁盘分区和挂载



## 分区的方式：{了解即可 }

1) **mbr 分区**:

1.最多支持四个主分区

2.系统只能安装在主分区

3.扩展分区要占一个主分区

4.MBR 最大只支持 2TB，但拥有最好的兼容性



2) **gtp 分区:**

1.支持无限多个主分区（但操作系统可能限制，比如 windows 下最多 128 个分区）

2.最大支持 18EB 的大容量（1EB=1024 PB，1PB=1024 TB  ）

3.windows7 64 位以后支持 gtp



![](C:\Users\fucker\Pictures\Linux23.PNG)



****



**Linux分区**

##  原理介绍

1) Linux 来说无论有几个分区，分给哪一目录使用，它归根结底就只有一个根目录，一个独立且唯一的文件结构 , Linux 中每个分区都是用来组成整个文件系统的一部分

2) Linux 采用了一种叫“载入”的处理方法，它的整个文件系统中包含了一整套的文件和目录， 且将一个分区和一个目录联系起来。这时要载入的一个分区将使它的存储空间在一个目录下获得

![](C:\Users\fucker\Pictures\Linux24.png)



**硬盘中的每一个分区对应(关联)着文件系统的一部分**

这是分区X{名词}和文件系统之间的关系，**我们把这种关系称为 “载入”**

所谓硬盘分区{动词}这一操作，就是**将分出来的硬盘空间和文件系统的某个部分建立联系！**我们也将这一过程称为 **挂载**{将文件系统中的xxx挂载到硬盘的a分区上}



而相对的，断开联系，我们就称为**卸载  **







****

## 硬盘说明 {了解即可}

Linux 硬盘分 IDE 硬盘和 SCSI 硬盘，目前基本上是 SCSI 硬盘{性能更好，IDE基本被淘汰了}

*1)对于 IDE 硬盘，驱动器标识符为“hdx~”,其中“hd”表明分区所在设备的类型，这里是指 IDE 硬盘了。“x”为盘号（a 为基本盘，b 为基本从属盘，c 为辅助主盘，d 为辅助从属盘）,“~”代表分区，前四个分区用数字 1 到 4 表示，它们是主分区或扩展分区，从 5 开始就是逻辑分区。例，hda3 表示为第一个 IDE 硬盘上的第三个主分区或扩展分区,hdb2 表示为第二个 IDE 硬盘上的第二个主分区或扩展分区。* {了解即可}



2)对于 SCSI 硬盘则标识为“sdx~”，SCSI 硬盘是用“sd”来表示分区所在设备的类型的，其余则和 IDE 硬盘的表示方法一样。



![](C:\Users\fucker\Pictures\Linux25.png)

勘误：唯一标识分区{UUID}是32位的，不是40位 



每一个分区的大小

![](C:\Users\fucker\Pictures\Linux26.png)

****

****



## 磁盘情况查询 ：`df- l`和 `df -lh`

**基本语法：**

df -l



**应用实例：**

查询系统整体磁盘使用情况：



```shell
root@LAPTOP-UN694I4M:/home/mochou5# df -l
文件系统           1K-块      已用      可用 已用% 挂载点
rootfs         446370812 167853932 278516880   38% /
none           446370812 167853932 278516880   38% /dev
none           446370812 167853932 278516880   38% /run
none           446370812 167853932 278516880   38% /run/lock
none           446370812 167853932 278516880   38% /run/shm
none           446370812 167853932 278516880   38% /run/user
cgroup         446370812 167853932 278516880   38% /sys/fs/cgroup
root@LAPTOP-UN694I4M:/home/mochou5#
```

**查看磁盘具体使用情况(还有多少可用的)：`df -lh` **

```shell
root@LAPTOP-UN694I4M:/home/mochou5# df -lh
文件系统        容量  已用  可用 已用% 挂载点
rootfs          426G  161G  266G   38% /
none            426G  161G  266G   38% /dev
none            426G  161G  266G   38% /run
none            426G  161G  266G   38% /run/lock
none            426G  161G  266G   38% /run/shm
none            426G  161G  266G   38% /run/user
cgroup          426G  161G  266G   38% /sys/fs/cgroup
root@LAPTOP-UN694I4M:/home/mochou5#
```

****

## 查询指定目录的磁盘占用情况： `du -ach /目录`

## 

**基本语法：**

`du -ach /目录`

查询指定目录的磁盘占用情况，默认为当前目录

 

**常用选项：**

| 用法          | 功能描述                                                     |
| ------------- | ------------------------------------------------------------ |
| -s            | 指定目录占用大小汇总                                         |
| -h            | 带计量单位{显示出有多少k，和a连用}                           |
| -a            | {显示目录下的文件占用磁盘信息}                               |
| --max-depth=X | 子目录深度{显示出查到目录下的第X级子目录,X为任意数没有指定就是最大深度，查到所有子目录下} |
| -c            | 列出明细的同时，增加汇总值 {最后一个总用量}                  |





**应用实例：**

查用  /home 目录的磁盘占用情况，深度为1 



{深度为1，就是代表home下的1级子目录}



```shell
root@LAPTOP-UN694I4M://# du -ach --max-depth=1 /home
0       /home/a.txt
0       /home/aa.txt
0       /home/abc
0       /home/animal
0       /home/apple.txt
20K     /home/c.txt
0       /home/dir2
0       /home/hello4.txt
16K     /home/mochou5
0       /home/mydate.txt
0       /home/ok.txt
0       /home/orange.txt
0       /home/pig.txt
0       /home/tiger
0       /home/zwj
0       /home/看这里.txt
36K     /home
36K     总用量
root@LAPTOP-UN694I4M://#
```



**如果没有 `-c`,就没有最后的总用量 **

```shell
root@LAPTOP-UN694I4M:/# du -ah --max-depth=1 /home
0       /home/a.txt
0       /home/aa.txt
0       /home/abc
0       /home/animal
0       /home/apple.txt
20K     /home/c.txt
0       /home/dir2
0       /home/hello4.txt
16K     /home/mochou5
0       /home/mydate.txt
0       /home/ok.txt
0       /home/orange.txt
0       /home/pig.txt
0       /home/tiger
0       /home/zwj
0       /home/看这里.txt
36K     /home
root@LAPTOP-UN694I4M:/#
```



**如果没有h,则不显示计量单位**



```shell
root@LAPTOP-UN694I4M:/# du -a --max-depth=1 /home
0       /home/a.txt
0       /home/aa.txt
0       /home/abc
0       /home/animal
0       /home/apple.txt
20      /home/c.txt
0       /home/dir2
0       /home/hello4.txt
16      /home/mochou5
0       /home/mydate.txt
0       /home/ok.txt
0       /home/orange.txt
0       /home/pig.txt
0       /home/tiger
0       /home/zwj
0       /home/看这里.txt
36      /home
root@LAPTOP-UN694I4M:/#
```



**如果没有 `-a`,就没有目录下的文件占用磁盘信息**

```shell
root@LAPTOP-UN694I4M:/# du --max-depth=1 /home
0       /home/animal
16      /home/mochou5
0       /home/tiger
0       /home/zwj
36      /home
```

****



## **磁盘情况-工作实用指令**{重点}



### 1) 统计文件夹下文件的个数： `ls -l 目录 | grep "^-" | wc -l` 



`grep`是过滤指令  ，`grep "^-"`是正则表达式 ，表达的是过滤出以 `-`开头的文件/目录{以 `-`开头的文件/目录，就是普通的目录 }

`|`是管道符，将前一条指令的返回值交给下一条指令处理

最后的 `wc -l`代表统计文件个数



后面的类似，只是参数有些不同



****



**案例1： 统计/home文件夹下文件的个数**

```shell
root@LAPTOP-UN694I4M:/# ls -l /home |grep "^-" | wc -l
12
root@LAPTOP-UN694I4M:/#
```





****



### 2)统计文件夹下目录的个数: `ls -l 目录 | grep "^d" |wc -l`

`grep "^d"`即可表示过滤出的是目录，{ `^-`表示过滤出的是普通文件，而 `"^d"`表示过滤出的是目录}



**案例2：统计/home文件夹下目录的个数**

```shell
root@LAPTOP-UN694I4M:/# ls -l /home |grep "^d" | wc -l
4
root@LAPTOP-UN694I4M:/# ls -l /home
总用量 20
-rw-r--r-- 1 root    root      478 2月  12 15:20 aa.txt
-rwxr-xr-x 1 root    root        0 2月  12 16:51 abc
drwxr-xr-x 1 mochou5 root     4096 2月  11 21:25 animal
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
root@LAPTOP-UN694I4M:/#
```

一共是4个 aniaml,mochou5,tiger,zwj





****



### 3)统计文件夹下文件的个数,包括子文件夹里的 `ls -lR 目录 | grep "^-" |WC -l`



`-R`表示递归，之前的查询/home下的变成了 **/home及其子目录下的**



**案例3：统计/home文件夹下文件的个数,包括子文件夹里的**



```shell
root@LAPTOP-UN694I4M:/# ls -lR /home |grep "^-" | wc -l
18
root@LAPTOP-UN694I4M:/#
```





****



### 4) 以树状显示当前文件夹目录结构: ` tree 文件/目录`

**没有指定，就是默认当前目录**



第一次使用，需要安装，CentOS使用指令 ：`yum install tree`安装



Ubuntu是`apt-get`代替了 `yum`，第一次需要用 `apt-get install `来安装指令{如果没有该指令，就需要安装}



**以树状显示当前文件夹{/home}目录结构**



```shell
root@LAPTOP-UN694I4M:/# tree /home
/home
├── aa.txt
├── abc
├── animal
│   └── tiger
│       └── pig.txt
├── apple.txt
├── a.txt
├── c.txt
├── dir2
├── hello4.txt
├── mochou5
│   └── hello5.txt
├── mydate.txt
├── ok.txt
├── orange.txt
├── pig.txt
├── tiger
│   └── pig.txt
├── zwj
│   ├── aaa.txt
│   ├── hello3.txt
│   └── pig.txt
└── 看这里.txt

5 directories, 18 files
root@LAPTOP-UN694I4M:/#
```



**我们可以看到文件系统的数据结构是树**



****



# Linux网络配置 [这章讲的不好]



## Linux网络配置原理图(虚拟机)的



![](C:\Users\fucker\Pictures\Linux30.PNG)

**Linux的ip是动态的ip**



broadcast

使用 `ping`指令，访问一下百度，表示目前网络状态良好

```shell
root@LAPTOP-UN694I4M:/# ping www.baidu.com
PING www.a.shifen.com (180.101.49.41) 56(84) bytes of data.
64 bytes from 180.101.49.41 (180.101.49.41): icmp_seq=1 ttl=52 time=46.2 ms
64 bytes from 180.101.49.41 (180.101.49.41): icmp_seq=2 ttl=52 time=304 ms
64 bytes from 180.101.49.41 (180.101.49.41): icmp_seq=3 ttl=52 time=23.3 ms
64 bytes from 180.101.49.41 (180.101.49.41): icmp_seq=4 ttl=52 time=35.4 ms
64 bytes from 180.101.49.41 (180.101.49.41): icmp_seq=5 ttl=52 time=49.3 ms
64 bytes from 180.101.49.41 (180.101.49.41): icmp_seq=6 ttl=52 time=46.5 ms
^C
--- www.a.shifen.com ping statistics ---
7 packets transmitted, 6 received, 14% packet loss, time 6005ms
rtt min/avg/max/mdev = 23.368/84.208/304.265/98.806 ms
```



**查看当前的网络配置：`ifconfig`或者 `idconfig -a`**



`ifconfig`相当于Windows中的 `ipconfig`



```shell
root@LAPTOP-UN694I4M:/# ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 1500
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0xfe<compat,link,site,host>
        loop  (本地环回)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        。。。。。。。。省略。。。。。。。。。
```



这里显示的Linux ip地址为 `127.0.0.1`  {并不是}

Windows有两块网卡，**Windows通过虚拟网卡和Linux构成了一个网络，可以进行通信**



Linux 通过网络来 `ping` windows



![](C:\Users\fucker\Pictures\Linux27.PNG)



Windows通过网络来 `ping` Linux

![](C:\Users\fucker\Pictures\Linux28.PNG)



而Windows真正和外接的是另一块 真实的网卡



例如这里使用无线上网的形式，那么和外接的就是这块网卡{无线适配器下的}

![](C:\Users\fucker\Pictures\Linux29.PNG)



**WSL和windows是通过本地连接来连接的，windows中本地连接的那一块的地址就是Windows和WSL通信时的IP地址。。。而Linux系统的地址和Windows居然是一样的(redis该文件哪里可以看出来 。。。)**





****



**`ifconfig` 查不出`eth0`时，使用 `ifcongfig -a` **



etho 表示网卡的代号（这里只有一块网卡，所以只有一个eth0，如果有若干网卡，则会有eth1，eth2等）
Link encap:表示网络接入类型，这里是Ethernet 表示以太网！
HWaddr: 硬件地址，也就MAC地址，图片里为FA:16:3E:9C:85:EB
inet addr:表示IP地址
Bcast:表示Broadcast，即广播地址
Mask:表示子网掩码
inet6 addr:ipv6的地址
MTU:链路帧长最大为1500字节
Metric:表示跃点数：指出路由的成本，通常表示到达目的地址的跳数
RX packets：表示从网络启动开始，接收到的包的总数
TX packets：表示从网络启动开始，发送包的总数
collisions :表示包碰撞的情况（如果碰撞的包很多，表明你的网络不太好）
txqueuelen:表示传送数据缓冲区的长度
RX bytes:接收的总字节数
TX bytes:发送的总字节数

****



**lo表示本机的环回接口**

第二种方法，使用ip addr



在命令行中输入命令 ip addr得到上图的结果
<BRADCAST,MULTICAST,UP,LOWER_UP>
bracast表示网卡具有广播地址
multicast表示可以发送多播包
up表示网卡处于启动模式
lower_up表示有电流

两种方式对比：
ifconfig可以查看到更为详细的信息，拥有查看发送与接收包的统计信息。
如果只是要查看一些基本信息，ip addr命令足够了



****



## 指定固定的ip

直 接 修 改 配 置 文 件 来 指 定  IP, 并 可 以 连 接 到 外 网 ( 程 序 员 推 荐 ) ， 编 辑	

CentOS是这个文件：

`/etc/sysconfig/network-scripts/ifcfg-eth0`

Ubuntu则是这个文件

`/etc/sysctl.d/10-network-security.conf`



eth0代表第一块网卡



要求：将 ip 地址配置的静态的，ip 地址为 192.168.184.130



额。。。WSL中没有显示具体ip的。。



```shell
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks.
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Turn on SYN-flood protections.  Starting with 2.6.26, there is no loss
# of TCP functionality/features under normal conditions.  When flood
# protections kick in under high unanswered-SYN load, the system
# should remain more stable, with a trade off of some loss of TCP
# functionality/features (e.g. TCP Window scaling).
net.ipv4.tcp_syncookies=1
```

而虚拟机上是



![](C:\Users\fucker\Pictures\Linux31.png)

修改后，一定要重启服务

1) service network restart

2) reboot 重启系统



![](C:\Users\fucker\Pictures\Linux32.png)

****

# 需要学的网络管理指令

参考这篇

https://mp.weixin.qq.com/s/oVb2pWproP4SjgNz8_x53g



## Linux下常见的网络接口

| 接口类型                           | 接口名称                                                     | 说明                                              |
| ---------------------------------- | ------------------------------------------------------------ | ------------------------------------------------- |
| 以太网接口{常说的网卡接口就是这个} | ethX{X可以是任何从0开始的整数。如：eth0表示的就是第一块以太网卡，而eth1就表示是第2块以太网卡} | 最常用的网络接口                                  |
| 令牌环接口                         | trX{X可以是任何从0开始的整数}                                | 只出现在少数纯IBM环境的网络中                     |
| 光纤分布式数据接口                 | fddiX{X可以是任何从0开始的整数}                              | FDDI接口设备昂贵，通常用于核心网或高速网络中      |
| 本地回环接口                       | lo                                                           | 用于支持UNIX Domain Socket技术的进程相互通信(IPC) |
|                                    |                                                              |                                                   |



****



配置网络参数有**两种**方式：

- 临时性网络配置

- - 通过**命令**修改当前内核中的网络相关参数实现，配置后**立即**生效，重新开机后失效。{这个也可以虚拟机图形化的界面来修改。。。用虚拟机的那个就是这么改的 }

- 永久性网络配置

- - 通过直接**修改**网络相关的**配置文件**实现，需要**重启服务**，重新开机后保留所有配置  {演示的进入/etc目录的哪个编辑文件就是这个}



****



**三种网络连接模式**

简要摘抄一下：

- 桥接模式的虚拟机，就像一个在路由器"民政局"那里"上过户口"的成年人，有自己单独的居住地址，虽然和主机住在同一个大院里，但好歹是有户口的人，可以大摇大摆地直接和外面通信。{常见的联网就是这种模式}
- NAT模式的虚拟机，纯粹就是一个没上过户口的黑户，路由器"民政局"根本不知道有这么个人，自然也不会主动和它通信。即使虚拟机偶尔要向外面发送点的信件，都得交给主机以主机的名义转发出去，主机还专门请了一位叫做NAT的老大爷来专门负责这些虚拟机的发信、收信事宜。{上面的那张网络原理图就是这个}
- 仅主机模式的虚拟机，纯粹是一个彻彻底底的黑奴，不仅没有户口、路由器"民政局"不知道这么号人，还被主机关在小黑屋里，连信件也不准往外发。{机器断网模式}



**所以WSL是那种网络连接模式？？？**





参考这篇：https://zhuanlan.zhihu.com/p/34885187

两者存在共享端口，文件系统互通，同时WSL是进程形式存在的 ，猜测是桥接模式，Linux借用的Windows的ip和端口{虚拟机那个是有自己的端口和ip，WSL的ip和端口自己都没有}

毕竟 WSL是一个在Windows 10上能够原生运行Linux二进制可执行文件的兼容层

WSL使用中的坑---Docker和网络以及底层



然而WSL2已经变成了高级虚拟机了。。。。





****



## 网络接口相关：`ifconfig`和 `ifup/ifdown`

查看网络接口信息: `ifconfig`

基本语法：`ifconfig [ethX]`

查看网络具体接口配置



这个前面提过，不赘述



开启或关闭接口： `ifup/ifdown`

**基本语法：**

- 网络接口的启用与停用：使用 `ifup ethX` 命令来启用指定的接口，使用 `ifdown ethX` 命令来禁用指定的接口

第一次使用，需要先安装ifdown

```shell
root@LAPTOP-UN694I4M:/# apt install ifupdown
正在读取软件包列表... 完成
正在分析软件包的依赖关系树
正在读取状态信息... 完成
下列软件包是自动安装的并且现在不需要了：
  libdumbnet1
使用'apt autoremove'来卸载它(它们)。
建议安装：
  ppp rdnssd
下列【新】软件包将被安装：
  ifupdown
  。。。。。。。。。省略。。。。。。。。。。。
```

使用指令：

```shell
root@LAPTOP-UN694I4M:/# ifdown
ifdown: no interface(s) specified
ifdown: Use --help for help
root@LAPTOP-UN694I4M:/#
root@LAPTOP-UN694I4M:/# ifup
ifup: no interface(s) specified
ifup: Use --help for help
root@LAPTOP-UN694I4M:/#
```





****

## 临时配置相关



`route`命令：可以临时地设置内核路由表

执行结果是显示出，内核中的路由表

```shell
root@LAPTOP-UN694I4M:/# route
内核 IP 路由表
目标            网关            子网掩码        标志  跃点   引用  使用 接口
127.0.0.0       0.0.0.0         255.0.0.0       U     256    0        0 lo
127.0.0.1       0.0.0.0         255.255.255.255 U     256    0        0 lo
127.255.255.255 0.0.0.0         255.255.255.255 U     256    0        0 lo
224.0.0.0       0.0.0.0         240.0.0.0       U     256    0        0 lo
255.255.255.255 0.0.0.0         255.255.255.255 U     256    0        0 lo
0.0.0.0         192.168.31.1    255.255.255.255 U     0      0        0 wifi0
192.168.31.0    0.0.0.0         255.255.255.0   U     256    0        0 wifi0
192.168.31.106  0.0.0.0         255.255.255.255 U     256    0        0 wifi0
192.168.31.255  0.0.0.0         255.255.255.255 U     256    0        0 wifi0
224.0.0.0       0.0.0.0         240.0.0.0       U     256    0        0 wifi0
255.255.255.255 0.0.0.0         255.255.255.255 U     256    0        0 wifi0
。。。。。。。。。。。。省略。。。。。。。
```







`hostname`命令：可以临时地修改主机名

```shell
root@LAPTOP-UN694I4M:/# hostname
LAPTOP-UN694I4M
```

显示的就是`root@`后面的









`sysctl`命令：可以临时地开启内核的包转发



```shell
root@LAPTOP-UN694I4M:/# sysctl

用法：
 sysctl [options] [variable[=value] ...]

选项：
  -a, --all            display all variables
  -A                   alias of -a
  -X                   alias of -a
      --deprecated     include deprecated parameters to listing
  -b, --binary         print value without new line
  -e, --ignore         ignore unknown variables errors
  -N, --names          print variable names without values
  -n, --values         print only values of a variables
  -p, --load[=<file>]  read values from file
  -f                   alias of -p
      --system         read values from all system directories
  -r, --pattern <expression>
                       select setting that match expression
  -q, --quiet          do not echo variable set
  -w, --write          enable writing a value to variable
  -o                   does nothing
  -x                   does nothing
  -d                   alias of -h

 -h, --help     显示此帮助然后离开
 -V, --version  显示程序版本然后离开

欲了解更多详细信息，请参见 sysctl(8)。
root@LAPTOP-UN694I4M:/#
```



使用命令来做的是**网络临时配置**，要做到永久配置就需要**直接修改文件**的方式



CentOS下的文件



| 配置文件                                  | 说明                                                   |
| ----------------------------------------- | ------------------------------------------------------ |
| /etc/sysconfig/network                    | 系统网络配置文件，包含了主机的网络信息用于系统 启动    |
| /etc/sysconfig/network-scripts/ifcfg-ethX | 以太网接口配置文件                                     |
| /etc/sysconfig/network-scripts/route-ethX | 以太网接口的静态路由配置文件                           |
| /etc/hosts                                | 完成主机名映射为IP地址的静态解析功能                   |
| /etc/resolv.conf                          | 配置域名服务客户端的配置文件，用于指定域名服务器的位置 |
| /etc/host.conf                            | 配置域名服务客户端的控制文件                           |



**网络检测的常用工具/指令** {这个地方有坑，别纠结}



`ifconfig`命令：检测网络接口配置      {演示太多了，不再演示}

`route`命令：检测路由配置{路由表的形式}   {演示太多了，不再演示}

`ping`命令：检测网络连通性  {演示太多了，不再演示}



`netstat`命令：查看网络状态

```shell
root@LAPTOP-UN694I4M:/# netstat
激活Internet连接 (w/o 服务器)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
活跃的UNIX域套接字 (w/o 服务器)
Proto RefCnt Flags       Type       State         I-Node   路径
```

`lsof`命令：查看指定IP和/或 端口的进程的当前运行情况  {类似于windows的netstat查看端口号、进程占用}

```shell
COMMAND PID TID    USER   FD      TYPE DEVICE    SIZE             NODE NAME
init      1        root  cwd       DIR    0,2    4096 8725724278314007 /
init      1        root  rtd       DIR    0,2    4096 8725724278314007 /
init      1        root  txt       REG    0,2  591344 4222124650952678 /init
init      1        root  mem       REG    0,0                   292838 /init (path dev=0,2, inode=4222124650952678)
init      1        root    3w      CHR   1,11         1407374884100937 /dev/kmsg
init      1        root    0u      CHR    1,3         1407374884100942 /dev/null
init      1        root    1u      CHR    1,3         1407374884100942 /dev/null
init      1        root    2u      CHR    1,3         1407374884100942 /dev/null
init      1        root    4u      CHR  10,50          844424930681710 /dev/lxss
。。。。。。。。省略。。。。。。。。。
```

****

`host`  、`dig`、`nslookup`  {这三个都是} 检测DNS解析

```shell
root@LAPTOP-UN694I4M:/# dig

; <<>> DiG 9.11.3-1ubuntu1.11-Ubuntu <<>>
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24324
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 24

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
; COOKIE: 69faa934bcbee591db4001795e462d9782f90a0d2f536774 (good)
;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       73308   IN      NS      f.root-servers.net.
.                       73308   IN      NS      m.root-servers.net.
.                       73308   IN      NS      i.root-servers.net.
.                       73308   IN      NS      g.root-servers.net.
.                       73308   IN      NS      k.root-servers.net.
.                       73308   IN      NS      d.root-servers.net.
.                       73308   IN      NS      a.root-servers.net.
.                       73308   IN      NS      l.root-servers.net.
.                       73308   IN      NS      c.root-servers.net.
.                       73308   IN      NS      b.root-servers.net.
.                       73308   IN      NS      e.root-servers.net.
.                       73308   IN      NS      j.root-servers.net.
.                       73308   IN      NS      h.root-servers.net.
```

`traceroute`   检测到目的主机所经过的路由器

同样第一次使用，需要安装

```shell
root@LAPTOP-UN694I4M:/# apt install traceroute
正在读取软件包列表... 完成
正在分析软件包的依赖关系树
正在读取状态信息... 完成
下列软件包是自动安装的并且现在不需要了：
  libdumbnet1
使用'apt autoremove'来卸载它(它们)。
下列【新】软件包将被安装：
  traceroute
  。。。。。省略。。。。。。。。。。
```





****

`tcpdump`   显示本机网络流量的状态

```shell
root@LAPTOP-UN694I4M:/# tcpdump
tcpdump: socket: Socket type not supported
root@LAPTOP-UN694I4M:/#
```

**翻译结果**               

Tcpdump：套接字：不支持套接字类型



****

# **进程管理**

## 进程的基本介绍



1)在 LINUX 中，**每个执行的程序（代码）都称为一个进程**。每一个进程都分配一个 ID 号。

2)**每一个进程，都会对应一个父进程**，而这个父进程可以复制多个子进程。例如 www 服务器。

3)每个进程都可能以两种方式存在的。**前台与后台，所谓前台进程就是用户目前的屏幕上可以进行操作的。后台进程则是实际在操作{后台进程也被称为守护进程}，但由于屏幕上无法看到的进程**，通常使用后台方式执行。

4)**一般系统的服务都是以后台进程的方式存在**，而且都会常驻在系统中。直到关机才结束。

****

## 显示系统执行的进程：`ps`,一般使用的参数是 `ps -aux`



**基本介绍：**

`ps`指令是用来查看目前系统中，**有哪些进程正在执行**，**以及它们执行的状况**。

也可以不加任何参数

`ps`指令显示的信息选项



| 字段 | 说明                   |
| ---- | ---------------------- |
| PID  | 进程识别号             |
| TTY  | 终端机号               |
| TIME | 此进程所消耗的CPU时间  |
| CMD  | 正在执行的命令或进程名 |



**基本语法：**

| 用法  | 功能描述                   |
| ----- | -------------------------- |
| ps -a | 显示当前终端的所有进程信息 |
| ps -u | 以用户的格式显示进程信息   |
| ps -x | 显示后台进程运行的参数     |



执行 `ps -aux`{这个显示的信息比较完整}

```shell
root@LAPTOP-UN694I4M:/# ps -aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   8892   292 ?        Ssl  09:30   0:00 /init
root         5  0.0  0.0   8904   208 tty1     Ss   09:30   0:00 /init
mochou5      6  0.0  0.0  18692  3148 tty1     S    09:30   0:00 -bash
root        18  0.0  0.0  18500  1912 tty1     S    09:30   0:00 su root
root        19  0.0  0.0  17676  2140 tty1     S    09:30   0:00 bash
root       412  0.0  0.0  19496  2028 tty1     R    13:51   0:00 ps -aux
root@LAPTOP-UN694I4M:/#
```

`USER` 表示的是用户名

`PID` 表示的是进程ID

`%CPU`表示的是占用CPU的百分比

`%MER` 表示的是占用内存的百分比

`VSZ`表示的是使用的虚拟内存

`RSS`表示的是使用的物理内存的情况

`TTY`表示的是使用的终端

`STAT`表示的是进程的状态 ，如:S代表休眠，R表示运行

`START`表示的是进程启动的时间

`TIME`表示的是占用CPU的时间

`COMMAND`表示的是执行该进程时使用的命令行





init是系统启动后的第一个用户进程，好多服务，守护进程都依赖于它，不可能没有

****



**PS详解**

1）指令： `ps-aux|grep xxx`

使用管道符 `|`,将查看到的结果交给 `grep`进行过滤。相当于 *只想看结果中的某部分*

例如：我们想看看有没有sshd服务

```shell
root@LAPTOP-UN694I4M:/# ps -aux|grep sshd
root       414  0.0  0.0  16644  1104 tty1     S    14:20   0:00 grep --color=auto sshd
root@LAPTOP-UN694I4M:/#
```

只有字符，没有提示时，需要根据每个字符的相对位置推测是属于 哪项数据

```shell
root       414  0.0  0.0  16644  1104 tty1     S    14:20   0:00 grep --color=auto sshd
```

root用户，进程id为414，占用cpu和内存的百分比都为0.0,占用虚拟内存16644kb，占用真实内存1104KB，终端号缩写为tty1，进程处于休眠状态，线程启动的时间是14：20  ,CPU执行的时间为0.0,启动该线程的命令为 `grep --color=autp sshd`



2） 指令说明 

- System V ： 展示风格     {有时没有这个}
- USER：用户名称
- PID：进程号
- **%CPU：进程占用 CPU 的百分比**
- **%MIEM :进程占用的物理内存的百分比**
- **VSZ :进程占用的虚拟内存大小(单位：KB)**
- **RSS  :进程占用的物理内存大小 (单位：KB)**
- TT：终端名称,缩写 .
- STAT：进程状态，其中 S-睡眠，s-表示该进程是会话的先导进程，N-表示进程拥有比普通优先级更低的优先级，R-正在运行，D-短期等待，Z-僵死进程，T-被跟踪或者被停止等等
- STARTED：进程的启动时间
- TIME：CPU 时间，即进程使用 CPU 的总时间
- COMMAND  {有时也表示为CMD}：启动进程所用的命令和参数，如果过长会被截断显示

****

## 查看进程的父进程: `ps -ef`

将它和 `ps -aux`分开说，因为两者一起使用，会这样

```shell
root@LAPTOP-UN694I4M:/# ps -auxef
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   8892   292 ?        Ssl  09:30   0:00 /init
root         5  0.0  0.0   8904   208 tty1     Ss   09:30   0:00 /init
mochou5      6  0.0  0.0  18692  3096 tty1     S    09:30   0:00  \_ -bash HOSTTYPE=x86_64 LANG=zh_CN.UTF-8 PATH=
root        18  0.0  0.0  18500  1844 tty1     S    09:30   0:00      \_ su root LC_ALL=zh_CN.UTF-8 LS_COLORS=rs=
root        19  0.0  0.0  17676  2108 tty1     S    09:30   0:00          \_ bash LC_ALL=zh_CN.UTF-8 LS_COLORS=rs
root       423  0.0  0.0  19496  1996 tty1     R    14:35   0:00              \_ ps -auxef LC_ALL=zh_CN.UTF-8 LS_

```



`ps -ef`的使用和 `ps -aux`的使用是一样的，只是查询的数据显示有所区别

```shell
root@LAPTOP-UN694I4M:/# ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 09:30 ?        00:00:00 /init
root         5     1  0 09:30 tty1     00:00:00 /init
mochou5      6     5  0 09:30 tty1     00:00:00 -bash
root        18     6  0 09:30 tty1     00:00:00 su root
root        19    18  0 09:30 tty1     00:00:00 bash
root       417    19  0 14:31 tty1     00:00:00 ps -ef
```

没有CPU,内存的百分比占用，物理内存和虚拟内存的具体占用(单位KB)，进程的状态，这5条信息

但是多了`PPID`这个父进程 id

如果父进程ID为0，表示该进程是第一个进程



同样的也能用**管道符过滤**

显示出sshd进程以及其父进程的信息

```shell
root@LAPTOP-UN694I4M:/# ps -aux|grep sshd
root       414  0.0  0.0  16644  1104 tty1     S    14:20   0:00 grep --color=auto sshd
```

****



## 终止进程 `kill`和 `killall`



### 基本介绍:

 

若是某个进程执行一半需要停止时，或是已消了很大的系统资源时，此时可以考虑停止该进程。使用 kill 命令来完成此项任务。

 终止父进程时，它下面的子进程也会终止

### 基本语法：

kill	[选项] 进程号（功能描述：通过进程号杀死进程）

killall 进程名称（功能描述：通过进程名称杀死进程，也支持通配符，这在系统因负载过大而变得很慢时很有用）



**两者的区别：kill是根据进程号来杀死进程，而killall是通过进程名称来杀死进程**

###  常用选项：

-9 :表示**强制进程立即停止**

有些进程会忽略 `kill`指令，就需要加参数 `-9`来表示强制终止



强制杀死MySQL

```shell
root@LAPTOP-UN694I4M:/home/mochou5# kill  6365
root@LAPTOP-UN694I4M:/home/mochou5# ps -aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   8892   264 ?        Ssl  09:30   0:00 /init
root       861  0.0  0.0   8904   208 tty1     Ss   15:12   0:00 /init
mochou5    862  0.0  0.0  18692  3292 tty1     S    15:12   0:00 -bash
root      3039  0.0  0.0  18500  2100 tty1     S    16:33   0:00 su root
root      3040  0.0  0.0  17676  2252 tty1     S    16:33   0:00 bash
root      3630  0.0  0.0  18488  2020 tty1     S    16:36   0:00 su mochou5
mochou5   3631  0.0  0.0  18504  3248 tty1     S    16:36   0:00 bash
root      5989  0.0  0.0  18500  2116 tty1     S    17:04   0:00 su root
root      5990  0.0  0.0  17832  2364 tty1     S    17:04   0:00 bash
mysql     6365  0.0  0.0  10660   776 ?        S    17:07   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     6754  0.0  0.6 1937436 56836 ?       Sl   17:07   0:01 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plroot      6788  0.0  0.0  19496  2028 tty1     R    17:44   0:00 ps -aux
root@LAPTOP-UN694I4M:/home/mochou5# kill  -9 6365 6754
root@LAPTOP-UN694I4M:/home/mochou5# ps -aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   8892   264 ?        Ssl  09:30   0:00 /init
root       861  0.0  0.0   8904   208 tty1     Ss   15:12   0:00 /init
mochou5    862  0.0  0.0  18692  3292 tty1     S    15:12   0:00 -bash
root      3039  0.0  0.0  18500  2100 tty1     S    16:33   0:00 su root
root      3040  0.0  0.0  17676  2252 tty1     S    16:33   0:00 bash
root      3630  0.0  0.0  18488  2020 tty1     S    16:36   0:00 su mochou5
mochou5   3631  0.0  0.0  18504  3248 tty1     S    16:36   0:00 bash
root      5989  0.0  0.0  18500  2116 tty1     S    17:04   0:00 su root
root      5990  0.0  0.0  17832  2364 tty1     S    17:04   0:00 bash
root      6789  6.0  0.0  19496  2028 tty1     R    17:45   0:00 ps -aux
root@LAPTOP-UN694I4M:/home/mochou5#
```





****



## 查看进程树 `pstree [选项]`



**基本语法：**

`pstree [选项]`

可以更直观看进程的信息 {类似于文件树 }

进程树上有子进程和父进程。父进程是主干，子进程 是枝叶



**常用选项：**

`ps -p`  : 显示进程的 PID

`ps -u`  : 显示进程的所属用户



**应用实例：**

案例 1：请用树状的形式显示进程的 pid

```shell
root@LAPTOP-UN694I4M:/# pstree -p
init(1)─┬─init(861)───bash(862)───su(875)───bash(876)───pstree(890)
        └─{init}(4)
```

案例 2：请用树状的形式进程的用户

```shell
root@LAPTOP-UN694I4M:/# pstree -u
init─┬─init───bash(mochou5)───su(root)───bash───pstree
     └─{init}
```





****



## 服务(Service)管理   {下面会用mysql作为演示，可以先装MySQL}



**什么是服务？**

服务(service) 本质就是进程，但是是运行在后台的，通常都会监听某个端口，等待其它程序的请求，比如(mysql , sshd 防火墙等)，因此**我们又称为守护进程，是 Linux 中非常重要的知识点**。

在 CentOS7.0 后 不再使用 service ,而是 systemctl



**原理图：**

![](C:\Users\fucker\Pictures\Linux33.PNG)





**操作服务：**`service	服务名 [start或者stop或者restart或者reload或者 status]`

`start`代表启动

`stop`代表停止

`restart`代表重启服务

`reload`代表

`status`代表查看

**查看所有服务：**   `service --status-all`



```shell
root@LAPTOP-UN694I4M:/home/mochou5# service --status-all
 [ - ]  acpid
 [ - ]  apparmor
 [ ? ]  apport
 [ - ]  atd
 [ - ]  console-setup.sh
 [ - ]  cron
 [ ? ]  cryptdisks
 [ ? ]  cryptdisks-early
 [ - ]  dbus
 [ - ]  ebtables
 [ ? ]  hwclock.sh
 [ + ]  irqbalance
 [ + ]  iscsid
 [ - ]  keyboard-setup.sh
 [ - ]  kmod
 [ - ]  lvm2
 [ + ]  lvm2-lvmetad
 [ + ]  lvm2-lvmpolld
 [ - ]  lxcfs
 [ - ]  lxd
 [ - ]  mdadm
 [ - ]  mdadm-waitidle
 [ + ]  mysql
 [ ? ]  networking
 [ + ]  open-iscsi
 [ - ]  open-vm-tools
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ - ]  procps
 [ - ]  redis-server
 [ - ]  rsync
 [ - ]  rsyslog
 [ - ]  screen-cleanup
 [ - ]  ssh
 [ - ]  udev
 [ - ]  ufw
 [ - ]  unattended-upgrades
 [ - ]  uuidd
 [ - ]  x11-common
root@LAPTOP-UN694I4M:/home/mochou5#
```



**启动mysql服务**

```shell
root@LAPTOP-UN694I4M:/home/mochou5# service mysql start
 * Starting MySQL database server mysqld

                                                                                                                                                                                      [ OK ]
 
root@LAPTOP-UN694I4M:/home/mochou5#
```



**查看mysql服务是否启动**

```shell
root@LAPTOP-UN694I4M:/home/mochou5# service mysql status
 * MySQL is stopped.
```



**重启mysql服务**



```shell
root@LAPTOP-UN694I4M:/home/mochou5# service mysql restart
 * Stopping MySQL database server mysqld                                                                                                                                              [ OK ]
 * Starting MySQL database server mysqld



                                                                                                                                                                                      [ OK ]
root@LAPTOP-UN694I4M:/home/mochou5#
```



**停止mysql服务**

```
root@LAPTOP-UN694I4M:/home/mochou5# service mysql stop
 * Stopping MySQL database server mysqld                                                                                                                                              [ OK ]
root@LAPTOP-UN694I4M:/home/mochou5#
```

****



## 查看服务名称：`setup` ,CentOS是 `nmtui`

上面这种Ubuntu也用不了。。。

使用 `service --status-all`效果一样



另外一种查看 `/etc/init.d`文件



```shell
root@LAPTOP-UN694I4M:/home/mochou5# ls -l /etc/init.d
总用量 180
-rwxr-xr-x 1 root root 2269 4月  22  2017 acpid
-rwxr-xr-x 1 root root 4335 3月  23  2018 apparmor
-rwxr-xr-x 1 root root 2802 11月 21  2017 apport
-rwxr-xr-x 1 root root 1071 8月  22  2015 atd
-rwxr-xr-x 1 root root 1232 4月  19  2018 console-setup.sh
-rwxr-xr-x 1 root root 3049 11月 16  2017 cron
-rwxr-xr-x 1 root root  937 3月  18  2018 cryptdisks
-rwxr-xr-x 1 root root  978 3月  18  2018 cryptdisks-early
-rwxr-xr-x 1 root root 2813 11月 16  2017 dbus
-rwxr-xr-x 1 root root 4489 6月  29  2018 ebtables
-rwxr-xr-x 1 root root 3809 2月  15  2018 hwclock.sh
-rwxr-xr-x 1 root root 2444 10月 25  2017 irqbalance
-rwxr-xr-x 1 root root 1503 12月 12  2018 iscsid
-rwxr-xr-x 1 root root 1479 2月  16  2018 keyboard-setup.sh
-rwxr-xr-x 1 root root 2044 8月  16  2017 kmod
-rwxr-xr-x 1 root root  695 12月  3  2017 lvm2
-rwxr-xr-x 1 root root  571 12月  3  2017 lvm2-lvmetad
-rwxr-xr-x 1 root root  586 12月  3  2017 lvm2-lvmpolld
-rwxr-xr-x 1 root root 2378 11月 23  2018 lxcfs
-rwxr-xr-x 1 root root 2240 11月 24  2018 lxd
-rwxr-xr-x 1 root root 2653 1月  30  2019 mdadm
-rwxr-xr-x 1 root root 1249 1月  30  2019 mdadm-waitidle
-rwxr-xr-x 1 root root 5607 1月  12  2018 mysql
-rwxr-xr-x 1 root root 4597 11月 25  2016 networking
-rwxr-xr-x 1 root root 2503 12月 12  2018 open-iscsi
-rwxr-xr-x 1 root root 1846 12月 14  2018 open-vm-tools
-rwxr-xr-x 1 root root 1366 4月   4  2019 plymouth
-rwxr-xr-x 1 root root  752 4月   4  2019 plymouth-log
-rwxr-xr-x 1 root root 1191 1月  18  2018 procps
-rwxr-xr-x 1 root root 1614 4月   3  2018 redis-server
-rwxr-xr-x 1 root root 4355 12月 13  2017 rsync
-rwxr-xr-x 1 root root 2864 1月  15  2018 rsyslog
-rwxr-xr-x 1 root root 1222 5月  22  2017 screen-cleanup
-rwxr-xr-x 1 root root 3837 1月  26  2018 ssh
-rwxr-xr-x 1 root root 5974 4月  21  2018 udev
-rwxr-xr-x 1 root root 2083 8月  16  2017 ufw
-rwxr-xr-x 1 root root 1391 4月  29  2019 unattended-upgrades
-rwxr-xr-x 1 root root 1306 10月 16  2018 uuidd
-rwxr-xr-x 1 root root 2757 1月  20  2017 x11-common
root@LAPTOP-UN694I4M:/home/mochou5#
```



**CentOS7**使用 `systemctl list-units --type=service`可以达到同样的效果



****



ubuntu也是 `systemctl`，但是WSL中貌似有巨坑，用 `service`指令吧



```
由于Linux环境应用程序（如Ubuntu，Debian，OpenSuse或Kali）不支持为Linux操作系统提供基本构建块的Systemd，因此我们无法使用reboot或使用systemctl命令来管理systemd服务。 那么，在这种情况下，如果我们要为Linux Lxssmanager服务重启windows子系统，该怎么办？ 在本文中，您将获得简单的解决方案。

```

https://blog.csdn.net/A1553225534/article/details/99678282

还有这个

https://blog.csdn.net/zhangpeterx/article/details/95855326







ubuntu查看隔离级别

```
root@LAPTOP-UN694I4M:/home/mochou5# systemctl get-default
graphical.target
```



****

## 动态监控进程 ： `top`

有点像Windows下会自动更新的任务管理器

top 与 ps 命令很相似。它们都用来显示正在执行的进程。Top 与 ps 最大的不同之处，在于 top 在执行一段时间可以更新正在运行的的进程。



**基本语法：**

`top [选项]`



**选项说明：**



| 选项    | 功能                                                         |
| ------- | ------------------------------------------------------------ |
| -d 秒数 | 指定top命令每隔几秒更新。默认是3秒在top命令的交互模式当中可以执行的命令： |
| -i      | 使top不显示任何闲置或者僵尸进程                              |
| -p      | 通过指定监控进程ID来仅仅监控某个进程的状态                   |



**交互操作说明：**

| 操作         | 功能                          |
| ------------ | ----------------------------- |
| P{P是大写的} | 以CPU使用率排序，默认就是此项 |
| M            | 以内存的使用排序              |
| N            | 以PID排序                     |
| q            | 退出top                       |



###  应用实例：

案例 1.监视特定用户

top：输入此命令，按回车键，查看执行的进程。

*{u：然后输入“u”回车，再输入用户名，即可}  直接top也可以*



输入 `top`指令，就会进入这样一个界面

![](C:\Users\fucker\Pictures\Linux34.PNG)



这个界面，每隔3秒就会刷新一次{因此上图和下面的数据会有点区别，以下面的数据为准}



```
top - 21:02:00 up 11:31,  0 users,  load average: 0.52, 0.58, 0.59
任务:   6 total,   1 running,   5 sleeping,   0 stopped,   0 zombie
```

`21:02:00`表示的是当时间

`up 11:31`，机器开启运行了多少小时

` 0 users`当前登录系统的用户数。。。额（为0难道是root不算？？）

`load average: 0.52, 0.58, 0.59`表示的是当前机器的负载均衡数据

`0.52, 0.58, 0.59`，最大为1{0.52相当于百分之52，其他的也是类似}

**如果负载均衡三个值加起来除以3，达到0.7就表示系统有点跑不动了。。。**

`任务:   6 total,   1 running,   5 sleeping,   0 stopped,   0 zombie`

任务这个表示的是任务状态，total是任务总数{6}，running是正在运行的任务{1个},sleeping是正在睡眠的任务{5个}，stopped是停止的进程数量{0个}，zombie是僵尸状态的任务{0个}



```
%Cpu(s):  2.5 us,  2.8 sy,  0.0 ni, 94.6 id,  0.0 wa,  0.1 hi,  0.0 si,  0.0 st
KiB Mem :  8258868 total,  2073168 free,  5956348 used,   229352 buff/cache
KiB Swap: 25165824 total, 24855288 free,   310536 used.  2168788 avail Mem
```

`%Cpu(s)`代表CPU使用情况，`2.5 us`是用户使用2.5%,`2.8 sy`是系统使用了2.8%, `94.6 id`表示 还空闲94.6%

`KiB Mem`代表内存占用情况，`8258868 total`内存总共8个G，`2073168 free`使用了这么多，`5956348 used`还空闲这么多

`KiB Swap`代表虚拟内存使用情况，其他的free，used和上面类似





杀死进程，输入 k,然后回车

```shell
PID to signal/kill [default pid = 1]                                                                                    进 USER      PR  NI    VIRT    RES    SHR   %CPU %MEM     TIME+ COMMAND
    1 root      20   0    8892    276    244 S   0.0  0.0   0:00.48 init
```



`PID to signal/kill [default pid = 1]`后面填要杀死的进程号



随意填一个55555  ，然后回车

`Send pid 55555 signal [15/sigterm]   `

再次回车

` Failed signal pid '55555' with '15': 没有那个进程`



**`q`退出交互界面**

退出后

```shell
任务:   6 total,   1 running,   5 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.0 us,  3.8 sy,  0.0 ni, 87.0 id,  0.0 wa,  0.1 hi,  0.0 si,  0.0 st
KiB Mem :  8258868 total,  2209724 free,  5819792 used,   229352 buff/cache
KiB Swap: 25165824 total, 24830628 free,   335196 used.  2305344 avail Mem

进 USER      PR  NI    VIRT    RES    SHR   %CPU %MEM     TIME+ COMMAND
10498 root      20   0   19604   2076   1544 R   0.7  0.0   0:00.31 top
    1 root      20   0    8892    276    244 S   0.0  0.0   0:00.48 init
 9132 root      20   0    8904    220    176 S   0.0  0.0   0:00.00 init
 9133 mochou5   20   0   18692   3272   3176 S   0.0  0.0   0:00.18 bash
 9145 root      20   0   18500   2024   1996 S   0.0  0.0   0:00.13 su
 9146 root      20   0   17832   2312   2224 S   0.0  0.0   0:00.28 bash
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
root@LAPTOP-UN694I4M:/home/mochou5#   
```





指定系统状态更新的时间(每隔 10 秒自动更新， 默认是 3 秒)：

 `top -d 10` 修改默认刷新时间

这样就修改为10秒了{不便于演示}

****

# 查看系统网络情况 `netstat`    {重要}



**基本语法：**

`netstat`  选项

`natstat -anp`      {一般使用这个}

**选项说明**

| 选项 | 功能               |
| ---- | ------------------ |
| -an  | 按一定顺序排列输出 |
| -p   | 显示哪个进程在调用 |





**应用实例：**

查看所有的

```shell
root@LAPTOP-UN694I4M:/home/mochou5# netstat -anp
激活Internet连接 (服务器和已建立连接的)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
活跃的UNIX域套接字 (服务器和已建立连接的)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name     路径
root@LAPTOP-UN694I4M:/home/mochou5#
```



WSL这特么巨坑。。。。



看演示的 

![](C:\Users\fucker\Pictures\Linux35.png)







请查看服务名为 mysql的服务的信息

如果是没有的。。。

```
root@LAPTOP-UN694I4M:/home/mochou5# netstat -anp |grep mysql
root@LAPTOP-UN694I4M:/home/mochou5#
```

`netstat -anp |grep XXX`

XXX表示要监听的网络服务

将所有的网络服务通过 `grep`加上指定服务名过滤，达到只显示想看的的的



这个是监听ssd

![](C:\Users\fucker\Pictures\Linux36.png)





****

# **redis在WSL上，环境的搭建**



先安装

```
mochou5@LAPTOP-UN694I4M:~$ sudo apt-get install redis-server
```





```
mochou5@LAPTOP-UN694I4M:~$ nano /etc/redis/redis.conf
mochou5@LAPTOP-UN694I4M:~$ sudo nano /etc/redis/redis.conf
mochou5@LAPTOP-UN694I4M:~$ sudo service redis-server restart
Stopping redis-server: redis-server.
Starting redis-server: redis-server.
mochou5@LAPTOP-UN694I4M:~$ su root
密码：
root@LAPTOP-UN694I4M:/home/mochou5# cd /
root@LAPTOP-UN694I4M:/# redis-cli
127.0.0.1:6379> ping
PONG
127.0.0.1:6379> cd /
(error) ERR unknown command 'cd'
127.0.0.1:6379> exit
root@LAPTOP-UN694I4M:/#
```

****





https://www.zhihu.com/question/339939686/answer/792426363



**为什么要用WSL？**

**体验Linux系统命令行(实际开发也没有啥图形化界面)+学Redis**



都有涉及Docker用的不太多。首推WSL

如果你是想体验Linux命令行，使用bash，首推WSL。安装简单，操作简单，上手难度最低，体验也很棒。什么，想体验图形界面，讲真Linux的图形界面没啥好玩的，非要用的话可以在WSL里装个LXDE，gnome啥的再加个xrdp或vncserver然后简单体验一下，真想用图形界面就VM或双系统。

VM的话可以体验到更完整的Linux，不过图形界面会让你分心，比如安装输入法，界面美化，安装字体，各种Windows软件(通讯类)。就是虚拟机用着始终没有真机双系统爽就是了。但是这是能让你既能使用Linux桌面和完整Linux内核又能使用Windows软件的方案。

Docker的话，貌似不符合你这个需求，体验Linux为什么要用Docker，你在Windows上用Docker实际上也要用到虚拟机Hyper-V或VM，既然要用虚拟机，为啥不直接用虚拟机装个Linux？Docker主要是用来方便地部署应用环境的，在这体验Linux可能会各种不爽(Docker上跑个某Linux发行版真不如你直接去用虚拟机)，然而虚拟机效率不如真机，WSL可能介于之间？

另外WSL2可能是个不错的选择，不过实际上也是用了虚拟机技术，使用WSL2你甚至可以直接在WSL2上用Docker，体验应该还不错。

我还没用过WSL2，感觉WSL就够我用了，等WSL2更成熟一些后可能会升级过去。

总之首推WSL(没有图形界面)，然后VM(有图形界面效率低)，然后双系统(最完整的体验)，最后Docker吧

****



# MYSQL安装以及其坑



https://blog.csdn.net/weixin_43530726/article/details/91303898

参考这篇

单纯的改密码，参考第2步，先用免密码登入进去，再改密码



```
update user set authentication_string=password("root") where user="root";
```



```
update user set authentication_string=password("root"),plugin='mysql_native_password' where user='root';
```

