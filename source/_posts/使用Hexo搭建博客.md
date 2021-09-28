---
title: 使用Hexo搭建博客
date: 2021-05-18 15:11:46
tags: Hexo
top: 2 
---

## 原理综述

博客，我们也可以理解为一个网站。网站是用浏览器来浏览的，所以这个网站就相当于是由许多文件构成，这些文件是用不同的语言写成，最终以html的方式被浏览器解读。然而大多数的人，不是网站的设计人员，所以这许多繁锁的文件可以借助一些工具来实现，比如说本文要讲的工具--- hexo 。

<!--more-->

当我们使用工具建立一个基本的博客模板后，之后的工作便是设置一些主题及撰写博文。这个可以使用markdown 来写，它的语法非常简洁，由于本人具备LaTeX 的使用经历，所以在vim 下使用markdown 语法写markdown 文件，感觉很顺手。但是这个markdown 文件 file.md 是不能直接被浏览器展示给读者来看的，所以需要借助于hexo 作用来转换一下，就可以了。所以从这个意义上讲hexo又肩负了一个翻译的功能。

当完成上面的模板及文章写作后，我们在本地开启服务(hexo s) 后，会产生一个本地网址(文章中会具体说明），然后在浏览器中输入这个网址就可以看到博客了。但是注意，这个博客现在是在本机上，之所以能看到是因为本机专门为其开启了网站服务。然而我们的电脑又不能天天开机，同时我们写的文章是想别人能够通过网站来浏览的，所以我们需要找一台能永远开机的机器，这就是网络上的一些服务器。这些服务器，实际也是“一台电脑”，我们将刚才生成的博客的全部文件，上传到这个电脑上的指定目录，此电脑会送给我们一个域名，这样我们就可以通过域名来浏览我们设置的博客了。

当我们又写了一篇博文时，我们还可以通过上述步骤将文件上传到服务器上。但是写的文章越来越多，目录越来越复杂，这样子我的就不能沉浸在写作的愉悦环境中了，所以这时hexo又扮演了另一个角色---辅助上传博文。当我们用hexo n 追加一篇博文后，然后再用设置好的hexo 上传，它很聪明，只上传改动过的文件，这就大大节省了资源，节省了时间。但我们在上传文件时，服务器会问你，向哪个账号传文件？你的密码是多少？这是很合理的，因为所有人都向我的目录乱传文件，显然我是不同意的。

但是，我们写博文是经常性的操作，每次都输入一遍账号和密码，实在是麻烦。没问题啊，我们还有一个方法，就是借助一个工具ssh 对我们的账号生成密钥，然后在我们的服务器上设置启用密钥功能，重新告诉hexo ,上传文件时使用ssh 密钥验证就可以了。这样子，我们再上传文章时，我们系统的密钥和服务器中我们保存的密钥就会自动比对，比对成功则我们的博文就能自动上传到服务器了。

上面，我通俗的讲解了使用服务器搭建自己博客的原理，下面按照我列出的步骤逐步操作，你也可以搭建自己的博客了。但是请注意，一定要遵守相关法律规定，不要发违法的信息。我的操作系统是manjaro , 如果你使用的windows 请百度相关文章即可，设置方式类似，我不多说了,祝你成功！

## 软件安装

1. 使用Hexo搭建博客，需要安装三个软件。依次为：
````
    #pacman -S nodejs  npm  git 
````
2. 安装Hexo博客软件，需借助 npm 包管理器来安装，由于国外安装源很慢，所认利用 npm 安装cnpm 。即
````
    #npm install -g cnpm --registry=https://registry.npm.taobao.org
````
3. 看一下  cnpm 的版本：
````
    #cnpm -v
````
4. 安装Hexo软件：
````
    #cnpm install -g hexo-cli
````
5. 安装完成后可以验证一下：
````
    #hexo -v
````

## 使用Hexo搭建博客

1. 新建一个文件夹，可以设置在自己想要的任何位置。但是要注意，由于博客需要经常打理，所以一旦确定位置请不要随意变更，这方便日后的使用。比如我在家目录下直接设置了一个准备存放博客的目录Hexo
````
    $ mkdir ~/Hexo
    $ cd ~/Hexo
    $ hexo init
````
2. 上述第三条命令，初始化设置一个默认的博客，包含了各种组件，但是作为一个使用者来讲我不需要知道细节，只管用就是了。这条命令会自己到 github 克隆，同时克隆一个 Landscape  主题，我自己感觉默认主题还是挺漂亮的，所以直接采用它了。现在一个初始的博客就完成了，启动博客
````
    $ hexo s
````
3. 在浏览器地址栏输入上述命令生成的本地地址 localhost:4000 就可以看到默认的博客了。

## 撰写博客

1. 新建博文模板,如下
```
    $ hexo n "博客声明"
```
2. 上述命令会新建一个markdown 文件，位于目录
```
    ~/Hexo/source/_posts/
```
3. 使用vim 打开文件，编辑博客内容
```
    $vim ~/Hexo/source/_posts/博客声明.md
```
4. 使用markdown 语法编辑好就可以了。然后使用以下命令构建博客
````
    $ hexo clean
    $ hexo g
    $ hexo s
````
5. 此时刷新一下刚才本地打开的 localhost:4000 就可以看到效果了。

## 托管到 Github 上公开使用

写好的博客，只有放在网站上生成对应的网址才能被其他人阅读到。免费的 Github 就是一个不错的选择，除了在国内访问慢了一点。这里需要几个步骤：

### 使用https方式登录github

1. 登录自己的Github
2. 新建一个仓库，仓库名要与登录名一致，才可以使用简短的域名 https://youname..github.io 登录博客。
3. 使用 vim 打开配置文件 ~/Hexo/\_config.yml ,在文件的最底部修改成这样子
```
    deploy:
    type: git
    repository: https:github.com/fengzhenhua-vip/fengzhenhua-vip.github.io.git
    branch: master
```
注意：在上述设置中，冒号后面有一个英文空格。我的vim可以自动检测语法，这点让我感到非常高兴。修改完成后保存退出即可。
4.部署到远端：
```
    $npm install hexo-deployer-git --save
    $hexo d
```
上面的这种方式是使用https方式登录的，执行上述命令后需要输入自己的账号和密码才能上传到对应的仓库中。

### 使用ssh方式登录github

https协议方式，每次 pull 、push 都要输入密码，这种方式对于经常写博文来说非常不方便，所以我设置了第二种方式---ssh 密钥对认证，可实现免密且更加安全。

1. 查看Git 环境配置
```
    $ git config --list
```
如果没有配置user.name 和 user.email 则需要先配置一下
```
    $ git config --global user.name "fengzhenhua-vip"
    $ git config --global user.email "fengzhenhua@sina.cn"
```
2. 查看SSH Key
如果没有设置过，则系统内没有 ～/.ssh 文件夹，这时需要先建立一下，即
```
    $ mkdir ~/.ssh
```
如果有设置过，则执行命令
```
    $ ls -l ~/.ssh
    id_rsa  id_rsa.pub known_hosts
```
此时存在三个文件，其中第二个就是公共密钥。
3. 生成密钥
```
    $ssh-keygen -t rsa -C "fengzhenhua@sina.cn"  #没有的话用此命令生成公钥和私钥
    $cat ~/.ssh/id_rsa.pub  #查看公钥并复制备用
```
4. 复制密钥到github
在自己申请的github网站上，依次点击
````
    setting->SSH and GPG keys ->New SSH key
````
取个名字，粘贴密钥即可。注意，不取名字，github会自动设置一个名字给你的，所以不取名也可以。
5. 验证是否配置成功
```
    $ssh -T git@github.com  
    Hi fengzhenhua-vip! You've successfully authenticated, but GitHub does not provide shell access.
```
显然，配置成功了。
6. 修改Hexo的配置文件 ～/Hexo/\_config.yml 
我的做法是将原来设置的https  方式直接注释掉，然后在下面重新写一下ssh 格式
```
    deploy:
    type: git
    repo: git@github.com:fengzhenhua-vip/fengzhenhua-vip.git
    branch:master
```
这样设置好后，再通过 hexo d 提交博客代码时就不用输入密码了。
7. Hexo默认按照文件的创建顺序排列文章，然而我需要重要的文章设置顶置。在2020年5月后，Hexo 默认支持了这个功能，即使用top,但是注意文章前的设置顺序是不能乱放的，要实现这个功能必须如下安排
```
    title: 使用Hexo搭建博客
    date: 2021-05-18 15:11:46
    tags: 
    top: 2 
```

## 问题汇总

### 升级Manjaro 后使用Hexo编译出错

在2021年6月30日晚我升级了`Manjaro`系统，然后使用`Hexo`生成博客时，出现错误如下


```
node: error while loading shared libraries: libcares.so.2: cannot open shared object file: No such file or directory
```

由于`Hexo`基于`Nodejs`,所以分析后，我重新安装了一遍`nodejs` 和 `pandoc` ,再次生成博客问题解决。即

```
#  pacman -S nodejs  pandoc
```
