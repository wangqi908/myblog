---
title: ICARUS主题文档（中文版）
date: 2020-02-11 19:55:06
tags:
 - Hexo
 - Icarus
 - 文档
categories:
 - 干货
toc: true
---

# ICARUS主题文档（中文版）

> 原文来自[PPOffice](https://github.com/ppoffice)的[ICARUS主题文档](https://blog.zhangruipeng.me/hexo-theme-icarus/categories/)，由[猫梨（nek0ri）](https://nek0ri.de)进行英译中的翻译，本文档翻译遵循[MIT](https://opensource.org/licenses/MIT)协议。
>
> 译者水平有限，另时间较为仓促，若其中存在错误，期待您的指正！
>
> 我的个人网页：[nek0ri.de](https://nek0ri.de)
>
> 个人邮箱：[nek0ri@outlook.com](nek0ri@outlook.com)

<!--more-->

</br>

## 配置

### 1. 发布

#### 1.1 添加缩略图到你的文章

你可以用两个步骤来添加缩略图到你的文章。首先，确保`主题配置文件`中已经开启缩略图的功能：

{% codeblock lang:yaml _config.yml %}
article:
	thumbnail: true
{% endcodeblock %}


接下来，在你文章的`front-matter`中提供一个图像的链接或路径：

{% codeblock lang:markdown post.md %}
thumbnail: /gallery/thumbnails/desert.jpg
---
{% endcodeblock %}

**关于添加缩略图路径**

你放在`front-matter`中的图像路径需要和你**站点**下的`source`目录相关联的。比如，当你想使用以下的图像作为缩略图：

	/source/gallery/image.jpg

你需要用以下的内容作为图像路径：

	/gallery/image.jpg

此外，推荐你将所有图像放在和`_posts`文件夹相分开的专用资源文件夹中。

___

#### 1.2 目录表（Table of Contents / Catalogue）

要在发布页显示目录表（toc）部件，请先在你文章markdown文件的`front-matter`中添加`toc:true`：

{% codeblock lang:markdown post.md %}
title: Table of Contents Example
toc: true
---
Post content...
{% endcodeblock %}

接着，在`主题配置文件`添加`toc`部件：

{% codeblock lang:yaml _config.yml %}
widgets:
    -
        type: toc
        position: left
{% endcodeblock %}

> 效果演示请至[官方文档](https://blog.zhangruipeng.me/hexo-theme-icarus/Configuration/Posts/table-of-contents-catalogue/#toc)处
___

#### 1.3 Hexo内建标签插件指南

> 该主题的这部分指南是完全从Hexo官方文档拷贝的，请至[这里](https://blog.zhangruipeng.me/hexo-theme-icarus/Configuration/Posts/hexo-built-in-tag-helpers/#more)查看Hexo官方中文文档对标签插件使用方法的介绍。



### 2. 主题

#### 1.2 配置Icarus

Icarus的配置由两部分所组成：主题配置和文章配置。

**主题配置**

Icarus使用`_config.yml`文件来进行对全局页面布局、插件和部件的设置。它会检查配置并使其生效，指出任何的错误的配置，并当不存在配置文件时自动生成一个。你可以随时从`themes/icarus/includes/specs`文件夹中的`*.spec.js`文件查看明确说明。

默认主题配置由以下部分所组成：

- 站点偏好设置与页面元数据
- 顶部导航栏的链接
- 页脚的链接
- 文章显示的设置
- 评论、分享与搜索插件的设置
- 侧边栏部件的设置
- 其他显示与分析的插件
- CDN设置

大多数的设置已经记录在了`_config.yml`文件中。想要了解更多关于配置插件的详情， 你可以参考本文档（后续内容）。

**文章配置**

