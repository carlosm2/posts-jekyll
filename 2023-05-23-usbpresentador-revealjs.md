---
layout: post
title:  "habilitar presentador inalambrico en revealjs"
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
               
Desde hace varios años uso [https://revealjs.com/](https://revealjs.com/) para hacer mis presentaciones y talleres, despues de aprender a usarlo (esta fácil) hice un par de talleres en eventos universitarios [https://archive.org/details/talleres-10-uam](https://archive.org/details/talleres-10-uam) y en el hackerspace donde habitaba, colaboraba. [https://ranchoelectronico.org/presentaciones-con-revealjs](https://ranchoelectronico.org/presentaciones-con-revealjs)

En la búsqueda por incorporar nuevas cosas a los talleres probé un presentador inalámbrico que en mi computadora Debian aparece asi con el comando **lsusb**:

{% highlight java %} Bus 001 Device 012: ID 3243:0131 NORWII Norwii Wireless Presenter {% endhighlight %}

Pero no funcionaba con revealjs por lo que busqué en la documentación esta parte:

[https://revealjs.com/config/](https://revealjs.com/config/)

dentro de la inicialización:

{% highlight java %} Reveal.initialize({ {% endhighlight %}

si originalmente esta asi:

{% highlight java %} navigationMode: 'default', {% endhighlight %}
 
 cambiarlo o definirlo asi: 
 
{% highlight java %} navigationMode: 'linear', {% endhighlight %}
 
 guardan el cambio y con esto funciona bien :)
