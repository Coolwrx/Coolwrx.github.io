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

##为什么要刷 Padavan 固件？
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

![小米路由器获取 SSH](/media/img/小米路由器获取 SSH.PNG)

记下 root 密码，备用