---
title: 制作macOS安装U盘
date: 2020-03-05 12:30:00
tags: 
 - Mac
categories:
 - 干货
toc: true
thumbnail: https://pic.imgdb.cn/item/5e6084ea98271cb2b86eeba7.jpg
---

> 脑阔痛。

<!--more-->

图 / さけハラス

</br>

## 题外话

自己的iMac自从更新到macOS 10.14 Mojave后变得十分卡顿，甚至点开偏好设置都需要5-8秒，实在无语。问题是CPU的占用率是很低的，但系统就是很卡。

![](https://pic.imgdb.cn/item/5e60870e98271cb2b86fd79a.png)

而电脑的配置虽然放现在不算高但也不算糟糕吧...

![](https://pic.imgdb.cn/item/5e6083bc98271cb2b86e5ac4.png)

查阅了一下几个论坛，发现很多小伙伴的旧款机器（甚至是17、18年的顶配MacBook Pro）都在更新后出现了不同程度的卡顿问题。

鉴于没有什么好的解决方法，而最近因为语言、编程等学科的学习，需要安装的软件越来越多，实在无法忍受如此的卡顿，因此决定降级到10.12 Sierra。

</br>

## Before Start

我们需要：

 - 一个8G以上的U盘，由于后续要清空所以请不要放重要文件在里面
 - 一个macOS安装镜像（.dmg/.zip都行）
 - 一台Mac（黑苹果谨慎）

## 制作

### 准备U盘

插入U盘，点开`磁盘工具`，将其格式化为`Mac OS 扩展`，并起一个方便记忆的名字，以下我用`xxx`来代替U盘的名称。

![](https://pic.imgdb.cn/item/5e6083bc98271cb2b86e5abd.png)

### 准备安装程序

打开系统安装镜像，里面应该是叫做`安装macOS xxx`的应用程序，我们将其复制到`应用程序`文件夹中就好了。

接下来，开始制作安装盘。

### 制作安装盘

打开终端，输入以下内容：

注：

1. 因系统的不同，安装程序的名字会不同，如果当中有空格请在空格前加入反斜杠，否则终端会识别错误。比如“Install macOS Sierra.app”，应该写作`Install\ macOS\ Sierra.app`
2. 此处`xxx`为U盘的名称

```bash
sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/xxx/ --applicationpath /Applications/Install\ macOS\ Sierra.app/ --nointeraction
```
回车，输入密码，再回车。

出现`Done.`后，制作就完成啦。

### 安装

重启你的Mac，按照你Mac的外置驱动器引导快捷键`option`或者`Commmand+Option+P+R`（有些是`Command+R`等），选择你制作的盘并回车，进入安装。

另外，如果安装时提示：

> 这个安装macOS xxxx应用程序副本已损坏,不能用来安装macOS

退出安装程序，断开网络，点击`实用工具`-`终端`，输入`date 1025102016.20`并回车，应该就可以安装了。