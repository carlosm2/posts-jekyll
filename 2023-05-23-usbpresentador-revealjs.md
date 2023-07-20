---
layout: post
title:  "habilitar presentador usb en revealjs"
date:   2023-05-25 12:32:00
categories: softwarelibre revealjs presentacion
---


              /'._     _,
              \   ;__.'  }
          (`-._;-" _.--.}'
          /_'    /`    _}
            `.   \_._.;
              '-.__ /
               _/  `\
               ^`   ^`
               
Desde hace varios años uso [https://revealjs.com/](https://revealjs.com/) para hacer mis presentaciones y talleres, de hecho hice un par de talleres en eventos universitarios y en el hackerspace donde habitaba, colaboraba.

En la busqueda por incorporar nuevas cosas a los talleres probé un presentador - apuntador USB
que en mi computadora Debian aparece asi:

{% highlight java %} Bus 001 Device 012: ID 3243:0131 NORWII Norwii Wireless Presenter {% endhighlight %}

Pero no funcionaba con revealjs por lo que busque en la documentación esta parte:

[https://revealjs.com/config/](https://revealjs.com/config/)

dentro de la inicialización:

{% highlight java %} Reveal.initialize({ {% endhighlight %}

si originalmente esta asi:

{% highlight java %} navigationMode: 'default', {% endhighlight %}
 
 cambiarlo o definirlo asi: 
 
{% highlight java %} navigationMode: 'linear', {% endhighlight %}
 
 guardan el cambio y con esto funciona bien :)
