---
layout: post
title: 小米路由器 3G、mini 刷入 Padavan 固件
tags:
    - 教程
    - 路由器
---

Padavan 就是网传的老毛子固件，是一个优秀的路由器固件，支持采用 RT3883/MT7620/MT7621/MT7628 等系列 CPU 的路由器。  
本文使用的是集成了 ShadowSocks 的 Padavan 固件，开启 UDP 转发后可用于 Xbox 网络加速。  
请遵守当地法律法规，在使用 Xbox 加速服务时，自觉屏蔽 80、443 端口。  
（选购路由器时请注意其硬件配置是否可用于刷入 Padavan 固件）

点击[这里](#获取-ssh-权限)跳转至教程正文

## 相关链接
Breed Bootloader 下载
````
https://breed.hackpascal.net/
````
Rom 下载
````
http://opt.cn2qq.com/padavan/
````



## 为什么要刷 Padavan 固件？

折腾是一件很有意思的事情  
安卓版的 ShadowSocksR 太耗电了，无法后台常驻  
解决 Xbox 等主机的网络加速问题  
增强用户体验

## 什么是 Breed Bootloader ？
“Bootloader” 意为加载引导器，即为用于加载操作系统的程序。它是一大类此类功能 程序的统称。
````
http://www.right.com.cn/forum/thread-161906-1-1.html
````
类似于安卓手机关机状态下长按音量减和电源键可进到的，用于刷机、解BL锁和修复系统的 Bootloader 模式，同样基于 Linux 的路由器系统也拥有 Bootloader 模式。

Breed Bootloader 是一个第三方 Bootloader ，功能齐全，界面友好，非开源，若只在 Breed 中进行固件更新操作，则不会出现变砖的情况。有过刷机经验的读者应该了解，原厂自带的 Bootloader 通常只有简单功能且权限不足。所以在实际操作时， 一般会选择第三方 Bootloader。

## 获取 SSH 权限

- 将小米账号绑定至小米路由器  
这一步比较简单，下载小米路由器 Android 客户端并登录小米账号  
连接至小米路由器的无线网络，即可自动绑定（路由器需完成拨号设置并确保其能 够连接至互联网）
- 刷入最新开发版 Rom  
同上一步，下载最新的开发版 Rom，在路由器后台管理面板刷入
- 开启 SSH 工具
````
http://miwifi.com/miwifi_open.html
````
下滑此页面，找到“开启 SSH 工具”，并登录小米账号  
截官方教程

![小米路由器获取 SSH](/media/img/180907-1-小米路由器获取ssh.png)

记下 root 密码，备用

## 刷入 Breed Bootloader

*需要使用有线方式连接至路由器

### 下载 Breed Bootloader、Xshell、WinSCP

Breed Bootloader

<https://breed.hackpascal.net/>

Xshell

<https://www.netsarang.com/download/software.html>

WinSCP

<https://winscp.net/eng/download.php>


在下载页面中找到你的设备，下载至本地

![Breed Bootloader 下载](/media/img/180907-2-breed-bootloader下载.png)

Xshell 和 WinSCP 均为（教育版）免费软件，请自行尝试下载安装

### 连接至路由器
WinSCP 是一款开源的SFTP客户端（用来把文件传到路由器的闪存里）  
运行 WinSCP，添加路由器站点

![WinSCP新建站点](/media/img/180907-3-winscp-新建站点.png)

其中：

- 将文件协议更改为 SCP 协议
- 主机名即为网关地址，小米路由器默认为 192.168.31.1
- 用户名为 root，密码为先前记下的 SSH root 密码

单击“登录”，即可以图形界面方式登陆至路由器

### 刷写 Breed Bootloader
将之前下载的 Breed Bootloader 复制到路由器的 /tmp 目录下  
运行 Xshell，添加路由器会话

![Xshell新建会话](/media/img/180907-4-xshell-新建会话.png)

与 WinSCP 的操作相似，主机为 192.168.31.1，端口使用默认的 22 号端口  
单击“连接”后，将会弹出 SSH 安全警告，选择“接受并保存”

用户名为 root，密码为先前记录的 SSH root 密码  
如果一切顺利，你将会看到如下界面 ARE U OK ?

![小米路由器SSH界面.png](/media/img/180907-5-小米路由器ssh界面.png)

在命令行依次输入

````
cd /tmp
mtd -r write breed-***.bin Bootloader
````

请将 breed-***.bin 更换为你下载的 Breed Bootloader 文件名  
（或者，你可以使用“自动填充”，输入 mtd -r write breed 后按下 TAB 键

刷写完成后，路由器将会重新启动，此时将 PC 以有线方式连接至路由器，打开命 令提示符，运行 ping 192.168.1.1 -t （因为 Breed Bootloader 还没有启动， 所以 ping 的反馈将是“请求超时”）。按如下步骤操作
1. 断开路由器电源，用尖锐物按住 reset 键不松开，接通电源；
2. 保持按住 reset 键，直至路由器指示灯开始闪烁，即表明 Breed 启动成功， 此时命令提示符将提示小于 1ms 的延迟；
3. 关闭命令提示符，打开浏览器并访问 192.168.1.1，即可进入 Breed 控制台；

## 刷入 Padavan 固件
用 Web 方式进入 Breed 控制台（浏览器访问 http://192.168.1.1 ）后，依次单击：固件更新 / 常规固件 / 勾选固件复 选框 / 浏览…，上传之前下载好的 Padavan 固件包，开始刷写

成功后会自动重启，并默认开启无线连接，参数如下

> 网关： 192.168.123.1  
> 管理员账号、密码： admin / admin  
> Wifi SSID 名称： PDCN / PDCN-5G  
> 默认 Wifi 密码： 123456789  

用浏览器访问 192.168.123.1 或 my.router 即可进入 Padavan 后台管理面板  
大概长这个样子：

![Padavan面板.PNG](/media/img/180907-6-padavan-面板.png)

-----
转载请注明出处