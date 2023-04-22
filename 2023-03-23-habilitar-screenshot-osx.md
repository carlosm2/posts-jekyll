---
layout: post
title:  "habilitar captura de pantalla de keepassXC en macOS"
date:   2023-03-24 12:32:00
categories: softwarelibre keeepassxc osx macos
---

    .__________________________.
    | .___________________. |==|
    | |   [ Apol ]        | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | | ,|
    | !___________________! |(c|
    !_______________________!__!
    |    ___ -=      ___ -= | ,|
    | ---[_]---   ---[_]--- |(c|
    ---------------------------- 

# Habilitar captura de pantalla de KeepassXC en OSX

## Capturas de pantalla

Para hacer tutoriales, documentación, que es una de las cosas que frecuentemente hago necesito hacer capturas de pantalla, en mi sistema base (Debian Bullseye) utilizo el software integrado en gnome screenshot: [https://gitlab.gnome.org/GNOME/gnome-screenshot](https://gitlab.gnome.org/GNOME/gnome-screenshot) y para animaciones mp4 y gif uso Peek: [https://github.com/phw/peek](https://github.com/phw/peek).

En el caso de macOS se utiliza:

{% highlight java %}Shift +  Command + 5{% endhighlight %}

## Bloqueo de capturas de pantalla

Hay un bloqueo de privacidad que he notado al hacer capturas de pantalla en Android y macOS en aplicaciones enfocadas en la seguridad, privacidad como KeepassXC [https://keepassxc.org/](https://keepassxc.org/) y FreeOTP [https://freeotp.github.io/](https://freeotp.github.io/) que no te permiten guardar la captura de pantalla con los datos, tambien pasa cuando se esta usando un software de visualización remota [https://es.wikipedia.org/wiki/VNC](https://es.wikipedia.org/wiki/VNC). 

## Habilitar en macOS

Esta es la instrucción para habilitar una aplicacion:

{% highlight java %}open -n ./AppName.app --args -AppCommandLineArg{% endhighlight %}

entonces aplica para KeepassXC, abrir la terminal:

cambiarse al directorio donde esta la aplicación, en este caso: 

{% highlight java %}cd /Applications{% endhighlight %}

Y luego ejecutar:

{% highlight java %}open -n ./KeePassXC.app --args allow-screencapture{% endhighlight %}

esto abrira keepassXC con la posibilidad de hacer capturas de pantalla.



