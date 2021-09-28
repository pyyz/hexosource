---
title: Hexo添加宠物
date: 2021-05-30 20:33:20
tags: Hexo
---
# 简介

在解决写作问题的过程中，发现好多网友的网页上有一只漂亮的小猫在角落里，甚是可爱，于是先写一篇文章，为我的博客也添加一只宠物。

<!--more-->

# 安装宠物插件

```
$cnpm i hexo-helper-live2d --save
```

下载完插件后，使用`hexo s` 启动服务器发现右下角已经有了默认的 `live2d` 模型了。同时我们也可以安装自定义的宠物，可以参考[live2d官网](https://github.com/xiazeyu/live2d-widget-models)。由于我的博客以白色为主色调，所以我选择了一只黑猫作为宠物，在博客右下角守护我的博客。目前支持的宠物列表，如下

```
    live2d-widget-model-chitose
    live2d-widget-model-epsilon2_1
    live2d-widget-model-gf
    live2d-widget-model-haru/01 (use npm install --save live2d-widget-model-haru)
    live2d-widget-model-haru/02 (use npm install --save live2d-widget-model-haru)
    live2d-widget-model-haruto
    live2d-widget-model-hibiki
    live2d-widget-model-hijiki
    live2d-widget-model-izumi
    live2d-widget-model-koharu
    live2d-widget-model-miku
    live2d-widget-model-ni-j
    live2d-widget-model-nico
    live2d-widget-model-nietzsche
    live2d-widget-model-nipsilon
    live2d-widget-model-nito
    live2d-widget-model-shizuku
    live2d-widget-model-tororo
    live2d-widget-model-tsumiki
    live2d-widget-model-unitychan
    live2d-widget-model-wanko
    live2d-widget-model-z16
```

安装黑猫模型

```
$cnpm i live2d-widget-model-hijiki --save
```

# 配置宠物

编辑配置文件`~/文档/hexo/_config.yml`,在最下方添加如下配置信息启用宠物

```
# live2d配置宠物
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  model:
#    use: live2d-widget-model-tororo
    use: live2d-widget-model-hijiki
  display:
    position: right
    width: 240
    height: 480
  mobile:
    show: false
  react:
    opacityDefault: 1
    opacityOnHover: 1
```



