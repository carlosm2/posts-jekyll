
---
layout: post
title:  "Instalar PiRogue en pine rock64"
date:   2025-07-21 12:32:00
categories: pirogue forensic rock64
---

El proyecto PiRogue Tool Suite [https://pts-project.org/](https://pts-project.org/) - Open-Source Platform for Mobile Device Forensics and Digital Investigations (Plataforma de código abierto para análisis forense de dispositivos móviles e investigaciones digitales) pone a nuestra disposición algunas herramientas / software para el análisis forense, en mi caso desde hace algunos años necesitaba de algo asi, por lo que me dispuse a instalar una Pi-Rogue.

En la documentación oficial mencionan Raspberry Pis para instalarla, yo solo tengo algunas Raspberry Pis 3B+, la cual solo tiene  1 GB RAM, insuficiente para ejecutar Suricata  por lo que opté por instalar en una Single Board Computer (SBC) PINE rock64 [https://pine64.org/devices/rock64/](https://pine64.org/devices/rock64/) en la cual primero tenia que instalarle Debian 12, mi sistema operativo de cabecera.

De esta dirección web se pueden descargar las diferentes versiones de Armbian que se pueden instalar en esa PINE Rock64:
[https://armbian.tnahosting.net/archive/rock64/archive/](https://armbian.tnahosting.net/archive/rock64/archive/) En mi caso elijo instalar la versión basada en Debian Bookworm (12) porque en la Documentación de PTS Project esta documentado que se puede instalar en sistemas Debian 12:
[https://pts-project.org/docs/recipes/turn-a-regular-pc-into-a-pirogue/](https://pts-project.org/docs/recipes/turn-a-regular-pc-into-a-pirogue/)

Una vez instalado Armbian 12 se verá asi:

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

pero esta SBC no tiene tarjeta WiFi integrada, la cual es necesaria para poder funcionar en modo AP con PiRogue, usé esta USB wifi externa:

{% highlight python %}
root@rock64:/home/cacu# lsusb
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
{% endhighlight %}

que ya habia probado exitosamente en otras distribuciones Linux, que no necesita controladores externos o especiales para funcionar, lo que permite poder instalar Pi-ROgue en modo Access Point que es la función que mas se adapta a mis necesidades.

Para instalar PiRogue en un sistema base Debian se agregan los repositorios y se ejecuta lo siguiente:

{% highlight python %}
sudo wget -O /etc/apt/sources.list.d/pirogue.list https://pts-project.org/debian-12/pirogue.list
sudo wget -O /etc/apt/trusted.gpg.d/pirogue.gpg   https://pts-project.org/debian-12/pirogue.gpg
sudo apt update
sudo apt install pirogue-base
{% endhighlight %}

---

para revisar las conexiones existentes ejecutamos este comando:

root@rock64:/home/cacu# nmcli connection show

NAME                      UUID                    TYPE      DEVICE          
Wired connection 1        0d5e9649-86ce-masdatos  ethernet  end0            
lo                        36a9c025-fc84-masdatos  loopback  lo              
pirogue-isolated-network  c171297d-8af1-masdatos  wifi      wlxa0f3c109b6cf 

y para verificar la configuración:

pirogue-admin --configuration-tree
pirogue-admin --current-config
