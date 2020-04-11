---
title: 从零开始搭建telegram RSS订阅bot
date: 2020-03-07 23:15:00
tags: 
 - Telegram
 - RSS
toc: true
categories:
 - 干货
thumbnail: https://pic.imgdb.cn/item/5e63b3f498271cb2b8f82ad6.jpg
---

从零开始的复读机

<!--more-->

图 ／ 「Sword Art Online」

平时经常用telegram，然而bot和频道从来没有尝试过。然后这两天心血来潮打算整个bot作为RSS订阅的转发机器人（复读机）。

经过一次次的测试，目前看下来效果最好的就是flowerss-bot。（点击[这里](https://github.com/indes/flowerss-bot)前往Github项目页）

如果感兴趣的话，也欢迎加入我新创建的频道和讨论群！（[频道](https://t.me/Radiori)和[讨论群](https://t.me/nek0ri_ne)）

那么，就开始吧。

</br>

## Before start

我们需要准备：

 - 一台服务器（建议VPS）
 - 一个telegram bot

嗯，很简单吧。


</br>

## 创建telegram bot

首先，我们在telegram中搜索@BotFather，然后按照提示输入`/newbot`，步骤很简单，在此就不详述了。

需要留意的是，在创建完bot之后，该账号会给你一个这个bot的`token`，请务必保存好。

## 安装Docker

这里使用的是CentOS 7 x86_64 bbr系统，如果是用的CentOS建议至少在v7及以上，以及系统需64位。

假设现在是在非root用户的情况下安装。（强烈不建议日常vps使用root账户）

首先安装所需的软件包。

```bash
$ sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
```

使用以下命令来设置稳定的仓库。

```bash
$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

然后安装安装 Docker Engine-Community

```bash
$ sudo yum install docker-ce docker-ce-cli containerd.io
```

启动docker

```bash
$ sudo systemctl start docker
```

通过运行 hello-world 映像来验证是否正确安装了 Docker Engine-Community 。

```bash
$ sudo docker run hello-world
```

如果没有出现什么错误提示，那到此已经安装完成了。

</br>

## 搭建RSS bot

### Docker部署

首先下载配置文件。

    $ mkdir ~/flowerss && wget -O ~/flowerss/config.yml https://raw.githubusercontent.com/indes/flowerss-bot/master/config.yml.sample

然后修改配置文件（yaml）

    $ vi ~/flowerss/config.yml

配置要输入你bot的`token`，另有些需要DIY的配置。

具体模版点击[这里](https://github.com/indes/flowerss-bot)查看。

（PS：强烈建议申请至少三个telegraph token！！！）

### 运行

    $ docker run -d -v ~/flowerss:/root/.flowerss indes/flowerss-bot

然后就可以运行啦。

试试给你的bot在telegram里面发送`/help`，有回复就说明运行正常！

## 停止

如果你那个参数觉得调的不太满意，那就让docker容器先停止。

查看你容器的id。

    $ docker ps -n 5

寻找flowerss-bot所在的`CONTAINER ID`，然后

    $ docker stop CONTAINER_ID

在`CONTAINER_ID`处用你前面找到的CONTAINER ID替换。

然后再编辑配置文件：

    $ vi ~/flowerss/config.yml

配置完成后，再运行容器：

    $ docker run -d -v ~/flowerss:/root/.flowerss indes/flowerss-bot

</br>

嘛，就是这样啦。

Enjoy!

> 参考链接：
>
> Runnoob - CentOS Docker安装 [https://www.runoob.com/docker/centos-docker-install.html](https://www.runoob.com/docker/centos-docker-install.html)
>
> flowerss-bot [https://github.com/indes/flowerss-bot](https://github.com/indes/flowerss-bot)
