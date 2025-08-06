
---
layout: post
title:  "Instalar PiRogue en pine rock64"
date:   2025-07-21 12:32:00
categories: pirogue forensic rock64
---

Dispongo de una Single Board Computer PINE rock64 [https://pine64.org/devices/rock64/](https://pine64.org/devices/rock64/) en la cual queria instalar la suite PiRogue [https://pts-project.org/](https://pts-project.org/) para lo cual primero necesito instalarle Debian.

De esta dirección se pueden ver las diferentes versiones de sistemas operativos libres que se puede instalar en esa PINE Rock64:
[https://armbian.tnahosting.net/archive/rock64/archive/](https://armbian.tnahosting.net/archive/rock64/archive/)
en mi caso opto por instalar la versión basada en Debian Bookworm (12)

[https://armbian.tnahosting.net/archive/rock64/archive/](https://armbian.tnahosting.net/archive/rock64/archive/)

una vez instalado se verá asi:

    _             _    _           
   /_\  _ _ _ __ | |__(_)__ _ _ _  
  / _ \| '_| '  \| '_ \ / _` | ' \ 
 /_/ \_\_| |_|_|_|_.__/_\__,_|_||_|
                                   
 v25.5.1 for Rock 64 running Armbian Linux 6.12.38-current-rockchip64

 Packages:     Debian stable (bookworm)
 IPv4:         (LAN) 192.168.1.79, 10.8.0.1 (WAN) 189.x.x.x
 IPv6:         (WAN) xxx.xxxx.xxxxx.xxxxxx

pero est SBC no tiene tarjeta WiFi integrada por lo que use la siguiente:

root@rock64:/home/cacu# lsusb
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

que ya habia probado exitosamente en otras distribuciones Linux
