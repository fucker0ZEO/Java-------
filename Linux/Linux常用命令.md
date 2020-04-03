# Linux常用命令 (1)

## 1.man 你不会用的命令

例如

```linux
man date
```

表示的就是不知道date这个命令是什么，类似于在API文档中查API

结果：

```Linux
DATE(1)                                User Commands                               DATE(1)

NAME
       date - print or set the system date and time

SYNOPSIS
       date [OPTION]... [+FORMAT]
       date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]

DESCRIPTION
       Display the current time in the given FORMAT, or set the system date.

       Mandatory arguments to long options are mandatory for short options too.

       -d, --date=STRING
              display time described by STRING, not 'now'

       --debug
              annotate the parsed date, and warn about questionable usage to stderr

       -f, --file=DATEFILE
              like --date; once for each line of DATEFILE

       -I[FMT], --iso-8601[=FMT]
              output  date/time  in  ISO  8601  format.   FMT='date'  for  date  only (the
              default), 'hours', 'minutes', 'seconds', or 'ns' for date and  time  to  the
              indicated precision.  Example: 2006-08-14T02:34:56-06:00

       -R, --rfc-email
              output date and time in RFC 5322 format.  Example: Mon, 14 Aug 2006 02:34:56
              -0600

       --rfc-3339=FMT
              output date/time in RFC 3339 format.  FMT='date',  'seconds',  or  'ns'  for
              date   and   time   to   the   indicated   precision.   Example:  2006-08-14
              02:34:56-06:00

       -r, --reference=FILE
              display the last modification time of FILE

       -s, --set=STRING
              set time described by STRING

       -u, --utc, --universal
              print or set Coordinated Universal Time (UTC)

       --help display this help and exit

 Manual page date(1) line 1 (press h for help or q to quit)
```

然后进入这个文档界面中，**回车键/方向键中的下 表示文档向下走，方向键中的上表示向上走**，而最下面输入q，表示跳出，然后回到原界面

**第2种方式 具体命令 --help**

例如：

```linux
date --help
```

**第3种方式  info 具体命令**

例如：

```linux
info date
```

同样q是退出 

```
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse deb-src http$
```



# linux子系统ubuntu设置root用户以及普通用户



ubuntu切换root：使用su root命令

，此时会提示输入密码，可是怎么也输不对，提示“Authentication failure”，

此时有两种情况一个是真的是密码错了，另一种就是刚安装好的Linux系统，没有给root设置密码。

1 打开Ubuntu，输入命令：su root，回车提示输入密码，怎么输入都不对

2 给root用户设置密码：命令：sudo passwd root  。输入密码，并确认密码。

3 重新输入命令：su root  。然后输入密码：发现可以切换到root权限了。

4 使用su 普通用户名  命令，切换到普通用户。

密码设为 用户名加有1到 x的数字

root用户也是同样的



```
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties

deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted

deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted multiverse universe #Added by software-properties

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted

deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted multiverse universe #Added by software-properties

deb http://mirrors.aliyun.com/ubuntu/ xenial universe

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe

deb http://mirrors.aliyun.com/ubuntu/ xenial multiverse

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates multiverse

deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse

deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse #Added by software-properties

deb http://archive.canonical.com/ubuntu xenial partner

deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted

deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted multiverse universe #Added by software-properties

deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe

deb http://mirrors.aliyun.com/ubuntu/ xenial-security multiverse

```



```
sudo nano /etc/apt/sources.list
export LANG="zh_CN.UTF-8"
export LC_ALL="zh_CN.UTF-8"
```



```
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
粘贴好 然后Ctrl+O，按回车，再Ctrl+X，保存退出。输入：

Bash
sudo apt-get update
更新源列表。
然后更新已安装使所有软件：

Bash
sudo apt-get upgrade
（题外话：sudo的时候输入密码麻烦，修改/etc/sudoers如下内容即可（改为nopasswd:ALL）：

如果去除每次输入密码验证的话，输入命令：

Bash
sudo nano /etc/sudoers
然后更改内容为：你的用户名 ALL=(ALL) NOPASSWD: ALL

有的时候你的将用户设了nopasswd，但是不起作用，原因是被后面的group的设置覆盖了，需要把group的设置也改为nopasswd。

你的用户名 ALL=(ALL) NOPASSWD: ALL

%admin ALL=(ALL) NOPASSWD: ALL

如上图所示。然后Ctrl+O，按回车，再Ctrl+X，保存退出。）

 

二、安装中文字体及设置

查看系统类型：

Bash
cat /proc/version
查看中文字体：

Bash
fc-list :lang=zh-cn
系统没中文语言包的话，先安装中文语言包：

输入命令：

Bash
sudo apt-get install language-pack-zh-hans
接着输入：

Bash
sudo apt-get install -y fonts-wqy-zenhei
（没改过sudo的会提示输入密码，就输入开始你直接设置的密码回车就好了，按照教程来的不会提示输入密码。）



或者：

Bash
sudo apt install -y fonts-wqy-microhei
接着执行

1、输入命令：vim .profile    或者输入：nano .profile   （随意输入一个，建议nano的，好用）

比如输入：

Bash
nano .profile
然后在文本最末尾添加以下内容：

BASIC
export LANG="zh_CN.UTF-8"
export LC_ALL="zh_CN.UTF-8"
如下图；



然后Ctrl+O，按回车，再Ctrl+X，保存退出。

2、输入执行：

Bash
sudo dpkg-reconfigure locales
按键盘pagedown往下找到并且选择zh_CN.UTF-8（按空格键选择，按Tab键移动到确定，按回车键确定）



到下一步，选择zh_CN.UTF-8（按回车键确定）



之后等待生成结束。



3、执行locale查看 ，发现系统语言已经是中文了，



安装完成后重启系统就好了。

在windows的cmd窗口输入来重启Ubuntu系统：

Bash
net stop LxssManager
echo.关闭系统

Bash
net start LxssManager
echo.开启系统

 

三、安装桌面环境，两种方法（不想要"桌面图形界面"的同学可以忽略这步）

(推荐xfce桌面，也就是第二种方法)

进入正题：

有以下两种方法，只能选择其中一种哦。

先输入刷新：

Bash
sudo apt-get update
然后输入更新一下：

Bash
sudo apt-get upgrade
第1种方法；安装Tasksel工具：

Bash
sudo apt-get install tasksel -y
    然后输入：

Bash
sudo tasksel
将打开一个基于curses的GUI。使用键盘箭头键，向下滚动以选择Ubuntu desktop然后OK（按空格键选择，按Tab键移动到确定，按回车键确定），进度条跑完后，即可自动安装完成ubuntu桌面。

安装完成后重启系统就好了。

(提示:如果看不到桌面，显示空白或者鼠标是X的话那么执行：sudo apt-get install --no-install-recommends ubuntu-desktop gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal 然后把./vnc/xstartup修改为如下：

命令：

Bash
sudo nano .vnc/xstartup
之后，全部替换为以下内容：
BASIC
XAUTHORITY=$HOME/.Xauthority
export XAUTHORITY
LANG=zh_CN.UTF-8
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &
然后重启就能看见桌面了)
在windows的cmd窗口输入来重启Ubuntu系统：

Bash
net stop LxssManager
echo.关闭系统

Bash
net start LxssManager
echo.开启系统

 

第2种方法；输入命令：

Bash
sudo apt-get install xubuntu-desktop
之后会自动安装桌面。（gnome桌面、xfce4桌面、Unity桌面、kde桌面等可自行选择，只需命令sudo install xxx就可安装了）

如果界面管理器出错就安装（没有就不用管这句）：sudo apt install lightdm 安装完成后重启系统就好了。

（题外话；桌面管理器切换命令：sudo dpkg-reconfigure lightdm   假如要卸载的话,命令是：sudo apt remove gnome* --purge）

（如果桌面安装出错，出现E: Sub-process /usr/bin/dpkg returned an error code (1)的话，以下是解决方法：

输入：sudo mv /var/lib/dpkg/info /var/lib/dpkg/info.bak    //现将info文件夹更名

输入：sudo mkdir /var/lib/dpkg/info    //再新建一个新的info文件夹

输入：sudo apt-get update

输入你刚才安装出错的：apt-get -f install xxx（xxx表示某某某）：


Bash
比如再次输入命令：sudo apt-get install xubuntu-desktop
输入：sudo mv /var/lib/dpkg/info/* /var/lib/dpkg/info.bak

//执行完上一步操作后会在新的info文件夹下生成一些文件，现将这些文件全部移到info.bak文件夹下

输入：sudo rm -rf /var/lib/dpkg/info     //把自己新建的info文件夹删掉

输入：sudo mv /var/lib/dpkg/info.bak /var/lib/dpkg/info      //把以前的info文件夹重新改回名字

到此问题顺利解决）（如果之后提示：W: APT had planned for dpkg to do more than it reported back (0 vs 4).

   Affected packages: blueman:amd64 的话，输入：sudo dpkg -C    就可以解决）

（对于ightdm启动器；另外如果你自己需要重新加root登录的话，那么配置root登陆权限：

默认情况是不允许用root帐号直接登录图形界面的。这可以通过修改sudo nano /usr/share/lightdm/lightdm.d/50-ubuntu.conf 文件来允许root直接登录，增加

greeter-show-manual-login=true allow-guest=false .

登录之后如果会每次弹一个小错误，然后

，/root/.profile文件中将 mesg n||true 修改为 tty -s && mesg n ||true）
然后在windows的cmd窗口输入来重启Ubuntu系统：
Bash
net stop LxssManager
echo.关闭系统

Bash
net start LxssManager
echo.开启系统

然后愉快的使用ubuntu吧！

 

四、中文输入法、谷歌浏览器安装 和 连接桌面

4.1、中文输入法和浏览器安装

安装谷歌浏览器命令：

Bash
sudo apt install *chrome*
安装中文输入法命令：
Bash
sudo apt install -y fcitx fcitx-googlepinyin*
然后在/home/某某某/.profile文件添加代码；

列如、输入命令：

Bash
sudo nano .profile
然后复制以下代码粘贴进去：

BASIC
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
然后Ctrl+O，按回车，再Ctrl+X，保存退出。

这样就可以了。

4.2、连接桌面：

桌面连接有vnc和xrdp两种方法。 

第一种方法，先安装VNC：

Bash
sudo apt-get install vnc4server
接下来先输入VNC启动命令：

Bash
sudo vncserver -geometry 1600x900 :0
（命令结尾的1600x900是表示屏幕分辨率，:0是表示桌面端口号为零，分辨率和端口号都可以随意自行更改，只要不出错就行。） 

然后会提示设置连接密码，会提示输入两次，然后就能看见为0的端口号在运行。


之后输入VNC结束命令：


Bash
sudo vncserver -kill :0
然后把xstartup修改为如下：

先输入命令：

Bash
sudo nano .vnc/xstartup
然后复制以下内容粘贴到xstartup文本里：
 (桌面空白不显示桌面图像也可用此方法解决)


BASIC
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
startxfce4 &
然后Ctrl+O，按回车，再Ctrl+X，保存退出。

4、重新启动vncserver

再次启动vnc并且设置vnc分辨率：

Bash
sudo vncserver -geometry 1600x900 :0
（分辨率可以自行修改）
（题外话：结束vnc进程命令为，0表示为桌面端口号 ：sudo vncserver -kill :0 ）

然后使用vnc客户端连接即可查看桌面，如果显示端口是4那么在客户端连接的就是127.0.0.1:4 (每个人的不一样，可自行修改，一般默认是0)



VNC连接截图示例：



桌面显示成功后截图示例：



 

查看ubuntu版本方法：

输入安装版本查看器：

Bash
sudo apt-get install neofetch
然后输入查看即可：

Bash
neofetch
（也可以使用：sudo apt-get install linuxlogo  二选一 ，查看方式为：linuxlogo）



 

第二种xrdp桌面（建议用第一种，这种兼容性差）：

这个方法是使用微软自带远程桌面软件来显示的

1、安装xrdp，输入：

Bash
sudo apt-get install xrdp
2、设置使用3390端口(设置3390端口的目的是避免和Windows系统自带端口冲突)：

Bash
sudo sed -i 's/port=3389/port=3390/g' /etc/xrdp/xrdp.ini
然后输入:

Bash
sudo echo xfce4-session >~/.xsession
再输入：

sudo service xrdp restart
然后就可以打开软件连接了。



文字教程到此结束，下面是视频教程，方便看不懂文字教程的伙伴：



心得：此方式运行原理是类似于容器运行，相当于沙盒，加上微软本身开发接口支持，所以在配置偏低电脑上发挥的性能还是很可以的。

标签： 互联网 技术 教程 搭建

本文地址： https://www.tkdcz.top/post/46.html
文章来源： TKDCZ
版权声明：本站部分文章或资源为原创，部分文章或资源收集于互联网上的其他作者，若要转载，请务必先考虑保护原作者版权。
赞 23
上一篇
V4蝰蛇音效-magisk刷入模块包分享！
下一篇
安卓系统下用Linux deploy安装Ubuntu系统(电脑系统的感觉)-教程详细且带视频教程
相关文章


本站免费FRP内网穿透服务分享-适合没有公网ip的人


VOYO v3二合一平板笔记本原生BIOS程序分享-vbook-v3


适合初学者的Linux(Ubuntu)下搭建网页服务器apache2+php+mysql(mariadb)教程


Ubuntu 18.04 安装 python3.7-编译安装


一个可以自动更新动态域名解析(DDNS)的脚本分享-适合有公网却是动态ip的人-比如远程访问家中树莓派


Windows10应用商店崩溃闪退等问题的修复方法

发表评论 （已有42条评论）



发布评论
评论列表


高高手@回复2019-05-05 12:57:58
好长的文字教程哦


mpc@回复2019-05-06 11:38:23
很厉害！！！好用！！！


访客@回复2019-05-23 16:49:38
显示找不到VNCSERVER怎么办


访客@回复2019-05-25 01:12:50
@访客 输入卸载命令sudo apt remove vnc* --purge 然后输入安装sudo apt install -y vnc*


访客@回复2019-05-26 11:20:57
中文字体安装不上，显示E: Unable to locate package ttf-wqy-zenhei


TKDCZ@回复2019-05-26 11:31:19
@访客 你输入sudo apt-get install -y fonts-wqy-zenhei试试，而且要把源换成国内的


lhzherry@回复2019-05-29 14:42:04
xrdp的桌面用不了，怎么删了


TKDCZ@回复2019-05-30 11:58:56
@lhzherry 删除命令sudo apt remove *xrdp* --purge


小白@回复2019-07-10 14:13:01
手贱点了锁屏，然后就没反应了


fzl@回复2019-07-15 23:33:42
为什么安装了chrome后打不开呢，没反应啊


TKDCZ@回复2019-07-17 15:52:35
@fzl 估计组件不齐，你可以试试sudo apt-get update和sudo apt-get install libnss3，或者还有sudo google-chrome --no-sandbox


forever@回复2019-08-19 16:54:42
在更新阿里源时会出错


TKDCZ@回复2019-08-20 15:08:48
@forever 可以换个清华源试试，也可以换网易源和中科大源。


默@回复2019-08-28 09:50:30
楼主 在输入VNC启动命令时，提示sudo: vncserver：找不到命令，这是怎么回事呀！


TKDCZ@回复2019-08-28 11:02:35
@默 原因是没有安装vnc，输入命令安装就可以了sudo apt-get install vnc4server


默@回复2019-08-29 17:22:18
@TKDCZ 楼主，在安装 vnc4server时，出现下面的错误：
dpkg: 错误: 无法新建文件 '/var/lib/dpkg/info/format-new': 没有那个文件或目录
E: Sub-process /usr/bin/dpkg returned an error code (2)
我并没有找到var/lib/dpkg这个目录在哪


访客@回复2019-08-31 13:15:18
@默 你这个报错 文章中间部分有解决方法，照着做就可以了


默@回复2019-08-29 17:44:48
@TKDCZ 还有哦楼主，安装好桌面环境后，也没有显示出桌面


过路人@回复2019-09-16 14:57:28
@默 可能是没有修改好xstartup文件导致，可以重新照文章中修改试试


高手@回复2019-10-13 17:59:10
装了多个桌面如何切换啊！


访客@回复2019-10-13 18:46:49
@高手 装多个桌面不兼容，无法切换，会自动默认位最后安装的一个


与春如熙@回复2019-11-20 21:52:53
安装好之后，所有浏览器都无法联网，包括应用商店，chrome浏览器点击不出界面，输入法切换不了中文，怎么解决


过来人@回复2019-11-21 19:34:59
@与春如熙 安装后可能会遇到各种小问题，因为每个人电脑运行环境都有点小区别，且问题不统一，你的问题我没遇到过，所以动手能力强建议自行摸索解决


shadow@回复2019-11-22 13:43:40
请问安装vnc连接桌面每次电脑重启后不能重新连接，需要修改，例如sudo vncserver -geometry 1600x900 :0改为sudo vncserver -geometry 1600x900 :1才能正常连接，这种情况怎么解决


过路的@回复2019-11-24 22:58:35
@shadow 你输入sudo vncserver -kill :0既可


shadow@回复2019-11-26 09:24:54
@过路的 没有解决，显示No such process ；此外sudo vncserver -geometry 1600x900 :0重新打开时会提示A VNC server is already running as :0


过路人@回复2019-12-06 09:50:46
@shadow 显示running as :0就可以了啊，直接打开vnc就能连接了


分解机盾@回复2019-12-05 00:04:00
无法显示桌面怎么办


过路人@回复2019-12-23 14:29:51
@分解机盾 看网站结尾以上空白修复方法可解决桌面没有


John破喉咙@回复2020-01-23 15:19:19
启动完 sudo vncserver -geometry 1600x900 :0
报错
Warning: DESKTOP-78L0SHS:0 is taken because of /tmp/.X0-lock
Remove this file if there is no X server DESKTOP-78L0SHS:0
A VNC server is already running as :0######本文来自：TKDCZ网阁，原地址：https://www.tkdcz.top/post/46.html


John破喉咙@回复2020-01-23 15:19:44
@John破喉咙 咋搞啊 QAQ


John破喉咙@回复2020-01-23 17:57:34
我跟着UP操作完以后 桌面上并没有vnc4的桌面快捷方式 咋回事


过路人@回复2020-01-23 22:01:39
@John破喉咙 桌面没有快捷方式的话，你也可以右键vnc然后发送快捷方式到桌面。


John破喉咙@回复2020-01-29 11:40:57
您好 请问 在子系统里 我这边无法输入中文是什么问题 怎么解决 （全部是照着文本和视频的教程来操作的） 谢谢


过路人@回复2020-01-29 13:08:56
@John破喉咙 你的原因可能是中文输入法安装失败了，输入sudo apt-get install ibus 然后输入apt-get install ibus-libpinyin 更改输入法为中文试试


John破喉咙@回复2020-01-29 13:53:12
@过路人 感谢 操作后 提示我如下
E：无法打开锁文件 /var/lib/dpkg/lock-frontend ibus-libpinyin
E：无法获取 dpkg 前段锁 (/var/lib/dpkg/lock-frontend)，请查询是否正在以root用户运行？


John破喉咙@回复2020-01-29 13:54:50
@过路人 上面的打错字了 正确的如下：
E：无法打开锁文件 /var/lib/dpkg/lock-frontend - open（13：权限不够）
E：无法获取 dpkg 前段锁 (/var/lib/dpkg/lock-frontend)，请查询是否正在以root用户运行？


过路人@回复2020-01-29 17:56:17
@John破喉咙 忘记提示你了，命令开头加sudo才行，比如sudo apt-get install fcitx


John破喉咙@回复2020-01-29 18:48:32
想问下 这个环境里怎么安装Py Charm


John破喉咙@回复2020-01-29 19:26:33
安装好之后，所有浏览器都无法联网，包括应用商店，chrome浏览器点击不出界面，输入法切换不了中文，怎么解决


过路人@回复2020-01-29 20:36:10
@John破喉咙 你这个问题我也没遇到过，至于输入法切换是Ctrl+空格

######本文来自：TKDCZ网阁，原地址：https://www.tkdcz.top/post/46.html
```





```

Port 2222   
PermitRootLogin yes   
PasswordAuthentication yes    
AllowUsers sky 


```

# 连接Xshell

sudo vim /etc/ssh/sshd_config

编辑后，如何保存，退出

https://blog.csdn.net/qq_26369317/article/details/82384324





































sudo nano /etc/apt/sources.list

deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse



```
cat /proc/version
```



```
sudo apt-get update
```



```bash
fc-list :lang=zh-cn
```

```
sudo apt-get install language-pack-zh-hans
```

```
sudo apt-get install -y fonts-wqy-zenhei
```

```
sudo apt install -y fonts-wqy-microhei
```

```
nano .profile
```

```
export LANG="zh_CN.UTF-8"
export LC_ALL="zh_CN.UTF-8"
```



```bash
sudo dpkg-reconfigure locales
```

```
sudo apt-get install xubuntu-desktop
```

```
sudo sed -i 's/port=3389/port=3390/g' /etc/xrdp/xrdp.ini
```

```
sudo echo xfce4-session >~/.xsession
```

```
sudo service xrdp restart
```

```
sudo nano /etc/apt/sources.list
```

```
sudo apt-get install xubuntu-desktop
```

```
sudo apt-get install tasksel -y
```

```
sudo nano /etc/apt/sources.list
```

****



# 正式开始

## Linux 介绍

1**）Linux怎么读？ 【里纽克斯，里尼科斯，里纳克斯】**

2）Linux 是一款**操作系统，免费，开源， 安全，高效，稳定， 处理高并发**非常强悍，现在很多的企业级的项目都部署到 Linux/unix 服务器运行。

Linux 创始人-linux  林纳斯

3）Linux的吉祥物

企鹅 tux

🐧

4）**发行版和内核**

![](C:\Users\fucker\Pictures\Linux1.png)



**人机交互：**

![](C:\Users\fucker\Pictures\Linux2.PNG)

MVC三层架构的源头？？？ 应用层对应前端，解释层对应后台，操作系统对应数据库系统？



**Linux与Unix的关系**

![](C:\Users\fucker\Pictures\Linux3.png)

林纳斯响应GNU计划在Minix基础上开发了第一版的Linux的内核



**实际工作中的使用：**

![](C:\Users\fucker\Pictures\Linux4.PNG)



****

## 按照 VM和CentOS

学习 Linux **需要一个环境**，我们**需要创建一个虚拟机**，然后在虚拟机上安装一个 Centos 系统来学习。

1)先安装 virtual machine ,vm12

2)再安装 Linux (CentOS 6.8)

3)VM  和 CentOS 的关系：**原理示意图**

![](C:\Users\fucker\Pictures\Linux5.png)

****

## 虚拟机

- 虚拟机的网络连接三种形式说明
  - 桥连接：Linux可以和其他的系统通信。但是可能造成IP冲突。
  - NAT：网络地址转换方式：Linux可以访问外网，不会造成IP冲突。
  - 主机模式：你的Linux是一个独立的主机，不能访问外网。
- vmtools:
  - 共享文件夹
  - 共享剪贴板

****

# 基础命令--管理用户

## 创建用户，以及给用户分配密码 

```shell
mochou5@LAPTOP-UN694I4M:~$ su root
密码：
root@LAPTOP-UN694I4M:/home/mochou5# cd
root@LAPTOP-UN694I4M:~# cd /home/
root@LAPTOP-UN694I4M:/home#
root@LAPTOP-UN694I4M:/home#
root@LAPTOP-UN694I4M:/home# ls
mochou5  tiger
root@LAPTOP-UN694I4M:/home# useradd -d /home/tiger xg
root@LAPTOP-UN694I4M:/home# cd tiger
root@LAPTOP-UN694I4M:/home/tiger# passwd xg
输入新的 UNIX 密码：
重新输入新的 UNIX 密码：
passwd: password updated successfully
root@LAPTOP-UN694I4M:/home/tiger# su mochou5
mochou5@LAPTOP-UN694I4M:/home/tiger$ cd home
bash: cd: home: 没有那个文件或目录
mochou5@LAPTOP-UN694I4M:/home/tiger$ cd ..
mochou5@LAPTOP-UN694I4M:/home$ cd ..
mochou5@LAPTOP-UN694I4M:/$ su xg
密码：
$ date
2020年 02月 05日 星期三 19:23:55 CST
$
```

### **重点图示：操作系统与用户组的关系**

![](C:\Users\fucker\Pictures\Linux6.png)



**说明：**

1) Linux 系统是一个多用户多任务的操作系统，任何一个要使用系统资源的用户，都必须首先向系统管理员申请一个账号，然后以这个账号的身份进入系统。

2) Linux 的用户需要至少要属于一个组。



****

### 切换用户：su/su -



**su/su -  需要切换到的用户对应的用户名**

这两个命令都是一样的效果

`su root`这个命令 表示**切换到root账号/用户**

因为root账号是超级管理员账号，有很大的权限，而创建用户+分配密码就需要这样的权限。

1)**从权限高的用户切换到权限低的用户，不需要输入密码，反之需要**。

2)当需要返回到原来用户时，使用 exit 指令

实际上exit是**注销/退出**的意思，不是代表返回。只是可以通过返回达到同样的效果。

 

****

### 切换目录：cd

**cd  后面接目录路径**

这里绝对路径和相对路径都可以

例如：绝对路径

`cd /home/`

相对路径

`cd tiger`



绝对路径和相对路径的意思不多赘述，应该都懂。

我们可以看到两个`cd`命令之间隔着一个`ls`命令



因为在`/home/`目录下面有着子目录，其中有一个是tiger。直接通过`cd tiger`即可进入tiger目录。

而后面，因为没有注意相对路径，想通过`cd home`回到home目录，**但是tiger目录下并没有home这个子目录，因此提示失败 **

**返回父目录： `cd ..`**

第一次使用，从tiger目录回到了home目录

第二次使用，从home目录回到了初始目录



****

### 查询目录：ls

这个命令可以显示出该目录下的 ，文件或文件夹/(子)目录

它显示出了`/home/`目录下有两个目录。

****

### 创建用户：`useradd {-d 用户文件存放的路径}用户名 `

没有通过`-d`指定用户的路径，**会自动在当前目录下**创建和用户同名的家目录



如果指定，则是在**指定路径中创建**和用户同名的家目录{哪怕指定的路径都并不存在}，指定的具体路径不存在，则会顺带着创建一个路径

例如：

```shell
useradd -d /home/tiger xg
```

这条命令就在 /home/tiger这个路径下，创建了一个xg的账户，并默认创建了对应的家目录。

****

### 给用户分配密码：`passwd 用户名` 

通过`passwd`这条命令，就给后面跟着的用户名分配了一个密码

例如：

```shell
root@LAPTOP-UN694I4M:/home/tiger# passwd xg
输入新的 UNIX 密码：
重新输入新的 UNIX 密码：
passwd: password updated successfully
```

 最后一条`passwd: password updated successfully`表示密码已经更新成功

然后我们切换账户，用我们刚刚分配密码的用户名xg登录

```shell
mochou5@LAPTOP-UN694I4M:/$ su xg
密码：
$ date
2020年 02月 05日 星期三 19:23:55 CST
$
```

我们可以看到因为是自己用账户创建的用户，可能权限比较低，没有在$符前面显示出当前所在的目录。而且界面中实际也没有代码高亮。

不过通过`date`这一查看时间的命令使用，还是可以看到用户已经登录成功了。

****

## 删除用户：`userdel 用户名`

**基本语法**：`userdel 用户名`

应用实例:

### 1)删除xg,但是保留家目录 {实际中一般使用这种方式}：`userdel 用户名`

`userdel 用户名`

因为使用的是子系统 ，不便查看home目录，以及**查看不出具体的账户信息** 

因此不做演示了。

**为什么删除用户，但是保留家目录**

例如：有一个员工xg，它入职时给了他分配一个账户，他离职时删除该账户。但是他工作期间可能会有一些代码和分档放在家目录中。







```shell
root@LAPTOP-UN694I4M:/home/animal# cd /home/mochou5
root@LAPTOP-UN694I4M:/home/mochou5# userdel tom
userdel: user tom is currently used by process 41
root@LAPTOP-UN694I4M:/home/mochou5# su tom
$ exit
root@LAPTOP-UN694I4M:/home/mochou5# userdel tom
userdel: user tom is currently used by process 41
root@LAPTOP-UN694I4M:/home/mochou5# su tom
$ exit
root@LAPTOP-UN694I4M:/home/mochou5# exit
exit
$ exit
root@LAPTOP-UN694I4M:/home/mochou5# userdel tom
root@LAPTOP-UN694I4M:/home/mochou5# su tom
No passwd entry for user 'tom'
root@LAPTOP-UN694I4M:/home/mochou5#
```



可能有时出现进程占用的情况，需要连续退出几次



****

### 2）删除用户及**同名的家目录**：`userdel -r 用户名`

```shell
root@LAPTOP-UN694I4M:/# userdel -r xg
userdel: user xg is currently used by process 47
root@LAPTOP-UN694I4M:/# su xg
$ exit
root@LAPTOP-UN694I4M:/# exit
exit
$ exiit
sh: 8: exiit: not found
$ exit
mochou5@LAPTOP-UN694I4M:/$ su root
密码：
root@LAPTOP-UN694I4M:/# userdel -r xg
userdel: xg mail spool (/var/mail/xg) not found
userdel: /home/tiger not owned by xg, not removing
root@LAPTOP-UN694I4M:/# su xg
No passwd entry for user 'xg'
root@LAPTOP-UN694I4M:/#
```

`userdel -r 用户名`

我们可以看到当我们输入了：

`userdel -r xg`

之后系统提示了

```
userdel: user xg is currently used by process 47
```

**谷歌翻译：**

用户德尔：用户 xg 当前由进程 47 使用

**也就是说未退出账户，也就未结束进程。可以看到我们都是直接用su直接切换的账户，而不是退出账户号，再登录root账户！这不是一个好习惯！！！**

**未结束进程就不能退出账户。**

****

**退出的账户的命令：**

`exit`

一个非常常见的命令，大部分软件都是这个。不多说了

****

而当我们退出后，再次登录时，就显示

```
userdel: xg mail spool (/var/mail/xg) not found
userdel: /home/tiger not owned by xg, not removing
```

也就是说，**用户以及家目不存在**



我们登入用户xg，验证一下

系统：

```
root@LAPTOP-UN694I4M:/# su xg
No passwd entry for user 'xg'
```

也表示的是不存在。

也就是说userdel表示的是，**结束该账户的进程后删除。**



****

## 查询用户信息： `id 用户名`**

**基本语法：  `id 用户名`**

**应用实例：**

**查询root 信息**

```shell
mochou5@LAPTOP-UN694I4M:~$ id root
uid=0(root) gid=0(root) 组=0(root)
mochou5@LAPTOP-UN694I4M:~$ id xm
id: "xm": no such user
mochou5@LAPTOP-UN694I4M:~$ su root
密码：
root@LAPTOP-UN694I4M:/home/mochou5# useradd -d /home/ xq
root@LAPTOP-UN694I4M:/home/mochou5# passwd xq
输入新的 UNIX 密码：
重新输入新的 UNIX 密码：
passwd: password updated successfully
root@LAPTOP-UN694I4M:/home/mochou5# su mochou5
mochou5@LAPTOP-UN694I4M:~$ id xq
uid=1002(xq) gid=1002(xq) 组=1002(xq)
mochou5@LAPTOP-UN694I4M:~$
```



**查询xq,xg 信息 并删除xg**

```shell
root@LAPTOP-UN694I4M:/# id xq
uid=1002(xq) gid=1002(xq) 组=1002(xq)
root@LAPTOP-UN694I4M:/# id xm
id: "xm": no such user
root@LAPTOP-UN694I4M:/# id xg
uid=1001(xg) gid=1001(xg) 组=1001(xg)
root@LAPTOP-UN694I4M:/# id xh
id: "xh": no such user
root@LAPTOP-UN694I4M:/# userdel -r xg
userdel: xg mail spool (/var/mail/xg) not found
userdel: /home/tiger not owned by xg, not removing
root@LAPTOP-UN694I4M:/# id xg
id: "xg": no such user
root@LAPTOP-UN694I4M:/#
```







**细节说明：**

1）当用户不存在时，**返回无此用户**

```shell
root@LAPTOP-UN694I4M:/# userdel -r xg
userdel: xg mail spool (/var/mail/xg) not found
userdel: /home/tiger not owned by xg, not removing
root@LAPTOP-UN694I4M:/# id xg
id: "xg": no such user
root@LAPTOP-UN694I4M:/#
```

删除后，再查询时

显示的就是

```shell
id: "xg": no such user
```

****

2) **uid  gid  组**

![](C:\Users\fucker\Pictures\Linux7.png)

****



## **查看当前用户:**`whoami`

**可以用`whoami`或者`who am i`**

在子系统中，**这是一个很有用的命令**。因为没有目录栏，都只有$符号。因此**一时忘记就比较麻烦**

而$符表示普通用户

案例演示

```shell
root@LAPTOP-UN694I4M:/# su xq
$ whoami
xq
$
```

****

# 基础命令--管理用户组  {用户zwj以及他的组wudang还在 }

这里的组也就是上面所说的每一个用户所对应的家目录

## **什么是组？**

类似于角色组或者说现实中的小组/组织，系统**可以对有共性的多个用户**进行统一的管理。

## 增加用户组：`groupadd 用户组名`

`groupadd 用户组名`

实例：创建一个名为wudang的组

```shell
root@LAPTOP-UN694I4M:/# groupadd wudang
```

****

## **删除用户组**：`groupdel 用户组名`

`groupdel 用户组名`

案例:删除名为wudang的组

```shell
root@LAPTOP-UN694I4M:/# groupdel wudang
```

****

## **修改当前用户所在的组**：`usermod -g 将要去的用户组名 用户名 `        {接着-g就和用户组有关}

usermod是 user modify{汉语意思是修改}的缩写

或者说是给当前用户换一个组

`usermod -g 将要去的用户组名 用户名 `

**也可以理解为  组名   用户名**

例如： wudang  zhangsanfeng

**覆盖这个用户原本的信息{zhangsanfeng  zhangsanfeng}**

**为 wudang zhangsanfeng**

案例：创建了wudang这个组，并将xq放当wudang这个组下，最后再查询xq的信息

```shell
root@LAPTOP-UN694I4M:/# groupadd wudang
root@LAPTOP-UN694I4M:/# usermod -g wudang xq
root@LAPTOP-UN694I4M:/# id xq
uid=1002(xq) gid=1003(wudang) 组=1003(wudang)
```

可以看到xq的组变成了wudang

****

## **【重点】增加用户时直接加上组：`useradd -g  指定的用户组名 用户名`**                  

增加用户时，直接**指定一个已存在组**{指定的组是要已存在的组}

`useradd -g  指定的用户组名 用户名`

**与前文所述的`useradd -r 路径 用户名`比较：**

**-g 是指定组。而-r是指定组所在的路径**。没有-r就是默认当前路径下，没有-g就是同用户名的组



**案例：**创建名为shaolin的组，接着创建名为zwj的用户并指定到shaolin这个组，最好查询zwj的信息

```shell
root@LAPTOP-UN694I4M:/# groupadd shaolin
root@LAPTOP-UN694I4M:/# useradd -g  shaolin zwj
root@LAPTOP-UN694I4M:/# id zwj
uid=1003(zwj) gid=1004(shaolin) 组=1004(shaolin)
root@LAPTOP-UN694I4M:/#
```

****

## **删除用户的细节**:只删除了同名的组目录

```shell
root@LAPTOP-UN694I4M:/# userdel -r xq
userdel: group xq not removed because it is not the primary group of user xq.
userdel: xq mail spool (/var/mail/xq) not found
userdel: /home/ not owned by xq, not removing
root@LAPTOP-UN694I4M:/# su xq
No passwd entry for user 'xq'
root@LAPTOP-UN694I4M:/# userdel xq
userdel: user 'xq' does not exist
root@LAPTOP-UN694I4M:/home/mochou5# usermod -g wudang zwj
root@LAPTOP-UN694I4M:/home/mochou5# id zwj
uid=1003(zwj) gid=1003(wudang) 组=1003(wudang)
root@LAPTOP-UN694I4M:/home/mochou5#
```

使用`user -r xq`删除用户xq，已经所在的组，结果反馈是：

```shell
group xq not removed because it is not the 
```

xq所在的组未删除

首先我们试验，用户xq是否被删除

通过切换用户，和再次 删除的结果看已经被删除了



然后试验所在的组是否被删除

通过将用户zwj的组，修改为xq所在的组wudang，然后再查看zwj的信息可以看出，只删除了xq这个用户，而没有删除xq所在的组wudang

```shell
root@LAPTOP-UN694I4M:/home/mochou5# id zwj
uid=1003(zwj) gid=1003(wudang) 组=1003(wudang)
```

**最后单独的删除已经没有用户的组shaolin 和xq**    {本来在shaolin的zwj已经起来wudang，本来在xq组的xq已经去了wudang}   

```shell
root@LAPTOP-UN694I4M:/home/mochou5# groupdel xq
root@LAPTOP-UN694I4M:/home/mochou5# groupdel shaolin
root@LAPTOP-UN694I4M:/home/mochou5#
```



****









![](C:\Users\fucker\Pictures\Linux8.PNG)



**如何退出这个 界面？**

先按回车，然后输入命令`:q!`

















![](C:\Users\fucker\Pictures\Linux9.PNG)















![](C:\Users\fucker\Pictures\Linux10.PNG)



****

# 实用指令













**运行级别这一章，由于是子系统，不是虚拟机而且不是用的CentOS发行版，实操意义不大 ，看看理论就OK了**



centOS7在/lib/systemd/system/里

CentOS7 使用命令`systemctl set-default runleverl3.target`

一共0~6个runlevel.target文件，对应着7个级别，用来设置默认级别

Ubuntu也没有 /etc/inittab ，而且默认级别是2



现在较新的发行版都是用的system

****

# 实用指令--帮助指令

## 什么时候用帮助指令？







## 帮助指令man,使用：`man 指令名称`









## 帮助指令help ,使用：`help 指令名称`

基本语法

`help 命令名`（功能描述：获得 shell 内置命令的帮助信息）

只能获取shell内置命令，例如：cd,su

但是像ls这些就不行了。

因为之前改过默认语言，这里子系统中help使用的是中文显示的

****

# 实用指令 -- 文件目录类

这里是目录类。。。里面的指令非常多，类似于API。**建议细嚼慢咽，一个个的过**

## **显示当前工作目录的绝对路径**：`pwd`

**基本语法**

pwd	(功能描述：显示当前工作目录的绝对路径)



应用实例：登入用户zwj，进入home目录下的mochou5目录中，然后查看当前工作目录

```shell
$ cd mochou5
$ ls
$ ls -a
.  ..  .bash_history  .bash_logout  .bashrc  .local  .profile  .sudo_as_admin_successful
$ pwd
/home/mochou5
$ whoami
zwj
$
```

而切换到root账户后，是哪个目录？

```shell
root@LAPTOP-UN694I4M:/# pwd
/
root@LAPTOP-UN694I4M:/# ls -a
.   bin   dev  home  lib    media  opt   root  sbin  srv  tmp  var
..  boot  etc  init  lib64  mnt    proc  run   snap  sys  usr
root@LAPTOP-UN694I4M:/# cd root
root@LAPTOP-UN694I4M:~# pwd
/root
root@LAPTOP-UN694I4M:~#
```

显示的是在`/`这个目录下面，也就是文件树最初的地方

 

****

## 查看当前目录下的子目录或文件：`ls`

基本语法：

`ls [选项]   [目录或文件]`

这里的[选项]和[目录和文件],都只是可选的，不代表一定要选

后面的目录代表要查询的目录，未必是要用cd跳转到该目录下，才能查询 该目录下的文件

单纯的ls的意思，标题已叙



常用选项或者说是常用参数

`-a` :显示当前目录所有的文件和目录，包括隐藏的

`-l`：以列表方式显示“完整”信息

`-al或者-la`：相当于-a加上-l的效果，以列表形式较为完整的显示所有信息



应用实例

案例：显示当前工作目录的所有内容信息

一个是在`/`目录下信息，一个是在`/root`目录下的信息

```shell
root@LAPTOP-UN694I4M:/# ls -al
总用量 580
drwxr-xr-x  1 root root   4096 2月   5 14:24 .
drwxr-xr-x  1 root root   4096 2月   5 14:24 ..
drwxr-xr-x  1 root root   4096 2月   5 14:41 bin
drwxr-xr-x  1 root root   4096 5月  21  2019 boot
drwxr-xr-x  1 root root   4096 2月   6 12:06 dev
drwxr-xr-x  1 root root   4096 2月   6 16:15 etc
drwxr-xr-x  1 root root   4096 2月   5 16:30 home
-rwxr-xr-x  1 root root 591344 1月   1  1970 init
drwxr-xr-x  1 root root   4096 5月  21  2019 lib
drwxr-xr-x  1 root root   4096 5月  21  2019 lib64
drwxr-xr-x  1 root root   4096 5月  21  2019 media
drwxr-xr-x  1 root root   4096 2月   5 14:24 mnt
drwxr-xr-x  1 root root   4096 5月  21  2019 opt
dr-xr-xr-x 11 root root      0 2月   6 12:06 proc
drwx------  1 root root   4096 2月   6 16:15 root
drwxr-xr-x  1 root root   4096 2月   6 12:06 run
drwxr-xr-x  1 root root   4096 2月   5 14:44 sbin
drwxr-xr-x  1 root root   4096 3月  21  2019 snap
drwxr-xr-x  1 root root   4096 5月  21  2019 srv
dr-xr-xr-x 12 root root      0 2月   6 12:06 sys
drwxrwxrwt  1 root root   4096 2月   5 16:23 tmp
drwxr-xr-x  1 root root   4096 5月  21  2019 usr
drwxr-xr-x  1 root root   4096 5月  21  2019 var
root@LAPTOP-UN694I4M:/# ls -al /root
总用量 12
drwx------ 1 root root 4096 2月   6 16:15 .
drwxr-xr-x 1 root root 4096 2月   5 14:24 ..
-rw------- 1 root root 1272 2月   6 15:14 .bash_history
-rw-r--r-- 1 root root 3106 4月   9  2018 .bashrc
drwxr-xr-x 1 root root 4096 2月   5 14:32 .local
-rw-r--r-- 1 root root  148 8月  17  2015 .profile
-rw------- 1 root root 2412 2月   6 16:15 .viminfo
root@LAPTOP-UN694I4M:/#
```

****

## 切换指定目录：`cd`

**基本语法**

cd  [参数]  (功能描述，切换指定目录)

**常用参数**

- 绝对路径和相对路径
- cd~ 或者cd :    回到自己的家目录
- cd ..  回到当前目录的上一级目录

**应用实例**

案例1：使用绝对路径切换到root目录

案例2：使用相对路径到/root目录

****

## 用于创建目录：`mkdir`

**基本语法：**

mkdir是英文make directory的缩写

mkdir [选项] 要创建的目录



**常用选项/参数**

-p :创建多级目录

也就是一次性创建多级目录

**应用实例**

案例1：创建一个目录 /home/dog

`mkdir /home/dog`直接创建，然后用`ls home`查询目录下的文件，就可以看见创建的dog了

```shell
root@LAPTOP-UN694I4M:/# mkdir /home/dog
root@LAPTOP-UN694I4M:/# ls
bin  boot  dev  etc  home  init  lib  lib64  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var
root@LAPTOP-UN694I4M:/# ls  home
dog  mochou5  tiger
root@LAPTOP-UN694I4M:/# 
```

`mkdir /home/dog`表示的是在home目录下创建dog目录

****

案例2： 创建多级目录 /home/animal/tiger



```shell
root@LAPTOP-UN694I4M:/# mkdir /home/animal/tiger
mkdir: 无法创建目录"/home/animal/tiger": 没有那个文件或目录
```

直接mkdir创建时报错，因为mkdir只能创建1级目录

**什么是创建多级目录？**

创建/home/animal/tiger，它是*要在home这个已经存在的目录下，创建一共animal目录，接着在animal目录下创建tiger目录*。创建有了2步，也就是要创建一个2级目录

**如何一次性创建多级目录？**

`mkdir -p 要创建的多级目录`

```shell
root@LAPTOP-UN694I4M:/# mkdir -p /home/animal/tiger
root@LAPTOP-UN694I4M:/# ls /home/
animal  dog  mochou5  tiger
root@LAPTOP-UN694I4M:/# ls /home/animal
tiger
```

接着查询，显示有该目录

****

## 用于删除空目录：`rmdir` 



**基本语法：**

rmdir [选项]  要删除的空目录



**应用实例**

案例1 ：删除一个目录/home/dog

直接使用指令：`rmdir /home/dog`  ,然后查询是否还存在dog目录

```shell
root@LAPTOP-UN694I4M:/# ls /home/
animal  dog  mochou5  tiger
root@LAPTOP-UN694I4M:/# ls /home/tiger
root@LAPTOP-UN694I4M:/# ls /home/animal
tiger
root@LAPTOP-UN694I4M:/# rmdir /home/dog
root@LAPTOP-UN694I4M:/# ls home
animal  mochou5  tiger
```



**使用细节：**

rmdir 删除的是空目录，如果目录下有内容时无法删除



再建一个 /home/dog目录，并在其中用vim编辑器写一个文件test.txt。{这里编辑器使用的是nano，个人习惯 。指令只是将字符vim换成了nano：`nano test.txt` ,然后CTRL+O,再回车保存，ctrl+x退出}

文件内容

```
hello Linux!
```

`ls`再查看就要test.txt文件了，然后开始删除测试

```shell
root@LAPTOP-UN694I4M:/# mkdir /home/dog
root@LAPTOP-UN694I4M:/# cd /home/dog
root@LAPTOP-UN694I4M:/home/dog# nano test.txt
root@LAPTOP-UN694I4M:/home/dog# ls
test.txt
root@LAPTOP-UN694I4M:/home/dog# rmdir /home/dog
rmdir: 删除 '/home/dog' 失败: 目录非空
```



**提示：如果需要删除非空目录，需要使用 `rm -rf 要删除的目录`**

使用指令：`rm -rf /home/dog`

然后再查询

```shell
root@LAPTOP-UN694I4M:/home/dog# rm -rf /home/dog
root@LAPTOP-UN694I4M:/home/dog# ls  /home
animal  mochou5  tiger
```

****

## 用于创建空文件：`touch`



**基本语法：**

touch 文件名称



**应用实例：**

案例1：创建一个空文件hello.txt

使用指令：`touch hello.txt`

接着用`ls`查询，然后又用`ls -l`查询，我们可以看到hello.txt这个文件大小为0 

```shell
root@LAPTOP-UN694I4M:/home# touch hello.txt
root@LAPTOP-UN694I4M:/home# ls
animal  hello.txt  mochou5  tiger
root@LAPTOP-UN694I4M:/home# ls -l
总用量 0
drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
-rw-r--r-- 1 root    root       0 2月   9 15:18 hello.txt
drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
```



****

案例2：一次性创建多个文件hello2.txt.hello3.txt



使用指令：`touch hello2.txt hello3.txt`

然后用`ls`指令查询

```shell
root@LAPTOP-UN694I4M:/home# touch hello2.txt  hello3.txt
root@LAPTOP-UN694I4M:/home# ls
animal  hello2.txt  hello3.txt  hello.txt  mochou5  tiger
```

****

## 用于拷贝文件到指定目录：`cp`    【重要】

cp也就是copy的英文缩写，表示拷贝



**基本语法：**

cp [选项] source dest

这里的source代表的是源，也就是源文件/被拷贝的文件

相对的dest代表的就是目的地，也就是将源文件拷贝到那里去



或许应该这样表示基本语法：

**cp [选项] 源文件名 要拷贝到的目的地(用路径表示)**



这里可以用相对路径和绝对路径都可以，但是为了简便一般都用相对路径



**常用选项/参数：**

-r : 递归复制整个文件夹



**应用案例：**

案例1：将/home/aaa.txt拷贝到 /home/bbb 目录下   【拷贝单个文件】



因为没有 aaa.txt文件，也没有bbb目录，因此需要先创建

使用`mkdir /home/bbb`创建bbb目录

然后使用 `touch aaa.txt`直接当前目录(home)下创建aaa.txt文件

然后 `ls`查询

接着使用指令 `cp aaa.txt bbb`将aaa.txt文件拷贝到当前目录(home)下的bbb这个子目录中

最后查看bbb目录：`ls bbb `



```shell
root@LAPTOP-UN694I4M:/home# mkdir /home/bbb
root@LAPTOP-UN694I4M:/home# touch aaa.txt
root@LAPTOP-UN694I4M:/home# ls
aaa.txt  animal  bbb  hello2.txt  hello3.txt  hello.txt  mochou5  tiger
root@LAPTOP-UN694I4M:/home# cp aaa.txt bbb
root@LAPTOP-UN694I4M:/home# ls bbb
aaa.txt
```



****

案例2：递归复制整个文件夹，举例  将/home/bbb 整个目录拷贝到/home/zwj目录下

###     *插入一个   `clear`清屏*    它的中文意思是清楚

使用指令 `cp bbb zwj` ,但是系统报错了

```shell
root@LAPTOP-UN694I4M:/home# su zwj
$ exit
root@LAPTOP-UN694I4M:/home# cp bbb zwj
cp: -r not specified; omitting dweiiirectory 'bbb'
```

错误信息{-r not specified; omitting directory }  的意思为 {-r未指定； 省略目录}



**因此需要使用-r参数**

**注意{特别是初学者}：一定要注意你当前的目录位置，然后要准确的定位源目录和目标目录位置**



使用指令 `cp -r bbb zwj` 表示将bbb这整个目录复制到zwj这个目录下

接着用 `ls zwj` 查询zwj这个目录，**结果却只有aaa.txt文件，而不是bbb目录**

```shell
root@LAPTOP-UN694I4M:/home# cp -r bbb zwj
root@LAPTOP-UN694I4M:/home# ls zwj
aaa.txt
```

**why？？？**

又进入到zwj目录下，再查询

```shell
root@LAPTOP-UN694I4M:/home# cd zwj
root@LAPTOP-UN694I4M:/home/zwj# ls
aaa.txt
```

依旧如此

做出假设：bbb目录下只有aaa.txt一个文件，在系统递归复制时(可能问题就出在递归复制上？)只复制单一文件。**当bbb目录下有多个文件时，系统递归复制时会按照整个目录的形式复制**



*第2次拷贝*

切换到/home/bbb目录下

先在bbb目录下，使用指令 `touch a2.txt` 创建a2.txt文件

然后使用指令 `cp -r bbb zwj` 将home目录下的bbb目录，**复制到同样在home目录下的zwj目录**

然后再查看zwj目录，结果就有bbb目录

最后查看zwj目录下的bbb目录，有创建的2个文件

```shell
root@LAPTOP-UN694I4M:/home/zwj# cd /home
root@LAPTOP-UN694I4M:/home# cd bbb
root@LAPTOP-UN694I4M:/home/bbb# touch a2.txt
root@LAPTOP-UN694I4M:/home# cp -r bbb zwj
root@LAPTOP-UN694I4M:/home# ls zwj
aaa.txt  bbb
root@LAPTOP-UN694I4M:/home# ls  zwj/bbb
a2.txt  aaa.txt
```



****

**使用细节：**

强制覆盖不提示的方法：`\cp`

```shell
root@LAPTOP-UN694I4M:/home# cp  hello3.txt zwj
root@LAPTOP-UN694I4M:/home# cp  hello3.txt zwj
root@LAPTOP-UN694I4M:/home# ls zwj
aaa.txt  hello3.txt
root@LAPTOP-UN694I4M:/home# \cp hello3.txt zwj
root@LAPTOP-UN694I4M:/home# ls zwj
aaa.txt  hello3.txt
```

在WSL的Ubuntu中，**复制了已有的文件会默认覆盖且无提示**





![](C:\Users\fucker\Pictures\Linux12.png)

****

## 技术小技巧：上下键掉指令

可以通过 上下箭头的键，调出原来使用过的指令



****



## 移除文件或目录：`rm`



**基本语法**

rm [选项] 要删除的文件或目录



**常用选项**

-r  :  递归删除整个文件夹

-f   :  强制删除不提示



**应用实例**

案例1：将/home/aaa.txt删除

```shell
root@LAPTOP-UN694I4M:/home/mochou5# cd /home
root@LAPTOP-UN694I4M:/home# ls
aaa.txt  animal  bbb  hello2.txt  hello3.txt  hello.txt  mochou5  tiger  zwj
root@LAPTOP-UN694I4M:/home# rm bbb
rm: 无法删除'bbb': 是一个目录
root@LAPTOP-UN694I4M:/home# rm aaa.txt
root@LAPTOP-UN694I4M:/home# ls
animal  bbb  hello2.txt  hello3.txt  hello.txt  mochou5  tiger  zwj
```



在CentOS6.8中则会提示是否要删除该空文件



****

案例2： 递归删除整个文件夹 /home/bbb

```shell
root@LAPTOP-UN694I4M:/home# rm -r bbb
root@LAPTOP-UN694I4M:/home# ls
animal  hello2.txt  hello3.txt  hello.txt  mochou5  tiger  zwj
root@LAPTOP-UN694I4M:/home#
```





使用指令 `rm -rf 目录/文件路径` 这样也可以删除，而且在很多发行版中，都是用的这种，而单纯的-r 可能在其他发行版，例如CentOS中删不了，建议使用这种方式    `rm -r 目录/文件路径`



```shell
root@LAPTOP-UN694I4M:/home# cd zwj
root@LAPTOP-UN694I4M:/home/zwj# ls
aaa.txt  bbb
root@LAPTOP-UN694I4M:/home/zwj# rm -rf bbb
root@LAPTOP-UN694I4M:/home/zwj# ls
aaa.txt
root@LAPTOP-UN694I4M:/home/zwj#
```



****

**使用细节**

强制删除不提示的方法，带上 -f  参数即可

f代表false，强制



```shell
root@LAPTOP-UN694I4M:/# cd /home
root@LAPTOP-UN694I4M:/home# ls
animal  hello2.txt  hello3.txt  hello.txt  mochou5  tiger  zwj
root@LAPTOP-UN694I4M:/home# rm hello2.txt
root@LAPTOP-UN694I4M:/home# ls
animal  hello3.txt  hello.txt  mochou5  tiger  zwj
root@LAPTOP-UN694I4M:/home# nano hello.txt
root@LAPTOP-UN694I4M:/home# rm hello.txt
root@LAPTOP-UN694I4M:/home# ls

animal  hello3.txt  mochou5  tiger  zwj
```



而在WSL的Ubuntu中删除没有提示。。。。不需要加-f参数来消除提示，就像是cp拷贝文件时**默认覆盖无提示**

CentOS7貌似也没有。。。



**为什么有`rm`，还要设计`rmdir`???**

因为少一次提示？？？

还是说 `rmdir`更安全？？？

****

## 移动文件/目录，或进行重命名：`mv`



**基本语法：**

mv oldNameFile newNameFile (功能描述：重命名)

`mv 原文件名 新文件名`



mv /temp/movefile  /targetFolder (功能描述：移动文件)

`mv 文件名 路径`



**什么时候时移动，什么时候是重命名？**







****

**应用实例**

案例1：将/home/aaa.txt 文件重新命为 pig.txt

先用 `touch aaa.txt`指令建一个空文件aaa

然后再用 `mv aaa.txt pig.txt`重命名文件名

```shell
root@LAPTOP-UN694I4M:/home# touch aaa.txt
root@LAPTOP-UN694I4M:/home# ls
aaa.txt  animal  hello3.txt  mochou5  tiger  zwj
root@LAPTOP-UN694I4M:/home# mv aaa.txt pig.txt
root@LAPTOP-UN694I4M:/home# ls
animal  hello3.txt  mochou5  pig.txt  tiger  zwj
```

**为什么会有重命名呢？**【重命名原理】

本来这个指令 是移动这个

因为 **把aaa.txt这个文件移动到当前这个目录下，然后发现当前目录下有一个aaa.txt这个文件**，就将老的文件名改为pig这个新的文件名

**亲测  `mv dir1 dir2`,dir2不存在就会重命名**



```
root@LAPTOP-UN694I4M:/home# touch dir2
root@LAPTOP-UN694I4M:/home# ls
animal  dir1  dir2  hello3.txt  mochou5  pig.txt  tiger  zwj
root@LAPTOP-UN694I4M:/home# mv dir1 dir2
root@LAPTOP-UN694I4M:/home# ls
animal  dir2  hello3.txt  mochou5  pig.txt  tiger  zwj
```



先将dir1移动到当前目录下，然后当前目录下有一个dir1，则将其重命名为dir2，然后当前目录下也有一个dir2则覆盖掉原来的dir2



这里也可以用.txt文件演示，两个文件中编辑的内容不同，然后再演示时即可看出差别



****

案例2：

将/home/pig.txt 文件 移动到/zwj目录下

因为zwj目录下，没有pig.txt这个文件就会移动文件到zwj这个目录下

```shell
root@LAPTOP-UN694I4M:/home# mv pig.txt zwj
root@LAPTOP-UN694I4M:/home# cd zwj
root@LAPTOP-UN694I4M:/home/zwj# ls
aaa.txt  hello3.txt  pig.txt
```





****



## 查看文件(本页)内容 ：`cat`      只读



**基本语法**

cat [选项] 要查看的文件

它是以只读的方式查看文件内容



**常用选项**

-n ： 显示行号



**应用实例**

案例1：/etc/profile 文件内容，并显示行号



```shell
root@LAPTOP-UN694I4M:/# cat -n /etc/profile
     1  # /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
     2  # and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).
     3
     4  if [ "${PS1-}" ]; then
     5    if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
     6      # The file bash.bashrc already sets the default PS1.
     7      # PS1='\h:\w\$ '
     8      if [ -f /etc/bash.bashrc ]; then
     9        . /etc/bash.bashrc
    10      fi
    11    else
    12      if [ "`id -u`" -eq 0 ]; then
    13        PS1='# '
    14      else
    15        PS1='$ '
    16      fi
    17    fi
    18  fi
    19
    20  if [ -d /etc/profile.d ]; then
    21    for i in /etc/profile.d/*.sh; do
    22      if [ -r $i ]; then
    23        . $i
    24      fi
    25    done
    26    unset i
    27  fi
root@LAPTOP-UN694I4M:/#
```

Ubuntu系统中这个文件内容和CentOS不同。。。CentOS内容很多行。。建议分页查看





****

**使用细节**

cat**只能浏览文件，而不能修改文件**，为了浏览方便，一般会带上 管道命令 `|more`

`more`代表分页形式，而`|`是管道符。**管道是一种进程间通信方法**

空格是向下翻页,回车键是 向下读一行



使用指令：

`cat -n 文件名 | more`   {分页浏览}

 



这里 使用 /etc/presage.xml 显示

 在etc目录下，使用指令 `cat -n presage.xml`查看

```shell
root@LAPTOP-UN694I4M:/etc# cat -n presage.xml
     1  <?xml version="1.0" encoding="UTF-8" standalone="no" ?>
     2  <Presage>
     3      <PredictorRegistry>
     4          <LOGGER>ERROR</LOGGER>
     5          <!-- PREDICTORS
     6               Space separated list of predictors to use to generate predictions
     7          -->
     8          <PREDICTORS>DefaultAbbreviationExpansionPredictor DefaultSmoothedNgramPredictor UserSmoothedNgramPredictor DefaultRecencyPredictor</PREDICTORS>
     9      </PredictorRegistry>
    10      <ContextTracker>
    11          <LOGGER>ERROR</LOGGER>
    12          <!-- SLIDING_WINDOW_SIZE
    13               Size of buffer used by context tracker to detect context changes
    14          -->
    15          <SLIDING_WINDOW_SIZE>80</SLIDING_WINDOW_SIZE>
    16          <!-- LOWERCASE_MODE
    17               Instruct context tracker to track text as lowercase
    18          -->
    19          <LOWERCASE_MODE>yes</LOWERCASE_MODE>
    20          <!-- ONLINE_LEARNING
    21               Controls presage online machine learning feature.
    22               Presage is context-aware and capable of dynamic online learning.
    23               Setting this to yes/true will enable online learning mode.
    24               Setting this to no/false will disable online learning mode.
    25
    26               When online learning mode is disabled, it is still
    27               possible to instruct presage to learn through its API.
    28          -->
    29          <ONLINE_LEARNING>yes</ONLINE_LEARNING>
    30      </ContextTracker>
    31      <Selector>
    32          <LOGGER>ERROR</LOGGER>
    33          <!-- SUGGESTIONS
    34               Controls how many suggestions are returned in each prediction.
    35          -->
    36          <SUGGESTIONS>6</SUGGESTIONS>
    37          <!-- REPEAT_SUGGESTIONS
    38               Allow the same suggestion to be offered in subsequent
    39               predictions, even if no context change has been detected.
    40          -->
    41          <REPEAT_SUGGESTIONS>no</REPEAT_SUGGESTIONS>
    42          <!-- GREEDY_SUGGESTION_THRESHOLD
    43               Select only tokens whose completion length is greater than
    44               the specified greedy suggestion threshold.
    45               i.e. If this option is set to 2 and the current prefix is
    46                 "cu", then the word "cub" will not offered as a
    47                 suggestion, because the completion's length is only one
    48                 character long. Tokens "curb" or "cube" or "cubicle" or
    49                 "cucumber" will however be offered, because these
    50                 words' completions are at least 2 characters long.
    51          -->
    52          <GREEDY_SUGGESTION_THRESHOLD>0</GREEDY_SUGGESTION_THRESHOLD>
    53      </Selector>
    54      <PredictorActivator>
    55          <LOGGER>ERROR</LOGGER>
    56          <!-- PREDICT_TIME
    57               Maximum time allowed for predictors to return their prediction.
    58          -->
    59          <PREDICT_TIME>1000</PREDICT_TIME>
    60          <!-- MAX_PARTIAL_PREDICTION_SIZE
    61               Desired size of each prediction prior to combination phase.
    62          -->
    63          <MAX_PARTIAL_PREDICTION_SIZE>60</MAX_PARTIAL_PREDICTION_SIZE>
    64          <!-- COMBINATION_POLICY
    65               policy used by predictor to combine predictions returned
    66               by the active predictors into one prediction.
    67          -->
    68          <COMBINATION_POLICY>Meritocracy</COMBINATION_POLICY>
    69      </PredictorActivator>
    70      <ProfileManager>
    71          <LOGGER>ERROR</LOGGER>
    72          <!-- AUTOPERSIST
    73               Automatically saves configuration to active profile.
    74            -->
    75          <AUTOPERSIST>false</AUTOPERSIST>
    76      </ProfileManager>
    77      <Predictors>
    78          <DefaultSmoothedNgramPredictor>
    79              <PREDICTOR>SmoothedNgramPredictor</PREDICTOR>
    80              <LOGGER>ERROR</LOGGER>
    81              <DBFILENAME>/usr/share/presage/database_en.db</DBFILENAME>
    82              <!-- delta_0, delta_1, ..., delta_{n-1}
    83                   Deltas also control the value of n in the n-gram model.
    84              -->
    85              <DELTAS>0.01 0.1 0.89</DELTAS>
    86              <LEARN>false</LEARN>
    87              <DatabaseConnector>
    88                  <LOGGER>ERROR</LOGGER>
    89              </DatabaseConnector>
    90          </DefaultSmoothedNgramPredictor>
    91          <UserSmoothedNgramPredictor>
    92              <PREDICTOR>SmoothedNgramPredictor</PREDICTOR>
    93              <LOGGER>ERROR</LOGGER>
    94              <!-- ${HOME} is special. It expands to:
    95                    - $HOME on Unix
    96                    - %USERPROFILE% on Windows
    97                -->
    98              <DBFILENAME>${HOME}/.presage/lm.db</DBFILENAME>
    99              <!-- delta_0, delta_1, ..., delta_{n-1}
   100                   Deltas also control the value of n in the n-gram model.
   101              -->
   102              <DELTAS>0.01 0.1 0.89</DELTAS>
   103              <LEARN>true</LEARN>
   104              <DatabaseConnector>
   105                  <LOGGER>ERROR</LOGGER>
   106              </DatabaseConnector>
   107          </UserSmoothedNgramPredictor>
   108          <DefaultRecencyPredictor>
   109              <PREDICTOR>RecencyPredictor</PREDICTOR>
   110              <LOGGER>ERROR</LOGGER>
   111              <LAMBDA>1</LAMBDA>
   112              <N_0>1</N_0>
   113              <CUTOFF_THRESHOLD>20</CUTOFF_THRESHOLD>
   114          </DefaultRecencyPredictor>
   115          <DefaultDictionaryPredictor>
   116              <PREDICTOR>DictionaryPredictor</PREDICTOR>
   117              <LOGGER>ERROR</LOGGER>
   118              <DICTIONARY>/usr/share/dict/words</DICTIONARY>
   119              <!-- fixed probability assigned to prediction -->
   120              <PROBABILITY>0.000001</PROBABILITY>
   121          </DefaultDictionaryPredictor>
   122          <DefaultAbbreviationExpansionPredictor>
   123              <PREDICTOR>AbbreviationExpansionPredictor</PREDICTOR>
   124              <LOGGER>ERROR</LOGGER>
   125              <ABBREVIATIONS>/usr/share/presage/abbreviations_en.txt</ABBREVIATIONS>
   126          </DefaultAbbreviationExpansionPredictor>
   127          <DefaultDejavuPredictor>
   128              <PREDICTOR>DejavuPredictor</PREDICTOR>
   129              <LOGGER>ERROR</LOGGER>
   130              <MEMORY>/usr/share/presage/dejavu_memory_en.txt</MEMORY>
   131              <TRIGGER>3</TRIGGER>
   132          </DefaultDejavuPredictor>
   133          <DefaultARPAPredictor>
   134              <PREDICTOR>ARPAPredictor</PREDICTOR>
   135              <LOGGER>ERROR</LOGGER>
   136              <ARPAFILENAME>/usr/share/presage/arpa_en.arpa</ARPAFILENAME>
   137              <VOCABFILENAME>/usr/share/presage/arpa_en.vocab</VOCABFILENAME>
   138              <TIMEOUT>100</TIMEOUT>
   139          </DefaultARPAPredictor>
   140      </Predictors>
   141  </Presage>
root@LAPTOP-UN694I4M:/etc# 
```



**分页后的：**

使用指令 `Cat -n profile |more`

它表示以Cat指令打开文件，并以分页显示。





```shell
     1  <?xml version="1.0" encoding="UTF-8" standalone="no" ?>
     2  <Presage>
     3      <PredictorRegistry>
     4          <LOGGER>ERROR</LOGGER>
     5          <!-- PREDICTORS
     6               Space separated list of predictors to use to generate predictions
     7          -->
     8          <PREDICTORS>DefaultAbbreviationExpansionPredictor DefaultSmoothedNgram
Predictor UserSmoothedNgramPredictor DefaultRecencyPredictor</PREDICTORS>
     9      </PredictorRegistry>
    10      <ContextTracker>
    11          <LOGGER>ERROR</LOGGER>
    12          <!-- SLIDING_WINDOW_SIZE
    13               Size of buffer used by context tracker to detect context changes
    14          -->
    15          <SLIDING_WINDOW_SIZE>80</SLIDING_WINDOW_SIZE>
    16          <!-- LOWERCASE_MODE
    17               Instruct context tracker to track text as lowercase
    18          -->
    19          <LOWERCASE_MODE>yes</LOWERCASE_MODE>
    20          <!-- ONLINE_LEARNING
    21               Controls presage online machine learning feature.
    22               Presage is context-aware and capable of dynamic online learning.
    23               Setting this to yes/true will enable online learning mode.
    24               Setting this to no/false will disable online learning mode.
    25
    26               When online learning mode is disabled, it is still
    27               possible to instruct presage to learn through its API.
    28          -->
--更多-- 
```

因为之前WSL中装过默认中文环境，这里显示的是 `--更多--`。如果是CentOS或者是没有默认中文环境则是 `--More--`



****

## 以全屏幕的方式显示文件：`more`



more 指令是一个基于 VI 编辑器的文本过滤器，它以全屏幕的方式按页显示文本文件的内容。more 指令中内置了若干快捷键，详见操作说明

**操作说明：**

![](C:\Users\fucker\Pictures\Linux13.png)



**基本语法：**

more  要查看的文件



**应用实例:**

案例：采用 more 查看文件 /etc/presage.xml



实用指令 ` more /etc/presage.xml`

```shell
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<Presage>
    <PredictorRegistry>
        <LOGGER>ERROR</LOGGER>
        <!-- PREDICTORS
             Space separated list of predictors to use to generate predictions
        -->
        <PREDICTORS>DefaultAbbreviationExpansionPredictor DefaultSmoothedNgramPredicto
r UserSmoothedNgramPredictor DefaultRecencyPredictor</PREDICTORS>
    </PredictorRegistry>
    <ContextTracker>
        <LOGGER>ERROR</LOGGER>
        <!-- SLIDING_WINDOW_SIZE
             Size of buffer used by context tracker to detect context changes
        -->
        <SLIDING_WINDOW_SIZE>80</SLIDING_WINDOW_SIZE>
        <!-- LOWERCASE_MODE
             Instruct context tracker to track text as lowercase
        -->
        <LOWERCASE_MODE>yes</LOWERCASE_MODE>
        <!-- ONLINE_LEARNING
             Controls presage online machine learning feature.
             Presage is context-aware and capable of dynamic online learning.
             Setting this to yes/true will enable online learning mode.
             Setting this to no/false will disable online learning mode.

             When online learning mode is disabled, it is still
             possible to instruct presage to learn through its API.
        -->
--更多--(20%) 
```



ctrl+b 返回上一页





****

## 查看文件不仅可以分页，还可以方便地搜索，回翻等操作： `less`

**对于显示大型文件具有较高效率，特别是大型日志文件！！(工作中必备)**

less 指令用来分屏查看文件内容，它的功能与 more 指令类似，但是比 more 指令更加强大，**支持各种显示终端**。less 指令在显示文件内容时，**并不是一次将整个文件加载之后才显示，而是根据显示需要加载内容**，因此打开大文件（例如30MB,100MB）更快



我们使用less访问win10系统中桌面上的文件

WSL的Ubuntu中，**W10系统的文件在/mnt目录下**

用法和more一样的

使用指令 `less  /mnt/c/Users/{这里写直自己的用户名}/Desktop/看这里.txt`



```shell
root@LAPTOP-UN694I4M:/# less  /mnt/c/Users/{这里写直自己的用户名}/Desktop/看这里.txt
"/mnt/c/Users//{这里写直自己的用户名}/Desktop/看这里.txt" may be a binary file.  See it anyway?
```

然后输入 y

```shell
˵ʵ<BB><B0><A3><AC><CE><D2>C<D3><EF><D1>Ը<B4>ϰ<B5><C4><D7><CA><C1>ϲ<BB><B6>࣬<CE>Ҿ<CD>
<CA>ǰѽ̲Ŀ<B4><C1>˼<B8><B1>飬Ȼ<BA><F3><D7><F6><CD><EA><C1><CB>һ<B1><BE>C<D3><EF><D1><D4>
<C1><B7>ϰ<B2>ᣬ<D5><E2>Щ<BE><CD><D7>㹻<C1>ˡ<A3>ƽʱ<D4><DA>ѧУ<B0><D1><CE><D2><C3><C7>ר
<BF>Ƶ<C4>C<D3><EF><D1><D4>ѧ<BA>û<F9><B1><BE><BE><CD>OK<C1>ˣ<A1><A3><AC>
<CE>Ұ<D1><C1><B7>ϰ<B2><E1><B5>Ĺ<BA><C2><F2><C1><B4><BD><D3><CC><F9><C9><CF><C0><B4>
<A3><BA>
<C1><B7>ϰ<B2>᣺
<C7>廪<D5><FD><B0><E6> ̷<BA><C6>ǿ C<B3><CC><D0><F2><C9><E8><BC><C6><CA><D4><CC><E2><BB><E3><B1><E0> <B5><DA><C8><FD><B0><E6><B5><DA>3<B0><E6> C<B3><CC><D0><F2><C9><E8><BC>ƽ̳
<CC> C<D3><EF><D1>Գ<CC><D0><F2><C9><E8><BC>ƽ̲<C4><C5><E4><CC><D7>C<B3><CC><D0><F2><CC>
<E2><BF><E2> <B4><F3>ѧ<BC><C6><CB><E3><BB><FA><BD>̲<C4>C<B3><CC><D0><F2>ϰ<CC><E2>
-------------------
<8F><CD><D1>u<D5><E2><CC><F5>(1SYhY43C8FN)<A3><AC><BD><F8><C8>롾Tao<B1><A6><A1><BF>
<BC><B4><BF><C9><C7><C0><B9><BA>
/mnt/c/Users/fucker/Desktop/看这里.txt (END)
```



乱码。。。。

接着按 `q` 退出





**快捷键**

![](C:\Users\fucker\Pictures\Linux14.png)



也就是说↑，代表向上翻页。而↓，代表向下翻页

****



接着试试 把这个文件复制到home目录中,并使用 `ls` 查看

```shell
root@LAPTOP-UN694I4M:/# cp /mnt/c/Users/fucker/Desktop/看这里.txt /home
root@LAPTOP-UN694I4M:/# cd home
root@LAPTOP-UN694I4M:/home# ls
animal  dir2  hello3.txt  mochou5  tiger  zwj  看这里.txt
```





****

## 输出重定向和追加 ：`>`和 `>>`

`>`表示的是输出重定向

`>>`表示的是追加



**什么是输出重定向？**

输出的内容覆盖掉原有的内容



**什么是追加 ？**

输出的内容，追加到原有内容的尾部{并不覆盖}



**基本语法：  【实际开发中用的比较多】**

1. ls -l > 文件                 (功能描述：把当前查看列表的{返回}内容写入文件{a.txt}中{覆盖写}       如果文件{a.txt}不存在则创建这个文件，存在则覆盖文件)
2. ls -al >> 文件           (功能描述： 把当前查看列表的{返回}内容追加文件{aa.txt}的末尾{不覆盖原来的文件} )
3. cat  文件1 > 文件2      (功能描述： 将文件1的内容覆盖到文件2)
4. echo  "内容">> 文件         (功能描述：   把内容写入文件当中)



应用实例

第1点,使用指令 `ls -l > a.txt`

```shell
root@LAPTOP-UN694I4M:/home# ls
animal  dir2  hello3.txt  mochou5  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home# ls -l > a.txt
root@LAPTOP-UN694I4M:/home# ls
animal  a.txt  dir2  hello3.txt  mochou5  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home# nano a.txt
root@LAPTOP-UN694I4M:/home# cat -n a.txt
     1  总用量 0
     2  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
     3  -rw-r--r-- 1 root    root       0 2月  10 20:33 a.txt
     4  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
     5  -rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
     6  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
     7  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
     8  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
     9  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home# 
```

可以看到**原来是没有a.txt这个文件的，但是使用了输出重定向指令后，(不存在文件)就创建该文件并写入查询指令返回内容**



****

第2点，使用指令 `ls -al >> aa.txt`

```shell
root@LAPTOP-UN694I4M:/home# ls -al >> aa.txt
root@LAPTOP-UN694I4M:/home# cat -n aa.txt
     1  总用量 0
     2  drwxr-xr-x 1 root    root    4096 2月  10 20:39 .
     3  drwxr-xr-x 1 root    root    4096 2月  10 17:22 ..
     4  -rw-r--r-- 1 root    root       0 2月  10 20:39 aa.txt
     5  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
     6  -rw-r--r-- 1 root    root     465 2月  10 20:33 a.txt
     7  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
     8  -rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
     9  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
    10  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
    11  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
    12  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#                         
```

同样类似于 `>`,如果没有原文件则创建该文件直接写入，如果有原文件则追加到原文件尾部

使用指令 `ls -al >> aa.txt`

```shell
root@LAPTOP-UN694I4M:/home# ls -al >> aa.txt
root@LAPTOP-UN694I4M:/home# cat -n aa.txt
     1  总用量 0
     2  drwxr-xr-x 1 root    root    4096 2月  10 20:39 .
     3  drwxr-xr-x 1 root    root    4096 2月  10 17:22 ..
     4  -rw-r--r-- 1 root    root       0 2月  10 20:39 aa.txt
     5  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
     6  -rw-r--r-- 1 root    root     465 2月  10 20:33 a.txt
     7  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
     8  -rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
     9  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
    10  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
    11  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
    12  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
    13  总用量 4
    14  drwxr-xr-x 1 root    root    4096 2月  10 20:39 .
    15  drwxr-xr-x 1 root    root    4096 2月  10 17:22 ..
    16  -rw-r--r-- 1 root    root     624 2月  10 20:39 aa.txt
    17  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
    18  -rw-r--r-- 1 root    root     465 2月  10 20:33 a.txt
    19  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
    20  -rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
    21  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
    22  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
    23  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
    24  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home# ls -al
总用量 4
drwxr-xr-x 1 root    root    4096 2月  10 20:39 .
drwxr-xr-x 1 root    root    4096 2月  10 17:22 ..
-rw-r--r-- 1 root    root    1248 2月  10 20:42 aa.txt
drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
-rw-r--r-- 1 root    root     465 2月  10 20:33 a.txt
-rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
-rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home# 
```

可以看到了 `ls -al`  指令返回的结果是 `总用量 4`等

因此再次使用指令 `ls -al >> aa.txt`返回的结果就是追加了本次  `ls al`指令的结果

****



第3点，将a.txt文件覆盖到aa.txt文件 中



使用指令 `cat a.txt > aa.txt`

可以看到原来有 24行{见第2点返回的结果}的aa.txt被a.txt文件覆盖,只有9行了



```shell
root@LAPTOP-UN694I4M:/home# cat a.txt > aa.txt
root@LAPTOP-UN694I4M:/home# cat  -n aa.txt
     1  总用量 0
     2  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
     3  -rw-r--r-- 1 root    root       0 2月  10 20:33 a.txt
     4  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
     5  -rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
     6  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
     7  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
     8  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
     9  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home# cat -n a.txt
     1  总用量 0
     2  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
     3  -rw-r--r-- 1 root    root       0 2月  10 20:33 a.txt
     4  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
     5  -rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
     6  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
     7  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
     8  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
     9  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#
```



****



第4点，将“hello Linux!”写入到a.txt中



这里是将内容写入已有内容的文件中，使用追加符号

使用指令 `echo "hello Linux!" >> a.txt`



可以看到原来9行的a.txt文件变成了10行

```shell
root@LAPTOP-UN694I4M:/home# echo "hello Linux!" >> a.txt
root@LAPTOP-UN694I4M:/home# cat -n a.txt
     1  总用量 0
     2  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
     3  -rw-r--r-- 1 root    root       0 2月  10 20:33 a.txt
     4  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
     5  -rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
     6  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
     7  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
     8  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
     9  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
    10  hello Linux!
root@LAPTOP-UN694I4M:/home# 
```





****

案例0，将/home目录下的文件列表  追加到hello3.txt文件中



使用指令 `ls -l >> hello3.txt`，**将查看列表返回的结果追加到文件中**



```shell
root@LAPTOP-UN694I4M:/home# ls -l >> hello3.txt
root@LAPTOP-UN694I4M:/home# cat -n hello3.txt
     1  hello Linux!
     2
     3  总用量 0
     4  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
     5  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
     6  -rw-r--r-- 1 root    root      14 2月  10 20:18 hello3.txt
     7  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
     8  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
     9  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
    10  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#
```





案例1：将/home目录下的文件列表 写入到/home/hello3.txt中



使用指令 `ls -l > hello3.txt`

```shell
root@LAPTOP-UN694I4M:/home# ls -l > hello3.txt
root@LAPTOP-UN694I4M:/home# cat -n hello3.txt
     1  总用量 0
     2  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
     3  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
     4  -rw-r--r-- 1 root    root       0 2月  10 20:25 hello3.txt
     5  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
     6  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
     7  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
     8  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#
```





可以看出来，原来的内容被覆盖了{hello Linux！  消失了}，**查看出来的列表内容覆盖了hello3.txt文件中的原内容**



****



案例2：将当前日历信息 追加到/home/a.txt文件中 {提示cal}



**指令 `cal`显示当前日历**

```shell
root@LAPTOP-UN694I4M:/home# cal
      二月 2020
日 一 二 三 四 五 六
                   1
 2  3  4  5  6  7  8
 9 10 11 12 13 14 15
16 17 18 19 20 21 22
23 24 25 26 27 28 29

root@LAPTOP-UN694I4M:/home# 
```



将cal的内容追加到 /home/a.txt



```shell
root@LAPTOP-UN694I4M:/# cal >> /home/a.txt
root@LAPTOP-UN694I4M:/# cal >> /home/a.txt
root@LAPTOP-UN694I4M:/# cal >> /home/a.txt
root@LAPTOP-UN694I4M:/# cal >> /home/a.txt
root@LAPTOP-UN694I4M:/# cat -n /home/a.txt
     1  总用量 0
     2  drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
     3  -rw-r--r-- 1 root    root       0 2月  10 20:33 a.txt
     4  -rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
     5  -rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
     6  drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
     7  drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
     8  drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
     9  -rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
    10  hello Linux!
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20  exit
    21        二月 2020
    22  日 一 二 三 四 五 六
    23                     1
    24   2  3  4  5  6  7  8
    25   9 10 11 12 13 14 15
    26  16 17 18 19 20 21 22
    27  23 24 25 26 27 28 29
    28
    29        二月 2020
    30  日 一 二 三 四 五 六
    31                     1
    32   2  3  4  5  6  7  8
    33   9 10 11 12 13 14 15
    34  16 17 18 19 20 21 22
    35  23 24 25 26 27 28 29
    36
    37        二月 2020
    38  日 一 二 三 四 五 六
    39                     1
    40   2  3  4  5  6  7  8
    41   9 10 11 12 13 14 15
    42  16 17 18 19 20 21 22
    43  23 24 25 26 27 28 29
    44
    45        二月 2020
    46  日 一 二 三 四 五 六
    47                     1
    48   2  3  4  5  6  7  8
    49   9 10 11 12 13 14 15
    50  16 17 18 19 20 21 22
    51  23 24 25 26 27 28 29
    52
root@LAPTOP-UN694I4M:/#
```



我们可以看到日历与`hello Linux!`之间有空行和exit

这时使用键盘录入的结果

使用的指令

`cat >> 文件名`

cal错写成了cat。。产生的录入

****

**总结：**

**输出重定向：**

`带返回值的指令 > 文件名`

把该指令的返回值写入某文件中，如果某文件不存在则创建该文件，，如果某文件存在则覆盖该文件原来的内容



**追加：**

`带返回值的指令 >> 文件名`

把该指令的返回值写入某文件中，如果某文件不存在则创建该文件，如果某文件存在则追加到该文件原来的内容的末尾



`cat  文件a >>  文件b` 这样的指令也是将用Cat查看文件a的返回值写入到文件b中



**特殊的：**

`echo "内容" >> 文件名`

使用 `echo`指令可以将内容之间写入文件中

`echo` "内容"这个指令的返回值就是内容

```shell
root@LAPTOP-UN694I4M:/# echo "hello java"
hello java
root@LAPTOP-UN694I4M:/#
```



****



## 输出内容到控制台：`echo`



将查看的内容返回到控制台

**基本语法：**

echo [选项] [输出内容]



****

**应用实例**

案例：使用echo指令**输出环境变量**

使用指令 `echo $PATH`



```shell
root@LAPTOP-UN694I4M:/# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```



****

案例：使用echo指令输出hello,world!

这个类似于交互式/键盘录入



```shell
root@LAPTOP-UN694I4M:/# echo "hello java"
hello java
root@LAPTOP-UN694I4M:/#
```





****

## 用于显示文件的开头部分内容，默认情况下head指令显示的前10行内容  ：`head`



**基本语法：**

head 文件    (功能描述： 查看文件前10行内容)

head -n x 文件  （功能描述: 查看文件前x行内容，x可以是任意行数）



查看/etc/profile 的前10行代码

```shell
root@LAPTOP-UN694I4M:/# head /etc/profile
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
```



**应用实例：**

案例：查看/etc/profile 的前5行代码

使用指令 `head -n 5 /etc/prpfile`

```shell
root@LAPTOP-UN694I4M:/# head -n 5 /etc/profile
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
root@LAPTOP-UN694I4M:/#
```







****

## 用于输出文件尾部的内容{和head刚好相反}，默认情况下tail指令显示文件的后10行内容  : `tail`



**基本语法：**

1）tail 文件      （功能描述：查看文件后10行内容）

2） tail -n x 文件  （功能描述： 查看文件后x行内容，x可以是任意行数）

3） tail -f 文件       （功能描述： 实时追踪该文档的所有更新。**工作中经常使用**）



**应用实例：**

案例1： 查看/etc/profile 最后5行代码

```shell
root@LAPTOP-UN694I4M:/# tail -n 5 /etc/profile
      . $i
    fi
  done
  unset i
fi
root@LAPTOP-UN694I4M:/#
```





****

案例2： 实时监控mydate.txt,看看文件是否有变化，如果有变化则追加日期

```shell
root@LAPTOP-UN694I4M:/# cd home
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  dir2  hello3.txt  mochou5  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home# tail -f mydate.txt
tail: 无法打开'mydate.txt' 读取数据: 没有那个文件或目录
tail: 没有剩余文件
root@LAPTOP-UN694I4M:/home#
```



额。。Ubuntu又没有。。。

看示例吧

![ ](C:\Users\fucker\Pictures\Linux15.PNG)

后面  ` 总用量52` 以后都是右边执行指令  `ls -l >> mydate.txt`，按下回车后    实时更新的

![](C:\Users\fucker\Pictures\Linux17.png)



自己创建一共mydate.txt的空文件

使用指令 `touch mydate.txt`

```shell
root@LAPTOP-UN694I4M:/home# touch mydate.txt
root@LAPTOP-UN694I4M:/home# tail -f mydate.txt
s

ssss
hello Linux!
^C
root@LAPTOP-UN694I4M:/home# tail  -f  mydate.txt
^C
root@LAPTOP-UN694I4M:/home# tail mydate.txt
root@LAPTOP-UN694I4M:/home# head mydate.txt
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  dir2  hello3.txt  mochou5  mydate.txt  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home# cat -n mydate.txt
root@LAPTOP-UN694I4M:/home# more mydate.txt
root@LAPTOP-UN694I4M:/home# nano mydate,txt
root@LAPTOP-UN694I4M:/home# 
```



ctrl+c 退出



![](C:\Users\fucker\Pictures\Linux16.PNG)

空文件。。。因此三次查看命令无法打开

Vim/nano 编辑实际上是删除本文件，并生成了新的同名文件

****

软链接指令 ：`ln`

**什么是软链接？**

软链接也叫符号链接，**类似于windows里的快捷方式**，主要存放了链接其他文件的路径



**基本语法：**

ln -s [原文件或目录] [软链接名]  (功能描述：给原文件创建了一共软链接)



**应用实例**

案例1：在/home 目录下创建一个软链接 linkToRoot，连接到root目录

使用指令 `ln -s /root linkToRoot`，它表示**在当前目录下创建一个root目录的软链接linkToRoot**。root是原目录/文件，linkToRoot表示软链接文件





```shell
root@LAPTOP-UN694I4M:/home# ln -s /root linkToRoot
root@LAPTOP-UN694I4M:/home# ls -l
总用量 8
-rw-r--r-- 1 root    root     465 2月  10 20:48 aa.txt
drwxr-xr-x 1 root    root    4096 2月   9 14:42 animal
-rw-r--r-- 1 root    root    1288 2月  10 21:08 a.txt
-rw-r--r-- 1 root    root       0 2月  10 16:42 dir2
-rw-r--r-- 1 root    root     410 2月  10 20:25 hello3.txt
lrwxrwxrwx 1 root    root       5 2月  10 22:49 linkToRoot -> /root
drwxr-xr-x 1 mochou5 mochou5 4096 2月   5 16:35 mochou5
-rw-r--r-- 1 root    root       0 2月  10 22:15 mydate.txt
drwxr-xr-x 1 root    root    4096 2月   5 16:30 tiger
drwxr-xr-x 1 root    root    4096 2月  10 17:25 zwj
-rwxr-xr-x 1 root    root     360 2月  10 19:31 看这里.txt
root@LAPTOP-UN694I4M:/home#
```



我们可以看到其中有 `linkToRoot -> /root`，表示的是 ，如果*打开 linkToRoot,会跳转到root中{虽然pwd查看的当前目录依旧是linkToRoot,没有进行下一步操作时会是 linkToRoot目录下，进行下一步操作就会将指令转到root目录，对root目录进行操作}，实际上是打开了root* {和快捷方式是一样的}

```shell
root@LAPTOP-UN694I4M:/home/linkToRoot# pwd
/home/linkToRoot
root@LAPTOP-UN694I4M:/home/linkToRoot# ls -l
总用量 0
root@LAPTOP-UN694I4M:/home/linkToRoot# ls -al
总用量 12
drwx------ 1 root root 4096 2月   6 16:15 .
drwxr-xr-x 1 root root 4096 2月  10 17:22 ..
-rw------- 1 root root 3625 2月  10 21:07 .bash_history
-rw-r--r-- 1 root root 3106 4月   9  2018 .bashrc
drwxr-xr-x 1 root root 4096 2月   5 14:32 .local
-rw-r--r-- 1 root root  148 8月  17  2015 .profile
-rw------- 1 root root 2412 2月   6 16:15 .viminfo
root@LAPTOP-UN694I4M:/home/linkToRoot#
```



打开root，查看root的

```shell
root@LAPTOP-UN694I4M:/# cd /root
root@LAPTOP-UN694I4M:~# ls -al
总用量 12
drwx------ 1 root root 4096 2月   6 16:15 .
drwxr-xr-x 1 root root 4096 2月  10 17:22 ..
-rw------- 1 root root 3625 2月  10 21:07 .bash_history
-rw-r--r-- 1 root root 3106 4月   9  2018 .bashrc
drwxr-xr-x 1 root root 4096 2月   5 14:32 .local
-rw-r--r-- 1 root root  148 8月  17  2015 .profile
-rw------- 1 root root 2412 2月   6 16:15 .viminfo
root@LAPTOP-UN694I4M:~#
```



****

案例2：删除软链接linkToRoot

软链接实际上还是属于目录，因此 `rm`删除时需要 带参数 `-rf`



```shell
root@LAPTOP-UN694I4M:~# cd /home
root@LAPTOP-UN694I4M:/home# ls
aa.txt  a.txt  hello3.txt  mochou5     tiger  看这里.txt
animal  dir2   linkToRoot  mydate.txt  zwj
root@LAPTOP-UN694I4M:/home# rm -rf linkToRoot
root@LAPTOP-UN694I4M:/home# ls
aa.txt  animal  a.txt  dir2  hello3.txt  mochou5  mydate.txt  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home#
```



![](C:\Users\fucker\Pictures\Linux18.png)



因为带 `/`后表示的是删除链接以及链接里面的内容{root目录？？}，而不是链接本身





****

**细节说明：**

当我们使用pwd指令查看目录时，仍然看到的是软链接所在目录

```

```

****

## 查看以及执行过的指令 ：`history`



**基本语法**

history  (功能描述：查看已经执行过的历史命令)



**应用实例：**

案例1：显示所有历史命令

直接输出 `history`

```shell
root@LAPTOP-UN694I4M:/home# history
    1  useradd xm
    2  ls
    3  cd /home/
    4  ls
    5  useradd xiaoming
    .....省略分隔。。。。。
```





案例2：显示最近执行过的10个指令



案例3：执行{指令的}历史编号为2的指令

使用指令 `！2`，表示执行编号为2的指令 {执行时先查询到历史编号为2的指令，然后再调用这个指令}

```shell
root@LAPTOP-UN694I4M:/home# !2
ls
aa.txt  animal  a.txt  c.txt  dir2  hello3.txt  mochou5  mydate.txt  tiger  zwj  看这里.txt
root@LAPTOP-UN694I4M:/home#
```

可以看到编号为2 的指令是ls，因此它调用了ls这个指令





**history >> [文件]  可以将历史指令追加到文件中，用来记录工作记录**

```shell
root@LAPTOP-UN694I4M:/# cd /home
root@LAPTOP-UN694I4M:/home# history >> c.txt
root@LAPTOP-UN694I4M:/home# cat -n c.txt
     1      1  useradd xm
     2      2  ls
     3      3  cd /home/
     4      4  ls
     5      5  useradd xiaoming
     6      6  ls
     7      7  mkdir tiger
     。。。。。。。。。省略分隔符。。。。。。。。。。。。。
   399    399  rm -rf linkToRoot
   400    400  ls
   401    401  cd /
   402    402  cd /home
   403    403  history >> c.txt
```

可以看到这里显示的指令中，**没有哪些在其他账户中执行的指令，只有当前账户的**

文件系统原来

****

#   实用指令--时间日期类

##  显示当前日期：`date`



**基本语法：**

1）date        (功能描述：  显示当前时间 )

2）date+%Y    (功能描述：显示当前年份)

3）date+%m    (功能描述：显示当前月份)

4）date+%d      (功能描述： 显示当前是哪一天)

5）date"+%Y-%m-%d-%H:%M:%S"   (功能描述：显示年月日时分秒)



**应用实例：**

案例1：显示当前时间信息



```shell
root@LAPTOP-UN694I4M:/home# date > a.txt
root@LAPTOP-UN694I4M:/home# cat -n a.txt
     1  2020年 02月 11日 星期二 12:21:44 CST
```

 



****



案例2：显示当前时间年月日



```shell
root@LAPTOP-UN694I4M:/home# date "+%Y-%m-%d" >> a.txt
root@LAPTOP-UN694I4M:/home# cat -n a.txt
     1  2020年 02月 11日 星期二 12:21:44 CST
     2  2020-02-11
root@LAPTOP-UN694I4M:/home# 
```



年月日是 `“+%Y-%m-%d”`,`+`号在`“”`里面。`%Y`代表年，`%m`代表月，`%d`代表日。三者之间通过 `-`号连接，**空格也可以当做连接符用**





****

案例3：显示当前年月日时分秒



```shell
root@LAPTOP-UN694I4M:/home# date "+%Y %m %d %H:%M:%S" >> a.txt
root@LAPTOP-UN694I4M:/home# cat -n a.txt
     1  2020年 02月 11日 星期二 12:21:44 CST
     2  2020-02-11
     3  2020 02 11 12:31:48
root@LAPTOP-UN694I4M:/home# 
```



可以看到用 `-`作为连接符，显示就是`2020-02-11`

而应用空格和冒号做连接符，显示就是 `2020 02 11 12:31:48`

****

## 设置日期：`date`



**基本语法：**

date -s 字符串时间

```

```





**应用实例**

案例1：设置系统当前时间，比如设置成`2020-11-11 11：22：22`

```shell
root@LAPTOP-UN694I4M:/home# date -s "2020-10-11 11:22:22"
2020年 10月 11日 星期日 11:22:22 CST
root@LAPTOP-UN694I4M:/home# date
2020年 02月 11日 星期二 12:42:16 CST
root@LAPTOP-UN694I4M:/home# 
```



额。。。Ubuntu系统。。。设置时间后 ，又会被重置成当前时间{因为时间和w10同步或者和网络同步？？？}



时间设置回来：**校准为网络时间**

`ln -sf /user/share/zoneinfo/Asia/Shanghai /etc/localtime`



****

## 查看日历指令：`cal`

**基本语法：**

cal [选项]  （功能描述：不加选项，显示本月日历）





**应用实例**



案例1:显示当前日历

```shell
root@LAPTOP-UN694I4M:/home# cal
      二月 2020
日 一 二 三 四 五 六
                   1
 2  3  4  5  6  7  8
 9 10 11 12 13 14 15
16 17 18 19 20 21 22
23 24 25 26 27 28 29

root@LAPTOP-UN694I4M:/home#

```



案例2：显示2020年日历

```shell
root@LAPTOP-UN694I4M:/home# cal 2020
                            2020
         一月                    二月                    三月
日 一 二 三 四 五 六  日 一 二 三 四 五 六  日 一 二 三 四 五 六
          1  2  3  4                     1   1  2  3  4  5  6  7
 5  6  7  8  9 10 11   2  3  4  5  6  7  8   8  9 10 11 12 13 14
12 13 14 15 16 17 18   9 10 11 12 13 14 15  15 16 17 18 19 20 21
19 20 21 22 23 24 25  16 17 18 19 20 21 22  22 23 24 25 26 27 28
26 27 28 29 30 31     23 24 25 26 27 28 29  29 30 31


         四月                    五月                    六月
日 一 二 三 四 五 六  日 一 二 三 四 五 六  日 一 二 三 四 五 六
          1  2  3  4                  1  2      1  2  3  4  5  6
 5  6  7  8  9 10 11   3  4  5  6  7  8  9   7  8  9 10 11 12 13
12 13 14 15 16 17 18  10 11 12 13 14 15 16  14 15 16 17 18 19 20
19 20 21 22 23 24 25  17 18 19 20 21 22 23  21 22 23 24 25 26 27
26 27 28 29 30        24 25 26 27 28 29 30  28 29 30
                      31

         七月                    八月                    九月
日 一 二 三 四 五 六  日 一 二 三 四 五 六  日 一 二 三 四 五 六
          1  2  3  4                     1         1  2  3  4  5
 5  6  7  8  9 10 11   2  3  4  5  6  7  8   6  7  8  9 10 11 12
12 13 14 15 16 17 18   9 10 11 12 13 14 15  13 14 15 16 17 18 19
19 20 21 22 23 24 25  16 17 18 19 20 21 22  20 21 22 23 24 25 26
26 27 28 29 30 31     23 24 25 26 27 28 29  27 28 29 30
                      30 31

         十月                   十一月                   十二月
日 一 二 三 四 五 六  日 一 二 三 四 五 六  日 一 二 三 四 五 六
             1  2  3   1  2  3  4  5  6  7         1  2  3  4  5
 4  5  6  7  8  9 10   8  9 10 11 12 13 14   6  7  8  9 10 11 12
11 12 13 14 15 16 17  15 16 17 18 19 20 21  13 14 15 16 17 18 19
18 19 20 21 22 23 24  22 23 24 25 26 27 28  20 21 22 23 24 25 26
25 26 27 28 29 30 31  29 30                 27 28 29 30 31

root@LAPTOP-UN694I4M:/home# 

```



****



# Typora的缺陷，写大文档卡成 PPT，建议超过1万字后，开新的文档











****

# 附录：**输入命令的时候要常用tab键来补全**

- `ls`：显示文件或目录信息
- `mkdir`：当前目录下创建一个空目录
- `rmdir`：要求目录为空
- `touch`：生成一个空文件或更改文件的时间
- `cp`：复制文件或目录
- `mv`：移动文件或目录、文件或目录改名
- `rm`：删除文件或目录
- `ln`：建立链接文件
- `find`：查找文件
- `file/stat`：查看文件类型或文件属性信息
- `cat：`查看文本文件内容
- `more：`可以分页看
- `less：`不仅可以分页，还可以方便地搜索，回翻等操作
- `tail -10`： 查看文件的尾部的10行
- `head -20`：查看文件的头部20行
- `echo`：把内容重定向到指定的文件中 ，有则打开，无则创建
- `管道命令 |` ：将前面的结果给后面的命令，例如：`ls -la | wc`，将ls的结果加油wc命令来统计字数
- `重定向 > 是覆盖模式，>> 是追加模式`，例如：`echo "Java3y,zhen de hen xihuan ni" > qingshu.txt`把左边的输出放到右边的文件里去

学了这些命令我们能干嘛？**其实就是在Windows下复制文件、粘贴文件、创建文件、查看文件这几种**~~~