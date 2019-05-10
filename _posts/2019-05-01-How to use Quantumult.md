---
layout:     post
title:      Quantumult的使用方法
subtitle:   基础和进阶使用技巧
date:       2019-05-01
author:     XingKaiXin
header-img: img/post-bg-coffee.jpeg
catalog: true
tags:
    - 科学上网
    - iOS
    - Quantumult
    - 教学
---

## 导入订阅节点
1. 打开Quantumult，点击『设置』-> 订阅』-> 点击右上角『+』号 -> 『服务器』。『名称』填写IPLC.CLOUD(你喜欢的名字就可以)，『链接』粘贴前面提到的订阅节点。『高级』建议保持默认。然后保存。


2. 保存后左滑这个项目，选择『更新』。


![](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556121892754_image.png)


到这里你完成了服务器的订阅，之后服务器有节点更新，也会提示，更新方法同步骤2。

## 导入分流规则

自带的分流规则过于简陋，并不能很好的满足我们科学上网的需求，因此我们需要导入分流规则，这样我们使用起来更舒服，同时也可以屏蔽一部分的广告。
**推荐规则**
[ConnersHua](https://github.com/ConnersHua/Profiles) 神机规则


    QuantumultFilter:
    https://raw.githubusercontent.com/ConnersHua/Profiles/master/Quantumult/Pro.conf
    QuantumultRejection:
    https://raw.githubusercontent.com/ConnersHua/Profiles/master/Quantumult/Rejection.conf

**添加分流规则**

1. 点击『设置』-> 『订阅』-> 点击右上角『+』号 ->『分流』。『名称』填写自定义，『链接』填写Filter规则的URL，『高级』中勾选个性化。然后保存。


![](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556121919531_image.png)

2. 左滑对应分流规则，选择『替换』。这里可以先不做任何调整，保存即可。


![](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556121925594_image.png)


**添加链接阻止规则**

1. 点击『设置』-> 『订阅』-> 点击右上角『+』号 ->『链接阻止』。『名称』填写自定义，『链接』填写Rejection规则的URL，『高级』中勾选包含主机名。然后保存。


![](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556121930269_image.png)

2. 左滑对应链接阻止规则，选择『替换』。
## 开始使用

退出设置菜单，点击Quantumult的图标，可进行节点切换，左下仪表可进行延迟测速，测速会有2个数字，第一个数字代表TCP握手时间，第二个数字代表整个HTTP返回的时间。
在注册右上角开关可以开启Quantumult的使用。地图也会显示你当前使用节点的主机地理位置。
首次使用会需要你允许VPN，点击允许按步骤操作即可。

## 进阶使用

如果你的使用场景中，你因为有购买Youtube Premium所以你需要使用美国节点来这个服务，你有看亚洲的HBO，因此你需要使用香港节点来看，你有看Netflix，并且觉得新加坡区的片子上新比较快，但有时候你又会使用香港节点来看，等等正对每一个应用的不同节点使用情况。你有香港非IPLC的节点，也有香港IPLC的节点，香港IPLC里可能还分了上海-香港有2个，深圳-香港有2个，你不想每次使用时还要先检查一遍节点连接速度。以上，如果你确实有类似的问题，那么请继续看下去，如觉得不需要这么麻烦，就不用看了
**构想**
按前面提到的使用场景，我们会有三类节点组:

1. 我们会需要一个香港节点组、新加坡节点组和美国节点组，使用时我们可以手工选择。
2. 每个节点组里，我们会有直连的当地主机节点组、上海-当地的节点组和深圳到当地的节点组。使用时我们可以手工选择。
3. 这三个节点组里的实际节点，我们希望可以自动选择延迟低的节点。

**策略组**
在『设置』 -> 『策略』 -> 右上角『+』号，我们可以添加

1. 『延迟策略』：根据节点延迟速度提供一个最快的节点
2. 『静态策略』：手工选择节点组

**添加第三类节点组**
这里我们使用『延迟策略』。

1. 名称为香港,『添加服务器』，勾选订阅节点中香港的直连节点
2. 名称为上海-香港，『添加服务器』，勾选订阅节点中上海-香港的IPLC节点
3. 名称为深圳-香港，『添加服务器』，勾选订阅节点中深圳-香港的IPLC节点

对于美国、新加坡步骤同上。
**添加第二类节点组**
这里我们使用『静态策略』
名称为香港国旗的图标，『添加策略或服务器』，把第三类节点组，『香港』、『上海-香港』和『深圳-香港』加入。
对于美国、新加坡步骤同上。
**添加第一类节点组**
这里我们使用『静态策略』
名称为飞机的图标，『添加策略或服务器』，把第二类节点组，『香港』、『美国』和『新加坡』加入。


![第三类](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556121939374_image.png)
![第二类](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556122089508_image.png)
![第一类](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556121964497_image.png)


**应用策略**
回到『设置』 -> 『订阅』,左滑分流规则，选择『替换』。

1. 下滑找到『Youtube 专用节点』，选择第二类的美国节点。
2. 下滑找到『HBO NOW & GO 专用节点』，选择第二类的香港节点
3. 下滑找到『Netflix 专用节点』，选择第一类的节点


![](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556121979263_image.png)
![](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556122074453_image.png)


保存，回到『主页』。点击圈的图标，PROXY的节点是针对网页、Twitter这些前面没有提到应用会使用的节点。向右滑动，你可以选择Netflix使用哪个地区的节点，在向右滑动，你可以分别选择各个地区的节点组使用独立主机、上海IPLC线路、深圳IPLC线路，而这些线路具体使用的节点则由他们的延迟测试决定。
到此即告完成，你可以按照这个思路，针对你自己的使用场景进行调整、优化。

**路由器科学上网环境下，手机连接WiFi时圈不关闭但停止分流工作**
这里没有直接的UI配置，我们进入『设置』- 『编辑配置文件』,找到「SUSPEND-SSID」配置项，在下方填写你的WiFi名称并保存。
这样当你连接WiFi时，圈会处于挂起状态，断开WiFi又会继续运行。

![](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556121987839_image.png)
![](https://paper-attachments.dropbox.com/s_E93F0703280D5428F0BA890689E6A3957FC5DA07F12D7478EBB948B8A711987B_1556121993476_image.png)


