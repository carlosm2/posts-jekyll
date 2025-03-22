---
layout: post
title:  "Nahuatl para generar contraseñas en KeepassXC"
date:   2022-06-21 12:32:00
categories: softwarelibre nahuatl keepassxc
---


         .-==-.
        /{.=-.}\
       | / .  \ |
       |;   :  :|
       \(   :  )/
        `._'__.'
      |\   ||
      \ \  ||
       | | ||
       | | ||   /|
       \  \||  / /
        \ ||| | |
         | || | |
          \||/  /
           ||| /
           || |
           ||/
           ||


# Lista de palabras en Nahuatl para KeepassXC

Las listas de palabras pueden ser usadas para generar contraseñas aleatorias, el gestor de contraseñas KeepassXC tiene una lista integrada que aplica para el idioma ingles: [https://github.com/keepassxreboot/keepassxc/blob/develop/share/wordlists/eff_large.wordlist](https://github.com/keepassxreboot/keepassxc/blob/develop/share/wordlists/eff_large.wordlist) pero se pueden agregar listas de palabras en otros idiomas para que las contraseñas tengan un poco mas de sentido para personas de otras geografias no angloparlantes.

## Pasos para habilitar el idioma Nahuatl para KeepassXC en sistema GNU/Linux

Descargar Lista

{% highlight perl %}wget https://raw.githubusercontent.com/carlosm2/lista-nahuatl/main/nahuatl-lista.txt{% endhighlight %}

Descargar fuera de github

Opción 1:

{% highlight perl %}wget https://cacu.tech/nahuatl/nahuatl-lista.txt{% endhighlight %}

Opción 2: Usando torsocks para conectarse a un sitio cebolla

{% highlight perl %}torsocks wget http://www.orhecoctbqfeuftzycwrgg6rbf2tmsexnh7okufstc67r6fpnagjorid.onion/nahuatl/nahuatl-lista.txt{% endhighlight %}

## Copiar lista a wordlist de KeePassxc

esto para las versiones de KeePassXC menores a 2.7.x

{% highlight perl %}sudo cp nahuatl-lista.txt /usr/share/keepassxc/wordlists/{% endhighlight %}

## Seleccionar la lista:

Si keepassXC estaba abierto cierralo y abrelo de nuevo

## Selecciona de Lista de Palabras:

como se ve en esta imagen: [https://cacu.tech/img/kipas1.png](https://cacu.tech/img/kipas1.png)


en donde decia eff_large.wordlist al seleccionar el menú desplegable se verá en este caso nahuatl-lista.txt

## y seleccionas esa lista:

como se ve en esta imagen: [https://cacu.tech/img/kipas2.png](https://cacu.tech/img/kipas2.png)

será la unica vez que realices este cambio, la próxima vez que quieras crear una contraseña con frases estará seleccionado el idioma nahuatl.


## Pasos para hacerlo desde Windows:

Estan disponibles en:

[https://github.com/carlosm2/lista-nahuatl#pasos-para-habilitar-el-idioma-nahuatl-en-keepassxc-en-sistema-windows](https://github.com/carlosm2/lista-nahuatl#pasos-para-habilitar-el-idioma-nahuatl-en-keepassxc-en-sistema-windows)

## Video

Agregar Nahuatl al generador de contraseñas de KeepassXC

[https://fediverse.tv/w/m1GYXX3q8H7CVZYhPwVXea](https://fediverse.tv/w/m1GYXX3q8H7CVZYhPwVXea)

