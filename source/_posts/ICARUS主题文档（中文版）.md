---
title: ICARUS主题中文文档 · 配置
date: 2020-02-11 19:55:06
tags:
 - Hexo
 - Icarus
 - 文档
categories:
 - 干货
toc: true
thumbnail: https://pic.imgdb.cn/item/5e43a6972fb38b8c3ccc5add.jpg
---

> 原文来自[PPOffice](https://github.com/ppoffice)的[ICARUS主题文档](https://blog.zhangruipeng.me/hexo-theme-icarus/categories/)，由[猫梨（nek0ri）](https://nek0ri.de)进行英译中的翻译，本文档翻译遵循[MIT](https://opensource.org/licenses/MIT)协议。
>
><!--more-->
>
> 译者水平有限，另时间较为仓促，若其中存在错误，期待您的指正！
>
> 我的个人网页：[nek0ri.de](https://nek0ri.de)
>
> 个人邮箱：[nek0ri@outlook.com](nek0ri@outlook.com)

# ICARUS主题文档（配置篇）

图 / 不详（侵删）

注：带“*”为进阶操作，`主题配置文件`为`themes`目录下Icarus文件夹内的`_config.yml`文件。

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

你放在`front-matter`中的图像路径需要和你**站点**下的`source`目录相关联。比如，当你想使用以下的图像作为缩略图：

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

</br>

### 2. 主题

#### 2.1 配置Icarus

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

在全局主题配置外，你也可以在每篇文章中进行定制。也就是说，你可以在一篇文章页中推翻主题的配置。我们假设你想要在某篇文章中显示不同的导航栏菜单，而你仅需将`navbar`设置放在文章的`front-matter`中：

```markdown
navbar:
    menu:
        Home: /
        Special!: /special
```

你在此处设定的配置仅仅会影响这篇文章。这一特征对于为特定的读者展示定制化的/最优化的页面是十分有用的。例如，你可以启用更快的CDN或者页面访问者所在的国家和语言的本地化评论服务。

___

#### 2.2 多样的链接设置

你或许已经注意到Icarus允许你将如下格式的图标链接放在导航栏右侧，个人档案部件底部，与页脚的右侧：

```yml
footer:
    links:
        'Creative Commons':
            icon: fab fa-creative-commons
            url: 'https://creativecommons.org/'
        'Attribution 4.0 International':
            icon: fab fa-creative-commons-by
            url: 'https://creativecommons.org/licenses/by/4.0/'
```

在以上链接的格式中，你需要具体说明链接的名字（例如：知识共享），图标的类名称（比如Front Awesome类名称）和链接的URL。然而，Icarus也接受以下格式带链接名和URL的纯文字链接：

```yml
footer:
    links:
        'Creative Commons': 'https://creativecommons.org/'
        'Attribution 4.0 International': 'https://creativecommons.org/licenses/by/4.0/'
```

___

#### 2.3 用自定义的CDN来加速你的站点*

利用正确的CDN供应商可以加速你网站访问者加载网页的过程。同时Icarus允许你明确规定你想要使用的第三方静态库的CDN供应商。

**内置的CDN供应商**

目前你可以在以下内置的供应商中选择：

- **常规CDN**
    - CDN.js (cdnjs)
    - jsDelivr (jsdelivr)
    - Unpkg (unpkg)

- **字体CDN**
    - Google Fonts (google)

- **图标字体CDN**
    - Font Awesome (fontawesome)

默认的CDN设置如下：

```yml
providers:
    cdn: jsdelivr
    fontcdn: google
    iconcdn: fontawesome
```

**自定义CDN供应商**

除此之外，你也可以使用自定义的CDN供应商，你只需将他们的URL放在配置文件中。对于常规的CDN，你应该提供以下字符串格式的URL：

```yml
https://some.cdn.domain.name/${package}/${version}/${filename}
```

你需要使用`${package}`，`${version}`和`${filename}`占位符更换实际的包名称，包的版本以及相应的文件路径。比如，如下URL的JavaScript库：

```yml
https://unpkg.com/d3@5.7.0/dist/d3.min.js
```

可以被归纳为这样：

```yml
https://unpkg.com/${package}@${version}/${filename}
```

你应该知道，CDN供应商可能采用不同库的URL体系，即库的包名称与文件路径不是完全一致的。比如，`moment.js`库在CDN.js的URL是这样的：

```yml
https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.22.2/moment.js
```

然而在Unpkg中URL是如下这样：

```yml
https://unpkg.com/moment@2.22.2/min/moment.min.js
```

因此，你应该留意你自定义CDN供应商的URL格式。默认上，Icarus将尝试传入参数，就像对npm仓库（例如`moment@2.22.2/min/moment.min.js`）那样。这一npm体系被jsDelivr和Unpkg所采用。但如果你在用类似于CDN.js那样的供应商，请前置`[cdnjs]`在其格式串中：

```yml
[cdnjs]https://some.cdn.domain.name/${package}/${version}/${filename}
```

对于**字体CDN**，你可以传入一个Google Font镜像或适配的webfont（在线字体）CDN。Icarus依靠`Ubuntu`和`Source Code Pro`字体，因此确保你的CDN提供他们。URL应该为字体样式（图标`icon`或字体`font`）以及字体名安置两个占位符：

```yml
https://some.google.font.mirror/${type}?family=${fontname}
```

对于**图标CDN**，你可以用自定义的Font Awesome CDN传入URL，不需要占位符。你提供的自定义CDN应该至少有Font Awesome 5图标，因为其中有些会在该主题中被使用到。

```yml
https://custom.fontawesome.mirror/some.stylesheet.css
```

以上所有内容都应该放在`主题配置文件`的`provider`区域：

{% codeblock lang:yaml _config.yml %}
providers:
    cdn: 'https://some.cdn.domain.name/${package}/${version}/${filename}'
    fontcdn: 'https://some.google.font.mirror/${type}?family=${fontname}'
    iconcdn: 'https://custom.fontawesome.mirror/some.stylesheet.css'
{% endcodeblock %}

**CDN助手功能**

三个助手功能能够帮助开发者，轻易地包含在自定义CDN支持下的第三方库。你可以在Icarus主题文件夹下的`includes/helpers/cdn.js`查看他们。

___

#### 2.4 让侧边栏在页面滚动时固定住

有时你可能想要在你页面其他部分滚动的时候，侧边栏的位置保持固定。可以通过`主题配置文件`（即`_config.yml `）中的`sticky`侧边栏选项来实现。你可以单独设置某一边，或者让两边的侧边栏都被固定。

{% codeblock lang:yaml _config.yml %}
sidebar:
    left:
        sticky: false
    right:
        sticky: true
{% endcodeblock %}