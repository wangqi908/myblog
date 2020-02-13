---
title: ICARUS主题中文文档 · 插件与部件
date: 2020-02-12 20:46:45
tags:
 - Hexo
 - Icarus
 - 文档
categories:
 - 干货
toc: true
thumbnail: https://pic.imgdb.cn/item/5e43f5af2fb38b8c3cd9ff06.jpg
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

# ICARUS主题文档（插件与部件篇）

图 / 不详（侵删）

注：带“*”为进阶操作，`主题配置文件`为`themes`目录下Icarus文件夹内的`_config.yml`文件。

</br>

## 插件

### 1. 评论

> 官方文档已经列出了内置的所有评论插件，你可点击[这里](https://blog.zhangruipeng.me/hexo-theme-icarus/categories/Plugins/Comment/)前往官方文档，选中想要使用的评论插件后点击相应的`Installation instructions`，即可前往相应评论插件的官方教程处。

</br>

### 2. 捐赠

想要开启在文章内容下方的捐赠按钮，你需找到`主题配置文件`（即`_config.yml`）。目前Icarus支持以下捐赠入口，你可始终在你的博客使用一个或多个捐赠入口。

**支付宝**

```yml
donate:
    -
        type: alipay
        qrcode: # 指向你二维码图片的路径或链接
```

**微信**

```yml
donate:
    -
        type: wechat
        qrcode: # 指向你二维码图片的路径或链接
```

**Paypal**

你需要首先开启[Paypal Donate Button](https://www.paypal.com/donate/buttons/)。当你完成操作后请留意`business`和`currency_code`并将他们填入`_config.yml`。

```yml
donate:
    -
        type: paypal
        business: # 你Paypal的邮箱地址或者生成的business ID
        currency_code: # currency code
```

**Patreon**

```yml
donate:
    -
        type: patreon
        url: # 指向你Patreon页面的URL
```

</br>

### 3. 常规

#### 3.1 站点分析插件

> 官方文档已经列出了内置的所有分析插件，你可点击[这里](https://blog.zhangruipeng.me/hexo-theme-icarus/Plugins/General/site-analytics-plugin/)前往官方文档，选中想要使用的分析插件后点击相应的`Installation instructions`，即可前往相应分析插件的官方教程处。

____

#### 3.2 MathJax插件

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><mrow><mi>f</mi><mrow><mo>(</mo><mi>a</mi><mo>)</mo></mrow></mrow><mo>=</mo><mrow><mfrac><mn>1</mn><mrow><mn>2</mn><mi>&#x3C0;</mi><mi>i</mi></mrow></mfrac><msub><mo>&#x222E;</mo><mrow><mi>&#x3B3;</mi></mrow></msub><mfrac><mrow><mi>f</mi><mo>(</mo><mi>z</mi><mo>)</mo></mrow><mrow><mi>z</mi><mo>&#x2212;</mo><mi>a</mi></mrow></mfrac><mi>d</mi><mi>z</mi></mrow></math>

**配置**

要开启MathJax支持，你只需在`主题配置文件`中设置`plugins.mathjax = true`。

```yml
# Plugins
plugins:
    ...
    mathjax: true # options: true, false
```

需要更多MathJax配置，请编辑`/layout/plugin/mathjax.ejs`：

```js
document.addEventListener('DOMContentLoaded', function () {
    MathJax.Hub.Config({
        // Edit here
    });
});
```

**TeX和LaTeX输入**

> **注意**：请留意，当你在markdown文件中写TeX或LaTeX时，你需要用转义字符来防止某个符号被markdown解释程序处理。

输入

```
当 $a \ne 0$，\\(ax^2 + bx + c = 0\\) 有两个解，他们是
$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$
```

结果

当 $a \ne 0$，\\(ax^2 + bx + c = 0\\) 有两个解，他们是
$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

**MathML输入**

> **注意**：请留意，换行符可能会被markdown解释程序转化为标签，这回干涉MathML的注释，因此请在一行内写完MathML。

输入

```
当 <math xmlns="http://www.w3.org/1998/Math/MathML"><mi>a</mi><mo>&#x2260;</mo><mn>0</mn></math>，<math xmlns="http://www.w3.org/1998/Math/MathML"><mi>a</mi><msup><mi>x</mi><mn>2</mn></msup><mo>+</mo> <mi>b</mi><mi>x</mi><mo>+</mo> <mi>c</mi> <mo>=</mo> <mn>0</mn></math> 有两个解，他们是
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><mi>x</mi> <mo>=</mo><mrow><mfrac><mrow><mo>&#x2212;</mo><mi>b</mi><mo>&#x00B1;</mo><msqrt><msup><mi>b</mi><mn>2</mn></msup><mo>&#x2212;</mo><mn>4</mn><mi>a</mi><mi>c</mi></msqrt></mrow><mrow> <mn>2</mn><mi>a</mi> </mrow></mfrac></mrow><mtext>.</mtext></math>
```

结果

当 <math xmlns="http://www.w3.org/1998/Math/MathML"><mi>a</mi><mo>&#x2260;</mo><mn>0</mn></math>，<math xmlns="http://www.w3.org/1998/Math/MathML"><mi>a</mi><msup><mi>x</mi><mn>2</mn></msup><mo>+</mo> <mi>b</mi><mi>x</mi><mo>+</mo> <mi>c</mi> <mo>=</mo> <mn>0</mn></math> 有两个解，他们是
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block"><mi>x</mi> <mo>=</mo><mrow><mfrac><mrow><mo>&#x2212;</mo><mi>b</mi><mo>&#x00B1;</mo><msqrt><msup><mi>b</mi><mn>2</mn></msup><mo>&#x2212;</mo><mn>4</mn><mi>a</mi><mi>c</mi></msqrt></mrow><mrow> <mn>2</mn><mi>a</mi> </mrow></mfrac></mrow><mtext>.</mtext></math>

**AsciiMath输入**

> **注意**：请留意，当你在markdown文件中写AsciiMath的时候，你需要用转义字符来防止某个符号被markdown解释程序处理。

输入

```
当 \`a != 0\`，\`ax^2 + bx + c = 0\`有两个解，他们是<p style="text-align:center">\`x = (-b +- sqrt(b^2-4ac))/(2a) .\`</p>
```

结果

当 \`a != 0\`，\`ax^2 + bx + c = 0\`有两个解，他们是<p style="text-align:center">\`x = (-b +- sqrt(b^2-4ac))/(2a) .\`</p>

___

#### 3.2 图库（Gallery）插件

在`主题配置文件`（即`_config.yml`）中开启图库插件后，你只需在文章中添加一些图片即可创建图库：

```yml
plugins:
    gallery: true
```

此外，你还可以用齐行的图库（Justified Gallery）来展示网格化的照片集：

{% codeblock lang:html HTML + Markdown %}
&lt;div class="justified-gallery"&gt;
&lt;!-- 在这里需要一行空行来使得以下的markdown被显示 -->
![Elephant](/hexo-theme-icarus/gallery/animals/elephant.jpeg)
![Dog](/hexo-theme-icarus/gallery/animals/dog.jpeg)
![Birds](/hexo-theme-icarus/gallery/animals/birds.jpeg)
![Cat](/hexo-theme-icarus/gallery/animals/cat.jpeg)
![Fox](/hexo-theme-icarus/gallery/animals/fox.jpeg)
![Horse](/hexo-theme-icarus/gallery/animals/horse.jpeg)
![Leopard](/hexo-theme-icarus/gallery/animals/leopard.jpeg)
&lt;/div&gt;
{% endcodeblock %}

{% quote %}
由于本站（[nek0ri.de](https://nek0ri.de)）所有图片都使用图床，因此不便显示效果。效果请点击[这里](https://blog.zhangruipeng.me/hexo-theme-icarus/Plugins/General/gallery-plugin/#more)前往主题官方文档查看。
{% endquote %}

</br>

### 4. 搜索

> 官方文档已经列出了内置的所有搜索插件，你可点击[这里](https://blog.zhangruipeng.me/hexo-theme-icarus/categories/Plugins/Search/)前往官方文档，选中想要使用的搜索插件后点击相应的`Installation instructions`，即可前往相应搜索插件的官方教程处。

</br>

### 5. 分享

> 官方文档已经列出了内置的所有分享插件，你可点击[这里](https://blog.zhangruipeng.me/hexo-theme-icarus/categories/Plugins/Share/)前往官方文档，选中想要使用的分享插件后点击相应的`Installation instructions`，即可前往相应分享插件的官方教程处。

</br>

</br>

## 部件

### 个人档案侧边栏部件

Icarus以个人档案侧边栏部件的方式为你提供了一种展示你自己的方式。若要使用这一部件，请在你`主题配置文件`下部件的区域添加以下几行：

{% codeblock lang:yaml _config.yml %}
    -
        type: profile
        position: # 在左边或右边展示
        author: # 你的名字
        author_title: # 你的主题（描述）
        location: # 你在哪里
        avatar: # 你头像的路径或者URL
        gravatar: # 你gravatar的邮箱地址
        follow_link: # 任何你想前往的路径或URL
        social_links: # 在此处添加你社交网站的链接
{% endcodeblock %}

你需要注意两件事情：

 - 如果你想使用[Gravatar](https://en.gravatar.com/)，那就在`gravatar`区域填上你注册时的邮箱地址。否则，就让它空着，以防和你头像的设置起冲突。
 - `social_links`区域可以有大量的文字链接或者图标链接，你可以前往[ICARUS主题中文文档 · 配置](https://nek0ri.de/2020/02/11/icarus主题文档（中文版）/)的`多样的链接设置`查看详情。

</br>

### 侧边栏部件一览

由于这一全新的部件配置体系，你可以在页面任意一边轻易的设置部件。Icarus在部件已经定义的情况下，会读取在`主题配置文件`下已经启用的部件的列表，并将他们有序的显示出来。在Icarus 2.0.0中支持以下部件：

- Archives (archive) #归档
- Categories (category) #分类
- Links (links) #链接
- Profiles (profile) #个人档案
- Recent Posts (recent_posts) #最近的文章
- Tags (tag) #标签
- Tag Cloud (tagcloud) #标签云
- Table of Content / Catalogue (toc) #目录表

启用的部件会被定为一个队列，每个部件通常都有两个规定的区域：`type`（类型）和`position`（位置）。`type`（类型）区域明确被启用的部件，并且是**以上内容**的某个名称。一个部件的位置可以在`left`（左侧）或者`right`（右侧）。

```yml
widgets:
    -
        type: category
        position: left
    -
        type: tagcloud
        position: left
    -
        type: recent_posts
        position: right
    -
        type: archive
        position: right
    -
        type: tag
        position: right
```

这些部件大多都没有额外的配置。然而当你需要额外的配置，请参考之前的内容。

</br>

### 链接（Links）侧边栏部件

你可以在开启这一部件之后，在侧边栏展示前往其他网站的链接。你只需添加以下的内容在`主题配置文件`的`widgets`区域中即可启用：

```yaml
-
    type: links
    position: left
    links:
        '网站名称': 'http://website/url'
        Hexo: 'https://hexo.io'
        PPOffice: 'https://github.com/ppoffice'
```

需要留意一点，链接部件只为`网站名称`和`URL`建立列表，而`URL`显示在这一部件的右边。