---
title: 更新至ICARUS 3.0
date: 2020-04-09 22:22:00
categories:
 - 干货
tags:
 - Hexo
 - Icarus
 - 文档
variant: cyberpunk
thumbnail: https://pic.imgdb.cn/item/5e8f3025504f4bcb048b5232.jpg
---

> 赛 伯 朋 克 ！

<!--more-->

表示站点驾驭不了这一风格，所以就设置了仅本页面有效，各位看看效果就好2333

源码可以前往Github Release页查看，[点击这里](https://github.com/ppoffice/hexo-theme-icarus/releases)。

</br>

表示没想到这个主题躺了许久之后，作者在前几天突然发布了一次大更新。虽说这一Hexo主题更新起来比较麻烦，不过看到加入了一些对我来说很实用的功能，因此毅然决定升级。

**若升级需注意一点：`images`文件夹改名为`img`，如果不是像我这样全站用图床保存图片，而是在本地存放的，建议修改下文件夹名称。**

## 本站更新

* 得益于新添加的`页面单独设置`功能，「关于」页去除了侧边Widget，使得页面能够更加简洁。

* 添加了`邮件订阅`功能。

* 未来会加入AdSense

* Valine加载速度更快了！

* 去除了文章`分享`功能（由于使用率几乎为0，因此决定去除以加快页面加载速度）

## 主题更新

使用该主题的各位可以参考一下官方的更新日志，衡量一下是否需要进行更新。

>### Breaking Changes
>
>* Completely rewrite layouts using JSX and Inferno.js
>
>* Reimplement configuration specification in JSON Schema, rewrite configuration validation and generation functions
>
>* Rewrite stylesheets and JavaScript scripts
>
>* Several configuration name and structure changes
>
>* Rename static image file folder from source/images to source/img
>
>* Remove the tag_cloud widget
>
>* Lots of the layouts, schemas, utility functions, and Hexo extensions have been moved to ppoffice/hexo-component-inferno
>
>### New Features
>
>* Add a new theme variant: Cyberpunk
>
>* Add support for layout-specific configurations: _config.post.yml and _config.page.yml
>
>* Introduce a new mechanism for migrating configurations to the latest version
>
>* Add Utterances comment plugin #625
>
>* Add Disqus.js comment plugin
>
>* Add Buy Me A Coffee donation button
>
>* Add CNZZ analytics support #584
>
>* Add Algolia search plugin #337
>
>* Add Google AdSense widget #451
>
>* Add KaTeX math renderer
>
>* Add structured data support #207
>
>* Add German translation #586
>
>* Add command-line flags to allow skip the configuration checking: --icarus-dont-generate-config, --icarus-dont-upgrade-config, --icarus-dont-check-config
>
>### Improvements
>
>* Speed up page generation and reduce memory footprint (use export NODE_ENV=production)
>
>* Code blocks now can be folded individually #576
>
>* Improved package dependency checking with version number checking
>
>* Load Valine comment plugin from CDN #574
>
>* Keyword highlight in Insight search plugin #418
>
>* A ton of bug fixes