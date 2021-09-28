---
title: 使用Hexo优雅的写作
date: 2021-05-30 21:07:00
tags: Hexo
---

# 简介

随着对`Hexo`的理解逐步深入，我逐步掌握了使用`Hexo`写作的一些技巧。本文就是介绍在写作过程中可能用到的方便工具，可以使文章更加清晰易懂。

<!--more-->

# 文本居中引用

## 源码

```
{% cq %}
思索，继续不断的思索，以待天曙，渐近及见光明。

——**牛顿**
{% endcq %}
```
其中 `cq` 是 `centerquote` 的缩写，在源码中使用全称也是可以的。

## 效果展示

{% cq %}
思索，继续不断的思索，以待天曙，渐近及见光明。

——**牛顿**
{% endcq %}

# 使用上标和下标

Markdown 可以和 HTML 的语法兼容，可以通过HTML的上标和下标标签来实现效果：

|标签|写法|效果|
|:----:|:----:|:----:|
|上标|2\<sup\>10\</sup\>| 2<sup>10</sup>|
|下标|H\<sub\>2\</sub\>O| H<sub>2</sub>O|

# 下划线
Markdown 可以和HTML的语法兼容，可以通过HTML的`\<u\>` 标签来实现效果：

|写法|效果|
|:----:|:----:|
|\<u\>下划线\</u\>|<u>下划线</u>|


`注意`：u指的是`underline`。尽量不要给文本加下划线，因为这会和超链接的表现形式混淆，会被误认为是超链接。

# 字体颜色

比如说我们要设置字体颜色为<label style="color:red">红色</label>，代码为

```
<label style="color:red">红色</label>
```

# 强调文字

对于强调的部分，我们有两种方法,代码展示如下

```
<code>测试</code>
```

对于行文中的`强调`，我们也可以用反引号标，得到相同的效果,这种方式更加方便。

# `Note`标签

通过 `note` 标签可以为段落添加背景色，语法为：

```
{% note class %}
文本内容 （支持行内标签）
{% endnote %}
```
支持的`class` 包括: default primary success info warning danger , 也可以不指定class ,则默认使用灰色。

{% note default %}
default
{% endnote %}

{% note primary %}
primary
{% endnote %}

{% note success %}
success
{% endnote %}

{% note info %}
info
{% endnote %}

{% note warning %}
warning
{% endnote %}

{% note danger %}
danger 
{% endnote %}

{% note %}
不指定`class`
{% endnote %}

# `label` 标签

`next` 主题默认配置的`label`标签不是很好看，我们后期可以修改这个默认配置。设置位置为: `~/文档/hexo/themes/next/source/css/_variables/base.styl` 

```
// Label colors
// --------------------------------------------------
$label = {
  default : lighten(spin($note-border.default, 0), 89% + $lbg),
  primary : lighten(spin($note-border.primary, 10), 87% + $lbg),
  info    : lighten(spin($note-border.info, -10), 86% + $lbg),
  success : lighten(spin($note-border.success, 10), 85% + $lbg),
  warning : lighten(spin($note-border.warning, 10), 83% + $lbg),
  danger  : lighten(spin($note-border.danger, -10), 87% + $lbg)
};
```

目前尚未获得最佳方案，暂不修改。展示如下

{% label default@测试 %}
{% label primary@测试 %}
{% label success@测试 %}
{% label info@测试 %}
{% label warning@测试 %}
{% label danger@测试 %}

# Tabs 标签
Tabs 标签多用于多个内容之间的切换，默认情况下只显示其中一个结果或不展开显示，使文章更有条理。 

##  配置文件 `~/文档/hexo/themes/netx/_config.yml`

```
tabs:
  enable: true
  transition:
    tabs: false
    labels: true
  border_radius: 0
```

## 语法

```
{% tabs Unique name, [index] %}
<!-- tab [Tab caption] [@icon] -->
Any content (support inline tags too).
<!-- endtab -->
{% endtabs %}

Unique name   : Unique name of tabs block tag without comma.
                Will be used in #id's as prefix for each tab with their index numbers.
                If there are whitespaces in name, for generate #id all whitespaces will replaced by dashes.
                Only for current url of post/page must be unique!
[index]       : Index number of active tab.
                If not specified, first tab (1) will be selected.
                If index is -1, no tab will be selected. It's will be something like spoiler.
                Optional parameter.
[Tab caption] : Caption of current tab.
                If not caption specified, unique name with tab index suffix will be used as caption of tab.
                If not caption specified, but specified icon, caption will empty.
                Optional parameter.
[@icon]       : FontAwesome icon name (without 'fa-' at the begining).
                Can be specified with or without space; e.g. 'Tab caption @icon' similar to 'Tab caption@icon'.
                Optional parameter.

```

## 实例展示

{% tabs First unique name %}
<!--tab Solution1 -->
**This is Tab 1.**
<!-- endtab -->

<!--tab Solution 2 -->
**This is Tab 2.**
<!-- endtab -->

<!--tab Solution 3 -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

# 流程图`mermaid`

## 启用流程图功能,配置位置`~/文档/hexo/themes/next/_config.yml`

```
  # Mermaid
  mermaid: true
```

## 具体代码

```
{% mermaid sequenceDiagram %}
Alice ->> Bob: Hello Bob ,how are you?
Bob -->> John:How about you John?
Bob--x Alice: I am good thanks!
Bob-x John: I am good thanks!
Note right of John: Bob thinks a long <br/>long time ,so long than the text does not fit on a row.
Bob -->>Alice:Checking with John...
Alice->>John: Yes... John,how are you?
{% endmermaid %}
```

## 效果展示

{% mermaid sequenceDiagram %}
Alice ->> Bob: Hello Bob ,how are you?
Bob -->> John:How about you John?
Bob--x Alice: I am good thanks!
Bob-x John: I am good thanks!
Note right of John: Bob thinks a long <br/>long time ,so long than the<br/> text does not fit on a row.
Bob -->>Alice:Checking with John...
Alice->>John: Yes... John,how are you?
{% endmermaid %}

