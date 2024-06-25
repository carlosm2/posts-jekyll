---
layout: post
title:  "Instalar cliente Outline VPN en Debian"
date:   2024-06-01 12:32:00
categories: vpn outline debian
---

## Instalar Cliente Outline VPN en Debian

Outline es un proyecto de código abierto creado por Jigsaw que proporciona a personas y organizaciones una forma más segura de acceder al Internet abierto. 
Outline permite crear fácilmente un servidor VPN para que todo el mundo pueda acceder al Internet libre y abierto.
consta de 2 paquetes, el Administrador de Outline y el Cliente de Outline
Puedes descargar el cliente desde la pagina: [https://getoutline.org](https://getoutline.org/), tiene versiones para Android, Windows, CHrome, IOS, MacOS y Linux.
Aqui voy a mostrar los pasos para instalar en Debian 11:

{% highlight php %}

cd Descargas
wget https://s3.amazonaws.com/outline-releases/client/linux/stable/Outline-Client.AppImage

{% endhighlight %}

luego lo movemos a la carpeta /opt

{% highlight php %}
sudo mv Outline-Client.AppImage /opt
{% endhighlight %}

y hacemos ejecutable el AppImage
{% highlight php %}
chmod a+x Outline-Client.AppImage
{% endhighlight %}

y finalmento lo ejecutamos:
{% highlight php %}
./Outline-Client.AppImage
{% endhighlight %}

## Crear icono lanzador:

Creamos un archivo .desktop con este comando:

{% highlight php %}vim ~/.local/share/applications/outline.desktop{% endhighlight %} 

donde vamos a poner este texto:

{% highlight php %}
[Desktop Entry]
Type=Application
Name=OutlineVPN
Comment=OutlineVPN
Exec=/opt/Outline-Client.AppImage
Icon=/home/cacu/tools/img/outlinevpnlogo.png
Terminal=false
Categories=Utilities;
{% endhighlight %} 

y listo.

También recién publiqué un video en el Fediverso con los pasos: [https://fediverse.tv/w/eSmfP1zaS3oLxNrbonetRr](https://fediverse.tv/w/eSmfP1zaS3oLxNrbonetRr)
