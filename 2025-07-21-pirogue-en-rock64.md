---
layout: post
title:  "Instalar PiRogue en una PINE Rock64"
date:   2025-07-21 12:32:00
categories: pirogue forensic rock64 debian
---
# Instalar PiRogue en una PINE Rock64

          ▒▒▒              
       ▒  ▒▒▒  ▒           
      ▒▒  ▒▒▒  ▒▒          
      ▒▒▒▒▒▒▒▒▒▒▒          
   ▓▓▓▓  ▒▒▒▒▒  ▓▓▓▓       
   ▓▓▓▓▓▓  ▓  ▓▓▓▓▓▓       
   ▓  ░▓▓▓▓▓▓▓▓▓░  ▓       
  ██░  ▓▓▓▓▓▓▓▓▓  ░██      
   ██████  ░  ██████       
    ███  █████  ███        
      ███████████          
          ▓█▓              
           █          

El proyecto PiRogue Tool Suite [https://pts-project.org/](https://pts-project.org/) - Open-Source Platform for Mobile Device Forensics and Digital Investigations (Plataforma de código abierto para análisis forense de dispositivos móviles e investigaciones digitales) pone a nuestra disposición algunas herramientas / software para el análisis forense, en mi caso desde hace algunos años necesitaba de algo asi, por lo que me dispuse a instalar una Pi-Rogue.

En la documentación oficial se mencionan las Raspberry Pi como una opción para la instalación. Sin embargo, yo solo cuento con algunas Raspberry Pi 3B+, que tienen apenas 1 GB de memoria RAM, lo cual resulta insuficiente para ejecutar Suricata. Por esta razón, opté por realizar la instalación en una Single Board Computer (SBC) PINE Rock64 (https://pine64.org/devices/rock64/). Antes de instalar Suricata, primero debía instalar Debian 12, que es mi sistema operativo favorito.

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

Sin embargo, esta SBC no cuenta con una tarjeta WiFi integrada, la cual es necesaria para funcionar en modo punto de acceso (AP) con PiRogue. Por ello, utilicé un adaptador WiFi USB externo:

{% highlight python %}
cacu@rock64:/home/cacu# lsusb
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
{% endhighlight %}

Ya había probado exitosamente esta antena USB externa en otras distribuciones Linux, sin necesidad de instalar controladores adicionales o especiales. Esto permite utilizarla para instalar Pi-Rogue en modo Access Point, una función que se adapta perfectamente a mis necesidades: el análisis de posibles amenazas de malware y conexiones maliciosas en un dispositivo.

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
