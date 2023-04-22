---
layout: post
title:  "Formatear lista con sed bash"
date:   2022-05-21 12:32:00
categories: softwarelibre bash sed
---

       ___________
      |.---------.|
      ||         ||
      ||         ||
      ||         ||
      |'---------'|
       `)__ ____('
       [=== -- o ]--.
     __'---------'__ \
     `""'"""""'""""`/T\
                    \_/
                    


## Acomodar lista de palabras con sed bash

Para formatear una lista en nahuatl que necesitaba para usarlo en KeepassXC:

[https://cacu.tech/softwarelibre,/nahuatl,/keepassxc/2022/06/21/idioma-nahuatl-keepassxc.html](https://cacu.tech/softwarelibre,/nahuatl,/keepassxc/2022/06/21/idioma-nahuatl-keepassxc.html)

tuve que buscar una lista

Afortunadamente tengo amiguis que estan interesades en idiomas originarios y que le mueven a la compu, entonces le pregunté a un par de los que seguro podria obtener respuestas, ya ubicaba varios diccionarios pero queria una lista de palabras que fuera mas o menos fácil de limpiar para tener los datos de forma que se puedan usar por KeepassXC.

Para descargar la lista original puedes visitar este sitio:

[https://aulex.org/nah-es/](https://aulex.org/nah-es/) 

que te dará este archivo:

{% highlight perl %}nah-es.htm{% endhighlight %}

Luego hay que filtrarla, acomodarla, el buen petrohs me pasó este comando:

{% highlight perl %}cat nah-es.htm | grep '<p><span class=dict>' 
| sed -e "s/<p><span class=dict>//" -e "s/:.*//"{% endhighlight %}

quedó casi perfecto pero luego vi que la lista tenia unos numeros, porque hay palabras que se repiten porque pueden tener diversos significados, tambien estaban signos de interrogación y admiración, esos los quite con esto:

{% highlight perl %}cat nah-es.txt | sed 's/[12!¡¿? \-]//g' nah-es.txt > nahuatl-lista.txt{% endhighlight %}

ya con los datos pulidos procedi a subirlo a github e hice un Pull Request para subirlo a algunos sitios que usan esas listas en otros idiomas.

[https://github.com/carlosm2/lista-nahuatl](https://github.com/carlosm2/lista-nahuatl)

Agradezco a Don Petrohs [https://github.com/petrohs](https://github.com/petrohs) ayudarme a formatear la lista.

