---
title: Next主题菜单项
date: 2021-07-12 11:50:21
tags: Hexo
---

# 菜单项的开启和设置

1. 打开主题配置文件 \_config.next.yml ,然后搜索 menu ，找到如下部分
```
# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If the translation for this item is available, the translated text will be loaded, otherwise the Key name will be used. Key is case-senstive.
# Value before `||` delimiter is the target link, value after `||` delimiter is the name of Font Awesome icon.
# External url should start with http:// or https://
menu:
  home: / || fa fa-home
  about: /about/ || fa fa-user
  tags: /tags/ || fa fa-tags
#  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
#  schedule: /schedule/ || fa fa-calendar
  sitemap: /sitemap.xml || fa fa-sitemap
#  commonweal: /404/ || fa fa-heartbeat
```
<!--more-->

2. 将要在首页显示的menu项前的注释符去掉，则开启对应项。但是在重新使用 `hexo g` 生成后，可以看到新增menu项，单击后却出现如下错误

```
Cannot GET /about/
Cannot Get /tags/
Cannot Get /categories/
```

这是因为还没有构建相关页面，执行如下命令新建相关页面

```
hexo n page "about"
hexo n page "tags"
hexo n page "categories"
```

运行后会在source文件夹下创建about、tags、categories文件夹，每个文件夹下会有创建一个index.md文件，编辑这三个文件可以自定义相关内容。

3. 打开各index.md文件，添加type,即可

```
---
title: About
date: 2021-07-12 10:39:26
type: "about"
---

---
title: Tags
date: 2021-07-12 10:39:37
type: "tags"
---
---
title: categories
date: 2021-07-12 10:39:53
type: "categories"
---
```

# 站点地图（sitemap)

## 简介

{% note success %}
站点地图描述了一个网站的架构。 它可以是一个任意形式的文档，用作网页设计的设计工具，也可以是列出网站中所有页面的一个网页，通常采用分级形式。这有助于访问者以及搜索引擎的爬虫找到网站中的页面。
{% endnote %}

## Hexo生成 sitemap

1. Google版本

```
# npm install hexo-generator-sitemap --save
```

2. Baidu版本

```
# npm install hexo-generator-baidu-sitemap --save
```

3. 生成站点地图

安装完成，在\_config.yml 中找到url,改成自己的域名

```
url: http://fengzhenhua-vip.github.io
permalink: :year/:month/:day/:title/
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
  trailing_html: true # Set to false to remove trailing '.html' from permalinks
```

这样，每次使用`hexo g`生成文件时，会自动在public文件夹下生成sitemap.xml和baidusitemap.xml分别用于Google和百度。

4. 查看

使用`hexo d`提交后，通过`域名/sitemap.xml`或`域名/baidusitemap.xml`可以进行诘问sitemap. 最后到Google或百度对应的站长工具进行提交sitemap就可以了。
