---
layout: post
title:  "Format list with sed bash (EN)"
date:   2022-05-20 12:32:00
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
                    


## Arrange word list with sed bash

To format a list in Nahuatl I needed to use it in KeepassXC:

[https://cacu.tech/softwarelibre,/nahuatl,/keepassxc/2022/06/21/idioma-nahuatl-keepassxc.html](https://cacu.tech/softwarelibre,/nahuatl,/keepassxc/2022/06/21/idioma-nahuatl-keepassxc.html)

I had to look for a list

Fortunately, I have friends who are interested in native languages ​​and who are computer-savvy, so I asked a couple of people who I was sure would be able to provide me with answers. I had already found several dictionaries, but I wanted a word list that was relatively easy to clean so I could have the data in a form that could be used by KeepassXC.

To download the original list you can visit this site:

[https://aulex.org/nah-es/](https://aulex.org/nah-es/) 

which will give you this file:

{% highlight perl %}nah-es.htm{% endhighlight %}

Luego hay que filtrarla, acomodarla, el buen petrohs me pasó este comando:

{% highlight perl %}cat nah-es.htm | grep '<p><span class=dict>' 
| sed -e "s/<p><span class=dict>//" -e "s/:.*//"{% endhighlight %}

quedó casi perfecto pero luego vi que la lista tenia unos numeros, porque hay palabras que se repiten porque pueden tener diversos significados, tambien estaban signos de interrogación y admiración, esos los quite con esto:

{% highlight perl %}cat nah-es.txt | sed 's/[12!¡¿? \-]//g' nah-es.txt > nahuatl-lista.txt{% endhighlight %}

ya con los datos pulidos procedi a subirlo a github e hice un Pull Request para subirlo a algunos sitios que usan esas listas en otros idiomas.

[https://github.com/carlosm2/lista-nahuatl](https://github.com/carlosm2/lista-nahuatl)

Agradezco a Don Petrohs [https://github.com/petrohs](https://github.com/petrohs) ayudarme a formatear la lista.

