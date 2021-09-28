---
title: Hexo中展示PDF文档
date: 2021-05-31 14:46:46
tags: Hexo
top: 9
---

# 简介
在网站中展示PDF是一个不错的主意，对于含有大量数学公式，使用LaTeX 排版的数学文档可以直接以这种方式展出，并提供下载。

从`Next` 主题官网中,知其支持PDF文档，查阅了很多文档，都没有把问题说清楚，故开此文，一则说明原理，二则准备发布关于`manjaro`的安装配置文档。


<!--more-->

# 开启PDF功能

配置文件位置为`~/文档/hexo/themes/next/_config.yml` ,修改如下

```
# PDF tag
# NexT will try to load pdf files natively, if failed, pdf.js will be used.
# So, you have to install the dependency of pdf.js if you want to use pdf tag and make it available to all browsers.
# Dependencies: https://github.com/next-theme/theme-next-pdf
pdf:
  enable: true
  # Default height
  height: 500px
```

如果插件没有安装，则按照配置文件中说明，从[next-pdf官网](https://github.com/next-theme/theme-next-pdf)对照说明安装即可。

# 插入PDF文件

在`~/文档/hexo/source/` 中新建一个文件夹 `PDF` 用以存放插入到文件中的PDF文档。在需要插入PDF文件的地方使用pdf标签即可，这里需要注意，有两种方式来插入pdf文件:

1. 使用外链的方式插入

```
{% pdf https://cdn.jsdelivr.net/gh/Justlovesmile/CDN/pdf/小作文讲义.pdf %}
```

上述地址，也是我的参考一篇文档[HEXO竟然可以展示PDF](https://www.freesion.com/article/21401006069) 中引用。

2. 使用内链

这个方式，正是许多网络文档解释不清楚的地方。在使用`hexo g` 命令构建网页时，它会将`source`中的`PDF`文件夹复制到`public`文件夹中，在填写PDF路径进应当是认为`public`主根目录，实际上我们发布的网站就是`public`中的所有文件。因此，我发布的`manjaro.pdf` 放置于`source/PDF/` 中，则文章中应当如下引用

```
{% pdf /PDF/manjaro.pdf %}
```

{% note warning %}
注意：在最初的引用时，我填写了具体的链接地址，当时是理解上存在问题。填写具体地址，虽然可以正常显示，但是在部署到不同的网站时由于域名不同，则新的部署将不能正常显示PDF文件。而`source/PDF/` 这个路径直接认为`source`为根目录，在使用hexo g生成博客时，会自动将此地址转换到加上域名的引用。所以这是一个最佳方案。由于网络上的文章`./PDF/manjaro.pdf`的写法是不对的，这也是之前一直没有成功的原因，2021年7月13日，对本文进行了修正,写成如上格式才是对的。
{% endnote %}


3. 嵌入manjaro.pdf文件展示

{% pdf /PDF/manjaro.pdf %}
