---
title: window10LTSC版打开图片查看器
date: 2021-09-18 17:38:11
top: 28
tags:
---

本人更愿意在Linux下办公，无奈很办公文件需要与同事兼容，所以需要装一台windows电脑，经过多方对比发现windows10 LTSC版简洁稳定，可以很好的用于办公环境。但是安装此版本的系统后发现系统自带的看图软件不见了，不知道微软是基于什么考虑的在此版中没有看图软件。但是经过百度之后发现，其实lstc版也是有自带看图软件，只不过需要通过注册表来打开而己。
<!--more-->
下面提供启用看图软件的步骤：

1. 打开注册表编辑器(Win+R,Regedit)，定位至(建议修改前备份注册表)
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Photo Viewer\Capabilities\FileAssociations
```

2. 在右侧窗口中点击右键，选择“新建 – 字符串值”，然后把新建的字符串值重命名为 .jpg ，数值数据设置为 PhotoViewer.FileAssoc.Tiff；然后按同样的方法新建名为 .jpeg .png .gif .bmp .pcx .tiff .ico 等常用图片格式的字符串值，数值数据均设置为 PhotoViewer.FileAssoc.Tiff。

3. 关闭注册表编辑器，然后再在图片上点击右键，“打开方式”菜单中就会显示“Windows照片查看器”了。

