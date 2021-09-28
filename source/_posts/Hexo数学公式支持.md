---
title: Hexo数学公式支持
date: 2021-05-27 16:41:50
tags: Hexo
top: 7
---

## 简介

作为物理老师，我是不能离开数学公式的。最初我是想在博客上能发布一些物理公式，回答学生的一些问题，但是作为初入hexo的人，我选择了默认的landscape模板，于是决定在此默认模板上添加数学支持，但是折腾了两天要么在手机上可以显示公式，但是电脑上不能显示，要么在电脑上显示公式（不完美显示），但是在手机上却不能显示。所以在参考了大量网络文章后决定切换主题，使用别人修改好的主题，其中next主题广受好评，同时其风格也得到我的认可，其对数学公式的支持也最完美，所以我的博客自今日起采用next模板。首先展示一下数学公式：

1. 行内公式:爱因斯坦的质能方程$e=mc^2$

2. 行间公式:库仑定律


$$\begin{equation}
F=k\frac{q_1q_2}{r^2}
\end{equation}$$


<!--more-->


## 安装next主题

````
$git clone https://github.com/next-theme/hexo-theme-next  ~/文档/hexo/theme/next
````

## 启用next主题

在主配置文件 ~/文档/hexo/\_config.yml 中将主题切换为 next

```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
#theme: landscape
theme: next
```

## 配置数学支持

1. 卸载默认的公式渲染插件

```
$npm uninstall hexo-renderer-marked --save
$npm uninstall hexo-math --save
```

2. 安装next所需的公式渲染插件

```
$npm install hexo-filter-mathjax --save
$npm install hexo-renderer-pandoc --save
```

按照[hexo-filter-mathjax 官网]( https://github.com/next-theme/hexo-filter-mathjax ) 所述：

WARNING:No front-end scripts and other Math plugins are required.Remove them ALL before using this plugin.

所以我按照要求删除了默认的插件，同时如果按照网络上的其他文章，按装过其他插件也务必要删除干净。

按照[next主题官网]( https://theme-next.js.org/docs/third-party-services/math-equations) 仅安装渲染插件 hexo-renderer-pandoc 即可，官网说

hexo-renderer-pandoc is recommended because it can handle mathematical formulas in markdown documents perfectly.


3. 由于插件 hexo-renderer-pandoc 需要pandoc支持，所以需要先在系统中安装pandoc 

```
$pacman -S pandoc
```

4. 开启数学公式功能

此处为了保险，按照next主题官网的配置进行.设置主题配置文件~/文档/hexo/themes/next/\_config.yml
  
```  
math:
  # Default (false) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in front-matter.
  # If you set it to true, it will load mathjax / katex srcipt EVERY PAGE.
  every_page: true

  mathjax:
    enable: true
    # Available values: none | ams | all
    tags: ams 
```

在官网中设置 every_page: false ,其考虑的是在没有数学公式的情况下不开启mathjax 以提高网页加载速度。但是在测试进我发现，网页是正常，但是我在文章中使用了<--!more-->设置了摘要，一旦点开全部，则公式就不再被正确显示，而是显示的源码。所以我设置为 true 后，则所有页面匀加载mathjax ，公式可以正常显示。 同时，按官网介绍，开启数学标签，要设置 tags: none 为 tags: ams ，则到此已经正确设置完毕。

## 参考文档

在百度时会有很多文章介绍hexo设置公式，但是经测试没有成功，为了不过多的折腾，我直接按照next官网来设置了我的博客，但是参考文章依然列出如下：

1. 首先附上官方网站
[Math Equations](https://theme-next.js.org/docs/third-party-services/math-equations)
2. 其次是我参考的文章
[在HEXO主题中添加数学公式支持](https://blog.csdn.net/weixin_43014927/article/details/99619627)
