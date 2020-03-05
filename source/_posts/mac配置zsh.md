---
title: macOS下配置ZSH和oh-my-zsh
date: 2020-02-28 21:00:00
tags: 
 - 终端
 - Mac
categories:
 - 干货
toc: true
thumbnail: https://pic.imgdb.cn/item/5e5909606127cc07132b7859.jpg
---

> 好用是其次，主要是好看（逃）

<!--more-->

图 / なかす

记得自己上学期做C语言的课后作业，一般都是在terminal里用GCC调试的，然而天天看着shell一成不变的样式未免有些视觉疲劳。

然后最近对着屏幕发呆，突然想到以前看到过人家终端用的shell是ZSH，主题相当漂亮，于是我就心血来潮也想尝试下了。（给我也整一个！.jpg）

![](https://pic.imgdb.cn/item/5e590ca76127cc07132be383.jpg)

> **测试证明macOS自带终端对oh-my-zsh兼容性不是很好，想要最好的体验建议使用iTerm**

___

先放效果图，使用的主题是`agnoster`。

![](https://pic.imgdb.cn/item/5e59059f6127cc07132aefee.png)

</br>

## 升级ZSH

一般我们Mac的终端没有配置时是这样的。

![](https://pic.imgdb.cn/item/5e590d5b6127cc07132bffb3.png)

当然，如果不想折腾shell，那也可以就修改下命令行提示符，在`~/.bash_profile`里把环境变量`PS1`改改，效果也是不错的。（例如我的MBP）

![](https://pic.imgdb.cn/item/5e590ec76127cc07132c30bd.jpg)

首先我们先确保Mac里是带ZSH的，输入`cat /etc/shells`。一般来说是以下的结果：

```
$ cat /etc/shells

/bin/bash
/bin/csh
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh
```

也就是macOS一般是自带很多shell的，其中就包括ZSH。但因为不知道自带的年代有多久远，还是更新下比较好。

我用的是brew，如果没有安装过的话请自行谷歌或者百度查看安装方式。假设已经装好brew了，那我们就输入`brew install zsh`（终端输出略）。

升级完成后，我们将终端从bash切换为zsh：

```
$ chsh -s /bin/zsh
Changing shell for xxx.
Password for xxx: 
```

输入密码，重启终端，搞定。

</br>

## 安装并配置oh-my-zsh

### 安装

然后我们就成功的切换到了zsh，然而看起来样式还是挺普通的（~~所以图略~~），那我们接下去安装oh-my-zsh。

我们可以用`curl`或者`wget`，从Github上下载.sh文件并执行。

方法一：

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
方法二：

```bash
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```
等它安装完成之后，我们再重启终端，然后就发现！

![](https://pic.imgdb.cn/item/5e59122e6127cc07132cbec6.png)

瞬间不一样啦。


### 配置

oh-my-zsh的配置文件是`~/.zshrc`，此处仅讨论主题与自动补全功能，其他内容请[点击这里](https://github.com/ohmyzsh/ohmyzsh)前往Github项目页查看。

#### 主题

我们用vim打开配置文件，发现默认的主题是`robbyrussell`：

![](https://pic.imgdb.cn/item/5e5917446127cc07132d7e4c.png)

如果想换其他主题，我们可以[这里](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)查看其自带的更多主题，这里我们使用`agnoster`主题。

~~如果你仔细看的话会发现，为了截图方便我已经事先注释好了嘿嘿~~

`Escape`、`:wq`、回车、重启终端。

然后大概率会出现这样的问题：

![](https://pic.imgdb.cn/item/5e5918e26127cc07132dc035.png)

实际上就是字体原因导致特殊字符无法正常显示，在此安利`powerline`字体。（点击[这里](https://github.com/powerline/fonts)查看powerline官方文档。）

换上自己喜欢的powerline字体，然后就显示正常啦：

![](https://pic.imgdb.cn/item/5e5918e26127cc07132dc032.png)

#### 自动补全功能（incr）*

来看下官方的Demo图，感觉是很有用的：

![](https://mimosa-pudica.net/img/zsh.gif)

我们可以通过[官网](https://mimosa-pudica.net/zsh-incremental.html)来下载。

安装步骤如下（此处有参考[一介布衣](http://yijiebuyi.com/blog/36955b84c57e338dd8255070b80829bf.html)）

```bash
$ cd /.oh-my-zsh/plugins
$ sudo mkdir incr
$ cd incr
#用管理员权限创建文件夹并进入
$ sudo mv ~/Downloads/incr-0.2.zsh  ~/.oh-my-zsh/plugins/incr/
#用管理员权限把下载下来的文件放入上面的路径中
$ ls
incr-0.2.zsh
#检查一下
$ chmod 777 incr*.zsh
#然后我们给拷贝进去的文件上最高权限
```

接下来，配置`~/.zshrc`文件：

```bash
$ vi ~/.zshrc
```

插入`source ~/.oh-my-zsh/plugins/incr/incr*.zsh`，参考第79行。（路径取决于你存放该文件的位置）

![](https://pic.imgdb.cn/item/5e591fa96127cc07132ec653.png)

保存并退出，输入`source ~/.zshrc`，然后

![](https://pic.imgdb.cn/item/5e5920416127cc07132edc25.png)

Enjoy! =w=