---
title: Ventoy制作多系统启动盘
date: 2021-07-10 23:17:57
tags: 电脑技术
top: 1
---

# 为何选择Ventoy ?

目前市面上有很多制作系统启动盘的工具，但是在工作中我们发现多数的系统启动盘制作工具所生成的启动盘会向新安装的系统中添加多余的软件，这点是我们非常不希望的。同时，一般而言这些系统启动盘制作工具只能支持windows,而对于Linux系统，则使用dd命令来记录启动盘。然而今天我们介绍一款能够同时支持主流Linux发行版和Windows的工具`Ventoy`。更多介绍请移步[Ventoy官网](https://www.ventoy.net/cn/index.html)

<!--more-->

# Ventoy使用方法

1. 在Ventoy官网下载此软件。Linux系统使用tar.gz格式。下载地址：
[https://www.ventoy.net/cn/download.html](https://www.ventoy.net/cn/download.html)

2. 下载后，解压，切换到该目录下，在终端中使用管理员权限启动Ventoy ,即

```
 # ./VentoyWeb.sh
```

3. 根据终端提示，在浏览器中打开Ventoy的前端界面。只要插上U盘，Ventoy能自动识别。识别后，点击安装按钮，即可把Ventoy安装到U盘上。注意，安装前会有警告：`最好使用空白、格式化的U盘，以免安装失败。`等几十秒后，Ventoy就安装好了。

4. 把操作系统的ISO镜像复制到U盘的数据分区里，这里的镜像支持Linux、Windows、WinPE。复制完毕，使用这个U盘启动电脑，则可以选择对应镜像就可以了。我本人经过测试，安装Windows10和 manjor Linux 均成功。

5. Ventoy使用说明官方版：[Ventoy使用说明](https://www.ventoy.net/cn/doc_start.html)


