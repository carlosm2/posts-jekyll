---
layout: post
title:  "instalación de proxy snowflake"
date:   2021-12-24 12:32:00
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



Hace algunos meses levanté un *standalone proxy snowflake*

[https://snowflake.torproject.org/](https://snowflake.torproject.org/)

en una Raspberry-pi 3 B+ 

[https://datasheets.raspberrypi.com/rpi3/raspberry-pi-3-b-plus-product-brief.pdf](https://datasheets.raspberrypi.com/rpi3/raspberry-pi-3-b-plus-product-brief.pdf)

usando esta documentación:

[https://gitlab.torproject.org/tpo/anti-censorship/pluggable-transports/snowflake/-/wikis/home](https://gitlab.torproject.org/tpo/anti-censorship/pluggable-transports/snowflake/-/wikis/home)

Que básicamente cuando ya tienes tu sistema operativo funcional, (desde hace mucho uso sistemas Debian o basados en Debian), debes de seguir con los siguientes pasos:

## ❄ Instalación snowflake ❄
 
{% highlight c++ %}# instalar golang
 
 apt install golang
 
 # clonar codigo
 
 git clone https://git.torproject.org/pluggable-transports/snowflake.git
 
 # levantar el snowflake proxy
 
 cd snowflake/proxy
 go build 
 
 # ejecutar el proxy
 
 cd snowflake/proxy
 nohup ./proxy & {% endhighlight %}
   
 y listo, despues puedes revisar ese archivo *nohup.out* para ver que esta sucediendo con el proxy.
 
❄
