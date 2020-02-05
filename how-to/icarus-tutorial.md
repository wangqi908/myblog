# ICARUS主题文档

## 设置

### 发布

#### 添加缩略图到你的文章：

你可以用两个步骤来添加缩略图到你的文章。首先，确保`站点配置文件`中已经开启缩略图的功能：

_config.yml

```YAML
article:
	thumbnail: true
```

接下里，提供一个图像的链接或路径在你文章的`front-matter`中：

post.md

```markdown

thumbnail: /gallery/thumbnails/desert.jpg
---

```

**关于添加题图路径**

你放在`front-matter`中的图像路径需要是和你**站点**下的`source`目录相关联的。比如，如果你想使用以下的图像作为缩略图：

	/source/gallery/image.jpg

你需要用以下的内容作为图像路径：

	/gallery/image.jpg

此外，推荐你将所有图像放在和`_posts`文件夹相分开的专门的资源文件夹中。

___

#### 内容表（Table of Contents / Catalogue）

要在发布页显示内容表（Toc）部件，请先在你文章markdown文件的`front-matter`中添加`toc:true`：

post.md

```Markdown
title: Table of Contents Example
toc: true
---
Post content...
```

接着，在`主题配置文件`添加`toc`部件：

_config.yml

```YAML
widgets:
    -
        type: toc
        position: left
```

___

#### 引用

[看这里](https://blog.zhangruipeng.me/hexo-theme-icarus/Configuration/Posts/hexo-built-in-tag-helpers/#more)