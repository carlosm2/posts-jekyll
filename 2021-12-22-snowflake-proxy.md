---
layout: post
title:  "Instalación de proxy snowflake"
date:   2024-04-01 12:32:00
categories: softwarelibre tor snowflake proxy
---
## ❄ Proxy Snowflake ❄

, ,    ,      ,    ,     ,     ,   ,      ,     ,     ,      ,      ,
,       ,     ,    ,       ,   .____. ,   ,     ,      ,       ,      ,
 ,    ,   ,    ,     ,   ,   , |   :|         ,   , ,   ,   ,       ,
   ,        ,    ,     ,     __|====|__ ||||||  ,        ,      ,      ,
 ,   ,    ,   ,     ,    , *  / o  o \  ||||||,   ,  ,        ,    ,
,   ,   ,         ,   ,     * | -=   |  \====/ ,       ,   ,    ,     ,
   ,  ,    ,   ,           ,  ==\__//__. \\//    ,  ,        ,    ,
,   ,  ,    ,    ,    ,  ,   / \\==// \ \ ||  ,   ,      ,          ,
 ,  ,    ,    ,     ,      ,|    o ||  | \||   ,      ,     ,   ,     ,
,      ,    ,    ,      ,   |    o ""  |\_|B),    ,  ,    ,       ,
  ,  ,    ,   ,     ,      , \__  --__/   ||  ,        ,      ,     ,
,  ,   ,       ,     ,   ,  /          \  ||,   ,   ,      ,    ,    ,
 ,      ,   ,     ,        |            | ||      ,  ,   ,    ,   ,
,    ,    ,   ,  ,    ,   ,|            | || ,  ,  ,   ,   ,     ,  ,


Escrito:  2021-12-24
Actualizado: 2026-04-01

Hace algunos meses levanté un *standalone proxy snowflake*

[https://snowflake.torproject.org/](https://snowflake.torproject.org/)

en una Raspberry-pi 3 B+ 

[https://datasheets.raspberrypi.com/rpi3/raspberry-pi-3-b-plus-product-brief.pdf](https://datasheets.raspberrypi.com/rpi3/raspberry-pi-3-b-plus-product-brief.pdf)

usando esta documentación:

[https://community.torproject.org/relay/setup/snowflake/standalone/source/](https://community.torproject.org/relay/setup/snowflake/standalone/source/)

Que básicamente cuando ya tienes tu sistema operativo funcional, (desde hace mucho uso sistemas Debian o basados en Debian), debes de seguir con los siguientes pasos:

## Pasos para Instalación snowflake
 
### instalar golang 

Buscamos la versión para **LinuxARM64**
 
[https://go.dev/dl/](https://go.dev/dl/)

{% highlight ruby %}

$ wget https://go.dev/dl/go1.22.1.linux-arm64.tar.gz

y luego lo extraemos en /usr/local:

$ sudo tar -xzvf go1.22.1.linux-arm64.tar.gz -C /usr/local

establecemos la variable PATH

$ echo export PATH=$HOME/go/bin:/usr/local/go/bin:$PATH >> ~/.profile

y guardamos los cambios con:

$ source ~/.profile

y verificamos la versión:

$ cacu@minipi:~$ go version
$ go version go1.22.1 linux/arm64

### Crear usuario dedicado

Para mayor seguridad y control creamos un usuario dedicado

$ cacu@minipi:~adduser snowflake
info: Adding user `snowflake' ...
info: Selecting UID/GID from range 1000 to 59999 ...
info: Adding new group `snowflake' (1004) ...
info: Adding new user `snowflake' (1004) with group `snowflake (1004)' ...
info: Creating home directory `/home/snowflake' ...
info: Copying files from `/etc/skel' ...
New password: 
Retype new password: 
passwd: password updated successfully
Changing the user information for snowflake
Enter the new value, or press ENTER for the default
	Full Name []: snowflake
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] y
info: Adding new user `snowflake' to supplemental / extra groups `users' ...
info: Adding user `snowflake' to group `users' ...

### cambiamos al usuario recien creado

$ cacu@minipi:~$ su snowflake
Password:

$ snowflake@minipi:~$

### clonar codigo
 
$ git clone https://git.torproject.org/pluggable-transports/snowflake.git
 
### Compilar el snowflake proxy
 
$ cd snowflake/proxy
$ go build 
 
### ejecutar el proxy
 
$ cd snowflake/proxy
$ nohup ./proxy &

### Ver registros
{% endhighlight %}
 
Si deseas guardar la salida del proxy en un archivo de registro —por ejemplo, para monitorear su uso— puedes usar:

{% highlight ruby %}
$ nohup ./proxy >snowflake.log 2>&1 &

### Agregarlo al cron
crontab -e

@reboot nohup /home/cacu/snowflake/proxy/proxy > /home/cacu/snowflake/proxy/snowflake.log 2>&1 &
{% endhighlight %}

Video sobre Instalación: [https://fediverse.tv/w/qnVVHitSyrk5c6zDDtEDan](https://fediverse.tv/w/qnVVHitSyrk5c6zDDtEDan)

❄
