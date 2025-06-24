---
layout: post
title:  "Enable screenshot for KeepassXC on macOS"
date:   2023-03-22 12:32:00
categories: softwarelibre keeepassxc osx macos
---

    .__________________________.
    | .___________________. |==|
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | | ,|
    | !___________________! |(c|
    !______________________ |__!
    |    ___ -=      ___ -= | ,|
    | ---[_]---   ---[_]--- |(c|
    ---------------------------- 

# Enable screenshots for KeepassXC on OSX

## Screenshots

To make tutorials, documentation, which is one of the things I often do I need to take screenshots, on my base system (Debian Bullseye) I use the software built into gnome screenshot: [https://gitlab.gnome.org/GNOME/gnome-screenshot](https://gitlab.gnome.org/GNOME/gnome-screenshot) and for mp4 and gif animations I use Peek: [https://github.com/phw/peek](https://github.com/phw/peek).

In the case of macOS it is used:

{% highlight java %}Shift +  Command + 5{% endhighlight %}

## Screenshot Lock

Hay un bloqueo de privacidad que he notado al hacer capturas de pantalla en Android y macOS en aplicaciones enfocadas en la seguridad, privacidad como KeepassXC [https://keepassxc.org/](https://keepassxc.org/) y FreeOTP [https://freeotp.github.io/](https://freeotp.github.io/) que no te permiten guardar la captura de pantalla con los datos, tambien pasa cuando se esta usando un software de visualización remota [https://es.wikipedia.org/wiki/VNC](https://es.wikipedia.org/wiki/VNC). 

## Habilitar en macOS

Esta es la instrucción para habilitar una aplicacion:

{% highlight java %}$ open -n ./AppName.app --args -AppCommandLineArg{% endhighlight %}

entonces aplica para KeepassXC, abrir la terminal:

cambiarse al directorio donde esta la aplicación, en este caso: 

{% highlight java %}$ cd /Applications{% endhighlight %}

Y luego ejecutar:

{% highlight java %}$ open -n ./KeePassXC.app --args allow-screencapture{% endhighlight %}

esto abrira keepassXC con la posibilidad de hacer capturas de pantalla.



