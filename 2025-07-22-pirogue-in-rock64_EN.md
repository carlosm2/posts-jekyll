---
layout: post
title:  "Install PiRogue on a pine rock64 (EN)"
date:   2025-07-22 12:32:00
categories: pirogue forensic rock64 debian
---

The project PiRogue Tool Suite [https://pts-project.org/](https://pts-project.org/) - Open-Source Platform for Mobile Device Forensics and Digital Investigations provides us with some tools/software for forensic analysis. In my case, I needed something like this for a few years, so I decided to install a Pi-Rogue.

The official documentation mentions Raspberry Pis as a supported option for installation. However, I only have a few Raspberry Pi 3B+ boards, which come with just 1 GB of RAM—insufficient to run Suricata effectively. For that reason, I decided to install it on a Single Board Computer (SBC), the PINE Rock64 (https://pine64.org/devices/rock64/). Before installing Suricata, I first needed to set up Debian 12, which is my favorite operating system.

De esta dirección web se pueden descargar las diferentes versiones de Armbian que se pueden instalar en esa PINE Rock64:
[https://armbian.tnahosting.net/archive/rock64/archive/](https://armbian.tnahosting.net/archive/rock64/archive/) En mi caso elijo instalar la versión basada en Debian Bookworm (12) porque en la Documentación de PTS Project esta documentado que se puede instalar en sistemas Debian 12:
[https://pts-project.org/docs/recipes/turn-a-regular-pc-into-a-pirogue/](https://pts-project.org/docs/recipes/turn-a-regular-pc-into-a-pirogue/)

Once Armbian 12 is installed it will look like this:

{% highlight python %}
    _             _    _           
   /_\  _ _ _ __ | |__(_)__ _ _ _  
  / _ \| '_| '  \| '_ \ / _` | ' \ 
 /_/ \_\_| |_|_|_|_.__/_\__,_|_||_|
                                   
 v25.5.1 for Rock 64 running Armbian Linux 6.12.38-current-rockchip64

 Packages:     Debian stable (bookworm)
 IPv4:         (LAN) 192.168.1.x, 10.8.0.1 (WAN) 189.x.x.x
 IPv6:         (WAN) xxx.xxxx.xxxxx.xxxxxx
 
{% endhighlight %}

However, this SBC does not have a built-in WiFi card, which is required to operate in AP mode with PiRogue. Therefore, I used an external USB WiFi adapter:

{% highlight python %}
cacu@rock64:/home/cacu# lsusb
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
{% endhighlight %}

Esta antena externa USB ya la habia probado exitosamente en otras distribuciones Linux, que no necesita controladores externos o especiales para funcionar, lo que permite poder instalar Pi-Rogue en modo Access Point que es la función que mas se adapta a mis necesidades; que es el analisis de posible Malware y conexiones maliciosas en un dispositivo.

Para instalar PiRogue en un sistema base Debian primero se actualiza el sistema:

{% highlight python %}
sudo apt update
sudo apt upgrade
{% endhighlight %}

despues se agregan los siguientes repositorios:

{% highlight python %}
sudo wget -O /etc/apt/sources.list.d/pirogue.list https://pts-project.org/debian-12/pirogue.list
sudo wget -O /etc/apt/trusted.gpg.d/pirogue.gpg   https://pts-project.org/debian-12/pirogue.gpg
sudo apt update
sudo apt install pirogue-base
{% endhighlight %}

Una vez instalado podemos revisar si quedó bien instalado, el tipo de configuración y las contraseñas de acceso al dashboard:

{% highlight python %}
pirogue-admin --configuration-tree
pirogue-admin --current-config
{% endhighlight %}

para revisar las conexiones existentes ejecutamos este comando:

{% highlight python %}
root@rock64:/home/cacu# nmcli connection show

NAME                      UUID                    TYPE      DEVICE          
Wired connection 1        0d5e9649-81ce-masdatos  ethernet  end0            
lo                        36a9c025-f184-masdatos  loopback  lo              
pirogue-isolated-network  c171297d-8af1-masdatos  wifi      wlxa0f3c109b6cf 

{% endhighlight %}
