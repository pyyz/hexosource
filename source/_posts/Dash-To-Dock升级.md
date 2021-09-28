---
title: Dash-To-Dock升级
date: 2021-07-17 00:13:16
tags: 电脑技术
---

在2021年7月17日下午我升级了我的Manjaro系统，但是拓展Dash To Dock 一直不能正常升级，此次升级也是造成了问题。所以根据出问题的提示，我直接是删除了这个插件的文件

```
# rm /usr/share/gnome-shell/extensions/dash-to-dock\@micxgx.gmail.com/schemas/gschemas.compiled
# pacman -Syu
```
然后成功执行升级。下面给出具体解决方案:

<!--more-->

# Manjaro升级后Dash-To-Dock 失效和无法通过Gnome插件官网安装的解决方案

1. 按[插件dash-to-dock](https://extensions.gnome.org/extension/307/dash-to-dock/) 的（用户）提示，由于本机Gnome升级到了Gnome3 V40.2.0 所以直接clone到本地

```
$ git clone -b ewlsh/gnome-40 https://github.com/ewlsh/dash-to-dock.git 
$ cd ./dash-to-dock
```

2. 安装编译插件所需的软件及设置环境变量

```
# pacman -S sassc
# export SASS=sassc
```

3. 编译安装插件

```
# exit
$ cd ~/下载/dash-to-dock
$ make
$ make install
```

----

# 附上官方README.md文件


# Dash to Dock
![screenshot](https://github.com/micheleg/dash-to-dock/raw/master/media/screenshot.jpg)

## A dock for the GNOME Shell
This extension enhances the dash moving it out of the overview and transforming it in a dock for an easier launching of applications and a faster switching between windows and desktops without having to leave the desktop view.

[<img src="https://micheleg.github.io/dash-to-dock/media/get-it-on-ego.png" height="100">](https://extensions.gnome.org/extension/307/dash-to-dock)

For additional installation instructions and more information visit [https://micheleg.github.io/dash-to-dock/](https://micheleg.github.io/dash-to-dock/).

## Installation from source

The extension can be installed directly from source, either for the convenience of using git or to test the latest development version. Clone the desired branch with git

### Build Dependencies

To compile the stylesheet you'll need an implementation of SASS. Dash to Dock supports `dart-sass` (`sass`), `sassc`, and `ruby-sass`. Every distro should have at least one of these implementations, we recommend using `dart-sass` (`sass`) or `sassc` over `ruby-sass` as `ruby-sass` is deprecated.

By default, Dash to Dock will attempt to build with `dart-sass`. To change this behavior set the `SASS` environment variable to either `sassc` or `ruby`.

```bash
export SASS=sassc
# or...
export SASS=ruby
```

注：在Manjaro中支持`sassc`,安装源中找不到`dart-sass`,所以安装了前者。做了如下设置

```
# pacman -S sassc
# export SASS=sassc
```


### Building

Clone the repository or download the branch from github. A simple Makefile is included.

Next use `make` to install the extension into your home directory. A Shell reload is required `Alt+F2 r Enter` under Xorg or under Wayland you may have to logout and login. The extension has to be enabled  with *gnome-extensions-app* (GNOME Extensions) or with *dconf*.

```bash
git clone https://github.com/micheleg/dash-to-dock.git
make
make install
```
注： 只下载分支`` 即可，所以执行的命令是

```
$ git clone -b ewlsh/gnome-40 https://github.com/ewlsh/dash-to-dock.git 
$ make
$ make install
```


## Bug Reporting

Bugs should be reported to the Github bug tracker [https://github.com/micheleg/dash-to-dock/issues](https://github.com/micheleg/dash-to-dock/issues).

## License
Dash to Dock Gnome Shell extension is distributed under the terms of the GNU General Public License,
version 2 or later. See the COPYING file for details.






