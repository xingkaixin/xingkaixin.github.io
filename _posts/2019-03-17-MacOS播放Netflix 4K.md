---
layout:     post
title:      MacOS播放Netflix 4K
subtitle:   MacOS播放Netflix 4K
date:       2019-03-17
author:     XingKaiXin
catalog: true
tags:
    - Netflix
---

按照Netflix的播放装置说明文档，MacOS上使用Chrome可以播放最高720p，Safari可以播放最高1080。Chrome可以通过扩展程序支援到1080p，但整个Macos都无法播放4K视频。

在Chrome和Safari上播放视频，查看视频编码（快捷键：Opt+Ctl+Shift+D）
![](https://raw.githubusercontent.com/xingkaixin/blog-img/master/img/CleanShot%202019-04-19%20at%2019.09.02%402x.32db57ef17254278bec06d852cf0c56b.png)

可以看到视频编码为AVC，那么应该就是H.264。

按照Netflix的说明，Windows上播放4K需要安装HEVC解码器，那么可以猜测Windows上的4K视频是基于H.265编码的，而明显MacOS是支援这种编码。

因此在Apple TV 4K上，我们是可以观看4K的Netflix视频的。

对于Youtube，因为使用VP9编码，因此使用Safari无法播放4K视频，而Chrome就支援，到了Apple TV 4K上，Youtube也一样无法播放4K视频。

iTunes上的影片，在MacOS上只能播放最高1080p，而同样的影片在Apple TV 4K上就可以播放最高4K。

一个猜测，为了保证ATV 4K用户的最高享受，因此Apple才不允许Netflix在MacOS上支援4K？
