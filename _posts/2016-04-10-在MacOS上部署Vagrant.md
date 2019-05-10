---
layout:     post
title:      在MaxOS上部署Vagrant
subtitle:   在MaxOS上部署Vagrant
date:       2016-04-10
author:     XingKaiXin
catalog: true
tags:
    - MacOS
    - Vagrant
    - 开发环境
---

### 安装
**安装VirtualBox**
下载地址：[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

**安装Vagrant**
下载地址：[http://downloads.vagrantup.com/](http://downloads.vagrantup.com/)

**下载官方封装好的系统镜像**
Ubuntu 14.04 (based on amd64 server iso file [https://github.com/kraksoft/vagrant-box-ubuntu/releases/download/14.04/ubuntu-14.04-amd64.box](https://github.com/kraksoft/vagrant-box-ubuntu/releases/download/14.04/ubuntu-14.04-amd64.box)


如果你想要使用别的系统，可以从这里下载：[http://www.vagrantbox.es/](http://www.vagrantbox.es/)

## 配置
1. 添加镜像到Vagrant
前面下载的系统镜像，放到 `/box/ubuntu-14.04-amd64.box`

    vagrant box add pinpin-master ~/box/ubuntu-14.04-amd64.box

![](https://raw.githubusercontent.com/xingkaixin/blog-img/master/img/DraggedImage.cc9ca882dc964fe88e0d074573149901.png)

2. 初始化开发环境
创建一个开发目录(`~/workspace/pinpin`)，也可以使用已有的目录，切换到这个目录，使用前面创建的镜像初始化。

    cd ~/workspace/pinpin
    vagrant init pinpin-master
    vagrant up
    vagrant ssh

![](https://raw.githubusercontent.com/xingkaixin/blog-img/master/img/DraggedImage.6edc5a8d154e4352a722d1d46ccea4e3.png)


安装pip
`sudo apt-get install python-pip python-dev build-essential `
`sudo pip install --upgrade pip`
