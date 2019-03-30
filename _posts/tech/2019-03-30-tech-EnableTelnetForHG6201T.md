---
layout: post
title: EnableTelnetForHG6201T
category: 科技
tags: [HG6201T,Telnet]
keywords: HG6201T,Telnet
description: 描述
---


## 0x0001 EnableTelnetAccessForHG6201T_v0.1
将 192.168.1.1 替换成你的光猫的 IP 地址
开启 HG6201T 的 Telnet 访问
或者在浏览器中访问下面的地址

```
TelnetHG6201TDefaultUser: root
TelnetHG6201TDefaultPasswd: abcd
```

## 0x0002 Linux shell

```
curl "http://192.168.1.1:8080/cgi-bin/telnetenable.cgi?telnetenable=1"
```

## 0x0003 Windows bat
```
 start explorer "http://192.168.1.1:8080/cgi-bin/telnetenable.cgi?telnetenable=1"
```
