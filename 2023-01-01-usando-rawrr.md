---
layout: post
title:  "Instalar RAWRR para acompañamiento en Seguridad Digital"
date:   2023-01-01 12:32:00
categories: softwarelibre, autocuidadodigital, conexo
---
                       .-'~~~-.
                     .'o  oOOOo`.
                    :~~~-.oOo   o`.
                     `. \ ~-.  oOOo.
                       `.; / ~.  OO:
                       .'  ;-- `.o.'
                      ,'  ; ~~--'~
                      ;  ;
_______\|/__________\\;_\\//___\|/________



## SAFETAG

**S**ecurity **A**uditing **F**ramework and **E**valuation **T**emplate for **A**dvocacy **G**roups

Existen varios frameworks o entornos de trabajo que nos ayudan a realizar un acompañamiento en #SeguridadDigital #AutocuidadoDigital, uno de ellos es **SAFETAG**, para utilizar este framework de manera sencilla existe **RAWRR** gracias a [Conexo](https://conexo.org/).

SAFETAG traducido seria: 

El Sistema de Auditorías de Seguridad y Plantilla de Evaluación para Grupos de Defensoría

tiene su sitio web con los elementos organizados:

[https://safetag.org/#allMethods](https://safetag.org/#allMethods)

y gracias a [Localization Lab](https://www.localizationlab.org/) lo tenemos en español: 

[https://github.com/SAFETAG/SAFETAG/releases/download/0.6.0/Spanish.pdf](https://github.com/SAFETAG/SAFETAG/releases/download/0.6.0/Spanish.pdf)

## RAWRR

[https://conexo.org/project/rawrr/](https://conexo.org/project/rawrr/)

Risk Assessment Workflow for Recommendation Roadmaps

Los releases o lanzamientos estan en la página de github de conexo:

[https://github.com/ConexoLA/RAWRR/releases](https://github.com/ConexoLA/RAWRR/releases)

Y la documentación de uso e instalación en esta página:

[https://rawrrdocs.netlify.app/es/2-uso/inicio/](https://rawrrdocs.netlify.app/es/2-uso/inicio/)

## Descargar e Instalar:

En mi caso voy a bajar la ultima versión con estos comandos en Linux:

Creamos un directorio (en mi caso llamado tools) y entramos al mismo:

{% highlight php %}mkdir tool && cd $_{% endhighlight %}

despues lo descargamos con esto:

{% highlight php %}wget https://github.com/ConexoLA/RAWRR/releases/download/v1.5.3/RAWRRv1.5.3-Linux-x64.zip{% endhighlight %}

lo descomprimimos en la carpeta actual:

{% highlight php %}unzip RAWRRv1.5.3-Linux-x64.zip -d .{% endhighlight %}

luego hacemos ejecutable el appimage con este comando:

{% highlight php %}chmod a+x RAWRR/RAWRR-1.5.3.AppImage{% endhighlight %}

y finalmento lo ejecutamos:

{% highlight php %}./RAWRR-1.5.3.AppImage{% endhighlight %} 

## Crear icono lanzador:

Creamos un archivo .desktop con este comando:

{% highlight php %}vim ~/.local/share/applications/rawwr.desktop{% endhighlight %} 

donde vamos a poner este texto:

{% highlight php %}
[Desktop Entry]
Type=Application
Name=RAWWR
Comment=RAWWR
Exec=/home/cacu/tools/RAWRR/RAWRR-1.5.3.AppImage
Icon=/home/cacu/tools/RAWRR/rawrr.png
Terminal=false
Categories=Utilities;
{% endhighlight %} 


En este caso use esta imagen para el logo: [https://cacu.tech/img/rawrr.png](https://cacu.tech/img/rawrr.png) asi que si quieres este mismo logo puedes descargarla y dejarla idealmente en el mismo directorio de RAWRR.

Con este procedimiento podras tener RAWRR a la mano en tu escritorio, en mi caso un gnome sobre Debian 11.




