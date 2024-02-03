---
layout: post
title:  "Proxy Snowflake Standalone installation"
date:   2021-12-24 12:31:00
categories: freesoftware tor snowflake proxy
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



A few months ago I built a *standalone proxy snowflake*

[https://snowflake.torproject.org/](https://snowflake.torproject.org/)

in a Raspberry-pi 3 B+ 

[https://datasheets.raspberrypi.com/rpi3/raspberry-pi-3-b-plus-product-brief.pdf](https://datasheets.raspberrypi.com/rpi3/raspberry-pi-3-b-plus-product-brief.pdf)

using this documentation:

[https://gitlab.torproject.org/tpo/anti-censorship/pluggable-transports/snowflake/-/wikis/home](https://gitlab.torproject.org/tpo/anti-censorship/pluggable-transports/snowflake/-/wikis/home)

Basically, when you already have your functional operating system (I have been using Debian or Debian-based systems for a long time), you must continue with the following steps:

## ❄ Snowflake Installation ❄
 
{% highlight c++ %}# instalar golang
 
 $ apt install golang
 
 # code clone
 
 $ git clone https://git.torproject.org/pluggable-transports/snowflake.git
 
 # levantar el snowflake proxy
 
 $ cd snowflake/proxy
 $ go build 
 
 # ejecutar el proxy
 
 $ cd snowflake/proxy
 $ nohup ./proxy & {% endhighlight %}
   
 y listo, despues puedes revisar ese archivo *nohup.out* para ver que esta sucediendo con el proxy.
 
❄
