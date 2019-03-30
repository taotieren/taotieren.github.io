---
layout: post
title: 标题
category: 科技
tags: [Debian9,ifenslave,bond]
keywords: Debian9,ifenslave,bond
description: 描述
---
@[TOC](Debian9 通过 ifenslave 配置多网卡 bond)

## 0x0001 安装 ifenslave

```
apt install ifenslave
```

## 0x0002 配置 bonding 模块

```
 vim /etc/modprobe.d/bonding.conf
 ```
 ```
 # bonding config
alias bond0 bonding
```
 ```
source /etc/modprobe.d/bonding.conf
```
## 0x0003 配置网卡信息
```
 systemctl stop networking.service 
```
```
 vim /etc/network/interfaces
```
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The boud0 network interface
auto bond0
iface bond0 inet static
address 192.168.1.120
mask 255.255.255.0
gateway 192.168.1.1
post-up ifenslave bond0 eno1 eno2 eno3 eno4
pre-down ifenslave -d bond0 enoe1 eno2 eno3 eno4
bond-mode balance-alb
bond-miimon 100
bond-slaves yes
dns-nameserver 1.1.1.1
```

```
 systemctl start networking.service 
```
## 0x0004 验证是否配置正确

```
ifconfig -a
```

```
bond0: flags=5187<UP,BROADCAST,RUNNING,MASTER,MULTICAST>  mtu 1500
        inet 192.168.1.120  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::ffff  prefixlen 64  scopeid 0x20<link>
        ether 00:11:22:33:44:55  txqueuelen 1000  (Ethernet)
        RX packets 25762  bytes 3490656 (3.3 MiB)
        RX errors 0  dropped 2  overruns 0  frame 0
        TX packets 3774  bytes 434182 (424.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eno1: flags=6211<UP,BROADCAST,RUNNING,SLAVE,MULTICAST>  mtu 1500
        ether 00:11:22:33:44:55  txqueuelen 1000  (Ethernet)
        RX packets 25762  bytes 3490656 (3.3 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3774  bytes 434182 (424.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  

eno2: flags=6147<UP,BROADCAST,SLAVE,MULTICAST>  mtu 1500
        ether 00:11:22:33:44:55  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  

eno3: flags=6147<UP,BROADCAST,SLAVE,MULTICAST>  mtu 1500
        ether 00:11:22:33:44:55  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  

eno4: flags=6147<UP,BROADCAST,SLAVE,MULTICAST>  mtu 1500
        ether 00:11:22:33:44:55  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 11352  bytes 30987198 (29.5 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11352  bytes 30987198 (29.5 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
