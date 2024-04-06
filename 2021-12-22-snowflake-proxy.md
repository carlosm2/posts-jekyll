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
Actualizado: 2024-04-01

Hace algunos meses levanté un *standalone proxy snowflake*

[https://snowflake.torproject.org/](https://snowflake.torproject.org/)

en una Raspberry-pi 3 B+ 

[https://datasheets.raspberrypi.com/rpi3/raspberry-pi-3-b-plus-product-brief.pdf](https://datasheets.raspberrypi.com/rpi3/raspberry-pi-3-b-plus-product-brief.pdf)

usando esta documentación:

[https://community.torproject.org/relay/setup/snowflake/standalone/source/](https://community.torproject.org/relay/setup/snowflake/standalone/source/)

Que básicamente cuando ya tienes tu sistema operativo funcional, (desde hace mucho uso sistemas Debian o basados en Debian), debes de seguir con los siguientes pasos:

## Pasos para Instalación snowflake
 
### instalar golang 

Buscamos la versi\u00f3n para **LinuxARM64**
 
[https://go.dev/dl/](https://go.dev/dl/)

{% highlight ruby %}

$ wget https://go.dev/dl/go1.22.1.linux-arm64.tar.gz

y luego lo extraemos en /usr/local:

$ sudo tar -xzvf go1.22.1.linux-arm64.tar.gz -C /usr/local

establecemos la variable PATH

$ echo export PATH=$HOME/go/bin:/usr/local/go/bin:$PATH >> ~/.profile

y guardamos los cambios con:

$ source ~/.profile

y verificamos la versi\u00f3n:

$ cacu@minipi:~$ go version
$ go version go1.22.1 linux/arm64
 
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
 
Si deseas guardar la salida del proxy en un archivo de registro, por ejemplo, para ver su uso del proxy, puede usar:

{% highlight ruby %}
$ nohup ./proxy >snowflake.log 2>&1 &

### Agregarlo al cron
crontab -e

@reboot nohup /home/cacu/snowflake/proxy/proxy > /home/cacu/snowflake/proxy/snowflake.log 2>&1 &
{% endhighlight %}

❄
