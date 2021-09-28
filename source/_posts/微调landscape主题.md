---
title: 微调landscape主题
date: 2021-05-20 11:24:16
tags: Hexo
top : 5
---

## 微调原因

在使用Hexo完成我的首部博客后，在官网看了若干主题，但是感觉默认的主题非常的简洁明了符合我的性格。但是由于图片中间的亮光，使得白色副标题显示不清析。同时，既然对landscape做出了微调，那他就不是原来的主题了，同时随着使用，以后我也希望能够逐步完美我的博客，更改一些像分享之类的链接。所以专门开了一个主题仓库，用来做为主题维护之用。

<!--more-->

## 具体修改

### 下载landscape主题

    $git clone https://github.com/hexojs/hexo-theme-landscape ~/文档/hexo/theme/landscape

### 按步骤修改模板

1. 模板的修改，比如博客最下面的版权信息等,都是一些ejs文件，使用vim直接修改就行。本次修改的是footer.ejs文件。即

    ```
    位置:~/文档/hexo/theme/landscape/layout/_partial/footer.ejs

    <footer id="footer">
      <% if (theme.sidebar === 'bottom'){ %>
        <%- partial('_partial/sidebar') %>
      <% } %>
      <div class="outer">
        <div id="footer-info" class="inner">
 	 <% if (theme.copyright){ %>
 	   <%- render(theme.copyright, 'pug'); %>
 	 <% } %>
 	 &copy; <%= date(new Date(), 'YYYY') %> <%= config.author || config.title %><br>
 	 <%= __('powered_by') %> <a href="https://github.com/fengzhenhua-vip/hexo-theme-landscape/" target="_blank">Zhenhua Feng</a>
        </div>
      </div>
    </footer>
    ```
2. 标题的修改,主要是修改了标题到顶端的比例由50% 到30%，这样子主标题和副标题都在黑色背景下，容易看清楚。

    ```
    位置：~/文档/hexo/theme/landscape/source/_partical/header.styl

    #header-title
    text-align: center
    height: logo-size
    position: absolute
    top: 30%
    left: 0
    margin-top: logo-size * -0.5
    ```
3. 修改副标题字号大小，由18px调整到20px,这样子将邮箱写到副标题下，更易识别。

    ```
    // Header
    logo-size = 40px
    subtitle-size = 20px
    banner-height = 300px
    banner-url = hexo-config("banner")
    ```
4. 一些分享链接及图片的修改，暂时不修改，记录下位置

    ```
    ~/文档/hexo/theme/landscape/source/js/script.js
    ~/文档/hexo/theme/landscape/source/js/css/images
    ```
